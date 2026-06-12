---
title: "cannot upgrade ubuntu server"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by kasak87 on 2012-10-24
hello everybody. 
my servers notified me about new release quantal, but i cannot upgrade because i have ru_RU locale, and i see this error:

```
&#1045;&#1089;&#1083;&#1080; &#1074;&#1099; &#1087;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1080;&#1090;&#1077;, &#1076;&#1086;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1077;&#1083;&#1100;&#1085;&#1072;&#1103; &#1089;&#1083;&#1091;&#1078;&#1073;&#1072; ssh &#1073;&#1091;&#1076;&#1077;&#1090; &#1079;&#1072;&#1087;&#1091;&#1097;&#1077;&#1085;&#1072; &#1085;&#1072; &#1087;&#1086;&#1088;&#1090;&#1091;
«1022».
&#1061;&#1086;&#1090;&#1080;&#1090;&#1077; &#1083;&#1080; &#1074;&#1099; &#1087;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1080;&#1090;&#1100;?

&#1055;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1080;&#1090;&#1100; [&#1076;&#1053;] &#1076;


&#1055;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1072; &#1082;&#1088;&#1080;&#1090;&#1080;&#1095;&#1077;&#1089;&#1082;&#1072;&#1103; &#1086;&#1096;&#1080;&#1073;&#1082;&#1072;

&#1055;&#1086;&#1078;&#1072;&#1083;&#1091;&#1081;&#1089;&#1090;&#1072;, &#1089;&#1086;&#1086;&#1073;&#1097;&#1080;&#1090;&#1077; &#1086;&#1073; &#1101;&#1090;&#1086;&#1081; &#1086;&#1096;&#1080;&#1073;&#1082;&#1077; &#1080; &#1074;&#1082;&#1083;&#1102;&#1095;&#1080;&#1090;&#1077; &#1092;&#1072;&#1081;&#1083;&#1099;
/var/log/dist-upgrade/main.log &#1080; /var/log/dist-upgrade/apt.log &#1074; &#1074;&#1072;&#1096;
&#1086;&#1090;&#1095;&#1105;&#1090;. &#1054;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1077; &#1073;&#1099;&#1083;&#1086; &#1086;&#1090;&#1084;&#1077;&#1085;&#1077;&#1085;&#1086;.
&#1042;&#1072;&#1096; &#1086;&#1088;&#1080;&#1075;&#1080;&#1085;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; &#1092;&#1072;&#1081;&#1083; sources.list &#1073;&#1099;&#1083; &#1089;&#1086;&#1093;&#1088;&#1072;&#1085;&#1105;&#1085; &#1074;
/etc/apt/sources.list.distUpgrade.

Traceback (most recent call last):

File "/tmp/update-manager-rAHyDt/quantal", line 10, in <module>
sys.exit(main())

File "/tmp/update-manager-rAHyDt/DistUpgrade/DistUpgradeMain.py",
line 240, in main
if app.run():

File
"/tmp/update-manager-rAHyDt/DistUpgrade/DistUpgradeController.py",
line 1764, in run
return self.fullUpgrade()

File
"/tmp/update-manager-rAHyDt/DistUpgrade/DistUpgradeController.py",
line 1616, in fullUpgrade
if not self.prepare():

File
"/tmp/update-manager-rAHyDt/DistUpgrade/DistUpgradeController.py",
line 429, in prepare
self._sshMagic()

File
"/tmp/update-manager-rAHyDt/DistUpgrade/DistUpgradeController.py",
line 299, in _sshMagic
"Do you want to continue?") % port)

File "/tmp/update-manager-rAHyDt/DistUpgrade/DistUpgradeViewText.py",
line 210, in askYesNoQuestion
if res.strip().lower().startswith(_("y")):

UnicodeDecodeError: 'ascii' codec can't decode byte 0xd0 in position
0: ordinal not in range(128)
=== Command detached from window (Wed Oct 24 11:34:55 2012) ===
=== Command terminated with exit status 1 (Wed Oct 24 11:34:55 2012) ===

```i saw the bug related to this problem on bugs.launchpad.net [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1031882](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1031882)

problem might be fixed for desktop, but i have ubuntu servers, that don't have update-manager, and i don't want to install it because of many depencies. 

is there any way to install new release with "do-release-upgrade" ?

---

### Post by Bucky Ball on 2012-10-24
For servers, or any production machines, you are better to stick with the LTS release. That's why they're there. If it's not broke, don't fix ... 

If you rely on these machines and all is well I'd stick with what you have. If you don't rely on them and have time to fix any issues that arise, go for it and report to the devs.

12.04 LTS is supported for five years, until April 2017. 12.10 is supported for the next eighteen months.

---

### Post by kasak87 on 2012-10-24
this is not production servers, I still want to know how can I upgrade them

---

### Post by dino99 on 2012-10-24
are you upgrading from "main server" or from "local server/mirror" ?

you'd better to use a local ru_RU server/mirror to upgrade instead of the "main" one using unicode en_US

your error is :  [COLOR="RoyalBlue"]UnicodeDecodeError: 'ascii' codec can't decode byte 0xd0[/COLOR] , so use a RU server (ansi 1250) for upgrading

---

### Post by grahammechanical on 2012-10-24
You might want to read this:

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuServer]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuServer")

See the heading Upgrade.

Regards.

---

### Post by kasak87 on 2012-10-25
thanks for link, but still no luck, I already have update-manager-core, and I still have error

---

