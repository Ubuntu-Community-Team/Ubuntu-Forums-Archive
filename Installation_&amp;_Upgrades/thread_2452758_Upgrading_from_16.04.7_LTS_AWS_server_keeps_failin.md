---
title: "Upgrading from 16.04.7 LTS AWS server keeps failing"
date: 2020-10-27
forum: Installation &amp; Upgrades
---

### Post by mikejones3 on 2020-10-27
I have an AWS EC2 server that I keep trying to upgrade and I keep failing.

Here are the steps I try:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo do-release-upgrade
```

Once I do the last command I go through the prompts and then I get this error...

```
Broken landscape-common:amd64 Depends on python3-twisted [ amd64 ] < none -> 17.9.0-2ubuntu0.1 > ( python )  Considering python3-twisted:amd64 1 as a solution to landscape-common:amd64 9999
    Reinst Failed because of python3-zope.interface:amd64
  MarkKeep python3-twisted [ amd64 ] < none -> 17.9.0-2ubuntu0.1 > ( python ) FU=0
  Considering python3-twisted:amd64 1 as a solution to landscape-common:amd64 9999
Done


Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-a7x268x1/bionic", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeMain.py", line 238, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeController.py", line 2072, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeController.py", line 1981, in fullUpgrade
    if not self.askDistUpgrade():
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeController.py", line 1153, in askDistUpgrade
    changes = self.calcDistUpgrade()
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeController.py", line 1120, in calcDistUpgrade
    if not self.cache.installTasks(self.tasks):
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeCache.py", line 856, in installTasks
    pkg.mark_install()
  File "/usr/lib/python3/dist-packages/apt/package.py", line 1356, in mark_install
    fixer.resolve(True)
SystemError: E:Unable to correct problems, you have held broken packages.
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/problem_report.py", line 497, in add_to_existing
    self.write(f)
  File "/usr/lib/python3/dist-packages/problem_report.py", line 450, in write
    block = f.read(1048576)
  File "/usr/lib/python3.5/codecs.py", line 321, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte


Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-a7x268x1/bionic", line 8, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeMain.py", line 238, in main
    if app.run():
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeController.py", line 2072, in run
    return self.fullUpgrade()
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeController.py", line 1981, in fullUpgrade
    if not self.askDistUpgrade():
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeController.py", line 1153, in askDistUpgrade
    changes = self.calcDistUpgrade()
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeController.py", line 1120, in calcDistUpgrade
    if not self.cache.installTasks(self.tasks):
  File "/tmp/ubuntu-release-upgrader-a7x268x1/DistUpgrade/DistUpgradeCache.py", line 856, in installTasks
    pkg.mark_install()
  File "/usr/lib/python3/dist-packages/apt/package.py", line 1356, in mark_install
    fixer.resolve(True)
SystemError: E:Unable to correct problems, you have held broken packages.
=== Command detached from window (Wed Oct 28 00:45:53 2020) ===
=== Command terminated with exit status 1 (Wed Oct 28 00:46:03 2020) ===
```

---

### Post by ActionParsnip on 2020-10-28
What is the output of
```

apt-cache policy landscape-common:amd64

```
Thanks

---

### Post by mikejones3 on 2020-10-28
```

ubuntu@ip:~$ apt-cache policy landscape-common:amd64
landscape-common:
  Installed: (none)
  Candidate: 16.03-0ubuntu2.16.04.8
  Version table:
     16.03-0ubuntu2.16.04.8 500
        500 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     16.03-0ubuntu2 500
        500 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

---

### Post by mikejones3 on 2020-10-29
Anyone got any ideas for me to try here?

---

### Post by QIII on 2020-10-29
Do you have any PPAs in use?

---

### Post by mikejones3 on 2020-10-29
Nope, I dont think so.

---

### Post by QIII on 2020-10-29
Pinned packages?  Third party python packages?

---

### Post by mikejones3 on 2020-10-29
Nope pretty sure I have a pretty vanila set up. Other than customizing my nginx configs. 

Is there any commands I can run to double check? If not worse case I do a back up and try and if it fails I can restore back up.

---

### Post by mikejones3 on 2020-11-05
Still running into issues:

