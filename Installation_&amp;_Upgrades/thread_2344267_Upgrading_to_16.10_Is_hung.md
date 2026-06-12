---
title: "Upgrading to 16.10 Is hung"
date: 2016-11-23
forum: Installation &amp; Upgrades
---

### Post by optiores on 2016-11-23
EDIT after being moved from another thread: Greetings. After upgrading Ubuntu from 16.04 to 16.10, after downloading the packets the installing phase began the window opened the terminal, displayed this
```
[FONT=Verdana]Rozpakowywanie szablonów pakietów dla pakietów: 100%[/FONT]
[FONT=Verdana]Prekonfiguracja pakietów...[/FONT]
[FONT=Verdana]Rozpakowywanie szablonów pakietów dla pakietów: 100%[/FONT]
[FONT=Verdana]Prekonfiguracja pakietów...[/FONT]
[FONT=Verdana]Rozpakowywanie szablonów pakietów dla pakietów: 100%[/FONT]
[FONT=Verdana]Prekonfiguracja pakietów...[/FONT]
[FONT=Verdana]Rozpakowywanie szablonów pakietów dla pakietów: 100%[/FONT]
[FONT=Verdana]Prekonfiguracja pakietów...[/FONT]
```
and hanged. Please help me, I don't know what to do now.

---

### Post by wildmanne39 on 2016-11-23
Moved to own thread!

---

### Post by jml3473 on 2016-11-23
Haha, I guess this was first posted in the thread I opened a few hours ago.
Did you also check whether your /var/log/dist-upgrade/main.log has the same error messages?
Well, I'm about to try out some combinations of dpkg --configure -a / apt-get update / apt-get dist-upgrade, so if there's no news from me something went bad and I lost my internet connection ;)

---

### Post by optiores on 2016-11-23
Yes, but as you can see above the moderator moved it to a new thread. I wonder if this hang has anything to do with the Python update that I installed before the distro update. Here's the end of the log file you mentioned:
```
2016-11-23 19:21:25,019 ERROR not handled exception:Traceback (most recent call last):


  File "/tmp/ubuntu-release-upgrader-_qub02e8/yakkety", line 8, in <module>
    sys.exit(main())


  File "/tmp/ubuntu-release-upgrader-_qub02e8/DistUpgrade/DistUpgradeMain.py", line 242, in main
    if app.run():


  File "/tmp/ubuntu-release-upgrader-_qub02e8/DistUpgrade/DistUpgradeController.py", line 1880, in run
    return self.fullUpgrade()


  File "/tmp/ubuntu-release-upgrader-_qub02e8/DistUpgrade/DistUpgradeController.py", line 1845, in fullUpgrade
    if not self.doDistUpgrade():


  File "/tmp/ubuntu-release-upgrader-_qub02e8/DistUpgrade/DistUpgradeController.py", line 1183, in doDistUpgrade
    res = self.cache.commit(fprogress,iprogress)


  File "/tmp/ubuntu-release-upgrader-_qub02e8/DistUpgrade/DistUpgradeCache.py", line 267, in commit
    apt.Cache.commit(self, fprogress, iprogress)


  File "/usr/lib/python3/dist-packages/apt/cache.py", line 515, in commit
    res = self.install_archives(pm, install_progress)


  File "/usr/lib/python3/dist-packages/apt/cache.py", line 479, in install_archives
    res = install_progress.run(pm)


  File "/tmp/ubuntu-release-upgrader-_qub02e8/DistUpgrade/DistUpgradeView.py", line 234, in run
    res = os.WEXITSTATUS(self.wait_child())


  File "/tmp/ubuntu-release-upgrader-_qub02e8/DistUpgrade/DistUpgradeViewGtk3.py", line 339, in wait_child
    self.update_interface()


  File "/tmp/ubuntu-release-upgrader-_qub02e8/DistUpgrade/DistUpgradeViewGtk3.py", line 346, in update_interface
    InstallProgress.update_interface(self)


  File "/usr/lib/python3/dist-packages/apt/progress/base.py", line 255, in update_interface
    if float(percent) != self.percent or status_str != self.status:


ValueError: could not convert string to float: '0,0000'


2016-11-23 19:21:25,020 DEBUG running apport_crash()
```

UPDATE: Tired of waiting, I've restarted the computer and obviously Ubuntu doesn't boot now. Tried to repair the packages from recovery mode but it doesn't help. Thankfully I have a dual-boot with Windows 7.

---

### Post by jml3473 on 2016-11-23
Looks like it's the same bug. I haven't touched python in a long while. I was suspecting something wrong with the locale, decimal separator is a comma in my country. Anyway the upgrade can be resumed manually. You can check out "my" thread but I'm no expert. Good luck :D

---

