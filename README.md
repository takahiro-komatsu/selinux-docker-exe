「Drupal 9 おいしいレシピ集 / Drupal Meetup 豊田支部」
第1章 アプリ開発のCI/CD環境構築

に関する補足ページです。

# 使い方
コンテナランタイムにPodmanを利用して、GitLab RunnerでDocker Executorを起動したい場合、SELinux環境下ではセキュリティコンテキストの修正が必要です。

ポリシーモジュールを適用するには、以下のコマンドを実行します。
```
$ cd ~
$ git clone https://github.com/takahiro-komatsu/selinux-docker-exe
$ cd selinux-docker-exe
$ sudo semodule -i gitlab-runner-b.pp
```

ポリシーモジュールが追加されたかどうかは
```
$ sudo semodule -l | grep gitlab-runner-b
```
で確認できます。

また、ポリシーモジュールが不要になった場合は
```
$ sudo semodule -r gitlab-runner-b
```
で削除が可能です。