I tried a [COLOR=#000000][FONT=Consolas]sudo ```
apt-get -f install[/FONT][/COLOR]
```

Any here were my results:

```
ubuntu@ip:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  javascript-common jsonlint libargon2-0 libjs-excanvas libvpx3 libzip5 linux-aws-headers-4.4.0-1054
  linux-aws-headers-4.4.0-1055 linux-aws-headers-4.4.0-1057 linux-aws-headers-4.4.0-1060 linux-aws-headers-4.4.0-1061
  linux-aws-headers-4.4.0-1062 linux-aws-headers-4.4.0-1065 linux-aws-headers-4.4.0-1066 linux-aws-headers-4.4.0-1069
  linux-aws-headers-4.4.0-1070 linux-aws-headers-4.4.0-1072 linux-aws-headers-4.4.0-1074 linux-aws-headers-4.4.0-1075
  linux-aws-headers-4.4.0-1077 linux-aws-headers-4.4.0-1079 linux-aws-headers-4.4.0-1083 linux-aws-headers-4.4.0-1084
  linux-aws-headers-4.4.0-1085 linux-aws-headers-4.4.0-1087 linux-aws-headers-4.4.0-1088 linux-aws-headers-4.4.0-1090
  linux-aws-headers-4.4.0-1092 linux-aws-headers-4.4.0-1094 mercurial mercurial-common php-cli-prompt php-composer-semver
  php-composer-spdx-licenses php-json-schema php-symfony-console php-symfony-filesystem php-symfony-finder
  php-symfony-process
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.

```


I Also ran a ```
apt-mark showhold
``` and it returned nothing.

Anyone have any other ideas, I am really stuck on trying to upgrade my server here.

---

### Post by rsteinmetz70112 on 2020-11-06
Did you run ```
sudo apt autoremove
```as suggested?

I suspect the problem is here ```
0 upgraded, 0 newly installed, 0 to remove and **38 not upgraded.**
```

---

### Post by CelticWarrior on 2020-11-06
Indeed, the "38 not upgraded" is the problem.
Release upgrades really need a fully updated system to start with.

---

### Post by mikejones3 on 2020-11-06
So I tried the ```
sudo apt autoremove
``` and it didn't help. Here are my steps and outputs I did everything in:

I logged in with ssh and I ran:

```
sudo apt-get -f install

```

After I ran that I got this output:

```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  javascript-common jsonlint libargon2-0 libjs-excanvas libvpx3 libzip5
  linux-aws-headers-4.4.0-1054 linux-aws-headers-4.4.0-1055
  linux-aws-headers-4.4.0-1057 linux-aws-headers-4.4.0-1060
  linux-aws-headers-4.4.0-1061 linux-aws-headers-4.4.0-1062
  linux-aws-headers-4.4.0-1065 linux-aws-headers-4.4.0-1066
  linux-aws-headers-4.4.0-1069 linux-aws-headers-4.4.0-1070
  linux-aws-headers-4.4.0-1072 linux-aws-headers-4.4.0-1074
  linux-aws-headers-4.4.0-1075 linux-aws-headers-4.4.0-1077
  linux-aws-headers-4.4.0-1079 linux-aws-headers-4.4.0-1083
  linux-aws-headers-4.4.0-1084 linux-aws-headers-4.4.0-1085
  linux-aws-headers-4.4.0-1087 linux-aws-headers-4.4.0-1088
  linux-aws-headers-4.4.0-1090 linux-aws-headers-4.4.0-1092
  linux-aws-headers-4.4.0-1094 mercurial mercurial-common php-cli-prompt
  php-composer-semver php-composer-spdx-licenses php-json-schema
  php-symfony-console php-symfony-filesystem php-symfony-finder
  php-symfony-process
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 42 not upgraded.
```

Next I ran:

```
sudo apt autoremove

```

When I ran the above I got this output:

```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
The following packages will be REMOVED:
  javascript-common jsonlint libargon2-0 libjs-excanvas libvpx3 libzip5
  linux-aws-headers-4.4.0-1054 linux-aws-headers-4.4.0-1055
  linux-aws-headers-4.4.0-1057 linux-aws-headers-4.4.0-1060
  linux-aws-headers-4.4.0-1061 linux-aws-headers-4.4.0-1062
  linux-aws-headers-4.4.0-1065 linux-aws-headers-4.4.0-1066
  linux-aws-headers-4.4.0-1069 linux-aws-headers-4.4.0-1070
  linux-aws-headers-4.4.0-1072 linux-aws-headers-4.4.0-1074
  linux-aws-headers-4.4.0-1075 linux-aws-headers-4.4.0-1077
  linux-aws-headers-4.4.0-1079 linux-aws-headers-4.4.0-1083
  linux-aws-headers-4.4.0-1084 linux-aws-headers-4.4.0-1085
  linux-aws-headers-4.4.0-1087 linux-aws-headers-4.4.0-1088
  linux-aws-headers-4.4.0-1090 linux-aws-headers-4.4.0-1092
  linux-aws-headers-4.4.0-1094 mercurial mercurial-common php-cli-prompt
  php-composer-semver php-composer-spdx-licenses php-json-schema
  php-symfony-console php-symfony-filesystem php-symfony-finder
  php-symfony-process
0 upgraded, 0 newly installed, 39 to remove and 42 not upgraded.
After this operation, 1,674 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 521502 files and directories currently installed.)
Removing javascript-common (11) ...
Removing jsonlint (1.4.0-1build1) ...
Removing libargon2-0 (0~20190702-0.1+ubuntu16.04.1+deb.sury.org+1) ...
Removing mercurial (3.7.3-1ubuntu1.2) ...
Removing mercurial-common (3.7.3-1ubuntu1.2) ...
Removing libjs-excanvas (0.r3-4) ...
Removing libvpx3:amd64 (1.5.0-2ubuntu1.1) ...
Removing libzip5:amd64 (1.3.2-1+ubuntu16.04.1+deb.sury.org+1) ...
Removing linux-aws-headers-4.4.0-1054 (4.4.0-1054.63) ...
Removing linux-aws-headers-4.4.0-1055 (4.4.0-1055.64) ...
Removing linux-aws-headers-4.4.0-1057 (4.4.0-1057.66) ...
Removing linux-aws-headers-4.4.0-1060 (4.4.0-1060.69) ...
Removing linux-aws-headers-4.4.0-1061 (4.4.0-1061.70) ...
Removing linux-aws-headers-4.4.0-1062 (4.4.0-1062.71) ...
Removing linux-aws-headers-4.4.0-1065 (4.4.0-1065.75) ...
Removing linux-aws-headers-4.4.0-1066 (4.4.0-1066.76) ...
Removing linux-aws-headers-4.4.0-1069 (4.4.0-1069.79) ...
Removing linux-aws-headers-4.4.0-1070 (4.4.0-1070.80) ...
Removing linux-aws-headers-4.4.0-1072 (4.4.0-1072.82) ...
Removing linux-aws-headers-4.4.0-1074 (4.4.0-1074.84) ...
Removing linux-aws-headers-4.4.0-1075 (4.4.0-1075.85) ...
Removing linux-aws-headers-4.4.0-1077 (4.4.0-1077.87) ...
Removing linux-aws-headers-4.4.0-1079 (4.4.0-1079.89) ...
Removing linux-aws-headers-4.4.0-1083 (4.4.0-1083.93) ...
Removing linux-aws-headers-4.4.0-1084 (4.4.0-1084.94) ...
Removing linux-aws-headers-4.4.0-1085 (4.4.0-1085.96) ...
Removing linux-aws-headers-4.4.0-1087 (4.4.0-1087.98) ...
Removing linux-aws-headers-4.4.0-1088 (4.4.0-1088.99) ...
Removing linux-aws-headers-4.4.0-1090 (4.4.0-1090.101) ...
Removing linux-aws-headers-4.4.0-1092 (4.4.0-1092.103) ...
Removing linux-aws-headers-4.4.0-1094 (4.4.0-1094.105) ...
Removing php-cli-prompt (1.0.1+dfsg-1build1) ...
Removing php-composer-semver (1.2.0-1build1) ...
Removing php-composer-spdx-licenses (1.1.2-1build1) ...
Removing php-json-schema (1.6.1-1build1) ...
Removing php-symfony-console (2.7.10-0ubuntu2) ...
Removing php-symfony-filesystem (2.7.10-0ubuntu2) ...
Removing php-symfony-finder (2.7.10-0ubuntu2) ...
Removing php-symfony-process (2.7.10-0ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu11.2) ...
```

Next I ran:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

and the output after the second one where it failed was:

```

Reading package lists... DoneBuilding dependency treeReading state information... DoneCalculating upgrade... Done0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.ubuntu@ip-172-31-72-89:~$ sudo do-release-upgradeChecking for a new Ubuntu releaseGet:1 Upgrade tool signature [819 B]Get:2 Upgrade tool [1,242 kB]Fetched 1,243 kB in 0s (0 B/s)authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg'extracting 'bionic.tar.gz'Investigating (4) landscape-common [ amd64 ] < none -> 18.01-0ubuntu3.5 > ( admin )Broken landscape-common:amd64 Depends on python3-twisted [ amd64 ] < none -> 17.9.0-2ubuntu0.1 > ( python )  Considering python3-twisted:amd64 1 as a solution to landscape-common:amd64 9999    Reinst Failed because of python3-zope.interface:amd64  MarkKeep python3-twisted [ amd64 ] < none -> 17.9.0-2ubuntu0.1 > ( python ) FU=0  Considering python3-twisted:amd64 1 as a solution to landscape-common:amd64 9999DoneTraceback (most recent call last):  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/bionic", line 8, in <module>    sys.exit(main())  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeMain.py", line 238, in main    if app.run():  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeController.py", line 2072, in run    return self.fullUpgrade()  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeController.py", line 1981, in fullUpgrade    if not self.askDistUpgrade():  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeController.py", line 1153, in askDistUpgrade    changes = self.calcDistUpgrade()  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeController.py", line 1120, in calcDistUpgrade    if not self.cache.installTasks(self.tasks):  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeCache.py", line 856, in installTasks    pkg.mark_install()  File "/usr/lib/python3/dist-packages/apt/package.py", line 1356, in mark_install    fixer.resolve(True)SystemError: E:Unable to correct problems, you have held broken packages.Error in sys.excepthook:Traceback (most recent call last):  File "/usr/lib/python3/dist-packages/problem_report.py", line 497, in add_to_existing    self.write(f)  File "/usr/lib/python3/dist-packages/problem_report.py", line 450, in write    block = f.read(1048576)  File "/usr/lib/python3.5/codecs.py", line 321, in decode    (result, consumed) = self._buffer_decode(data, self.errors, final)UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byteOriginal exception was:Traceback (most recent call last):  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/bionic", line 8, in <module>    sys.exit(main())  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeMain.py", line 238, in main    if app.run():  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeController.py", line 2072, in run    return self.fullUpgrade()  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeController.py", line 1981, in fullUpgrade    if not self.askDistUpgrade():  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeController.py", line 1153, in askDistUpgrade    changes = self.calcDistUpgrade()  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeController.py", line 1120, in calcDistUpgrade    if not self.cache.installTasks(self.tasks):  File "/tmp/ubuntu-release-upgrader-e4ydbqh7/DistUpgrade/DistUpgradeCache.py", line 856, in installTasks    pkg.mark_install()  File "/usr/lib/python3/dist-packages/apt/package.py", line 1356, in mark_install    fixer.resolve(True)SystemError: E:Unable to correct problems, you have held broken packages.=== Command detached from window (Sat Nov  7 03:36:58 2020) ===

```

---

### Post by rsteinmetz70112 on 2020-11-07
I'm having trouble reading your last output due to lack of line wrap but it appears this is the relevant part"
```
Reinst Failed because of python3-zope.interface:amd64  **MarkKeep** python3-twisted [ amd64 ]
```
I'm not sure exactly what that means but it looks like one or both of those packages are Marked to Keep and therefore not being upgraded.

---

### Post by mikejones3 on 2020-11-16
SO I have been doing some more research, and stumbled on this article: [https://community.letsencrypt.org/t/unmet-dependencies-debian-buster/133946/6](https://community.letsencrypt.org/t/unmet-dependencies-debian-buster/133946/6)

Could this be a letsEncrypt/certbot issue?

---

### Post by mikejones3 on 2020-11-21
So after looking into this I do have this PPA:

[COLOR=#F08D49][FONT=inherit]sudo[/FONT][/COLOR] [COLOR=#F08D49][FONT=inherit]apt-get[/FONT][/COLOR] update
[COLOR=#F08D49][FONT=inherit]sudo[/FONT][/COLOR] [COLOR=#F08D49][FONT=inherit]apt-get[/FONT][/COLOR] [COLOR=#F08D49][FONT=inherit]install[/FONT][/COLOR] software-properties-common
[COLOR=#F08D49][FONT=inherit]sudo[/FONT][/COLOR] add-apt-repository ppa:certbot/certbot
[COLOR=#F08D49][FONT=inherit]sudo[/FONT][/COLOR] [COLOR=#F08D49][FONT=inherit]apt-get[/FONT][/COLOR] update
[COLOR=#F08D49][FONT=inherit]sudo[/FONT][/COLOR] [COLOR=#F08D49][FONT=inherit]apt-get[/FONT][/COLOR] [COLOR=#F08D49][FONT=inherit]install[/FONT][/COLOR] python-certbot-nginx

---

