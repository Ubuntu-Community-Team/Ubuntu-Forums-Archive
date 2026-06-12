---
title: "installation freezes"
date: 2004-10-22
forum: Installation &amp; Upgrades
---

### Post by u_d on 2004-10-22
Hi I am trying to get Ubuntu on my Dell Latitude C600 laptop but it keeps freezing to a blue screen. It seems to be during the install just after you select the country info where it is detecting hardware to find cd-rom that the screen seems to freeze. This might help for someone trying to help me with this problem.

In one console I get:
(none) user.notice cdrom-detect: Searching for ubuntu installation media
(It seems to stop just after that message.)

In another console:
insmod /lib/modules/2.6.8.1-2-386/kernel/fs/isofs/isofs.ko
(It freezes after that message to)

Also the cd-rom starts and then stop and repeats doing this with messages from syslog:
syslog.info klogd: ide-cd: cmd 0x28 timed out
syslog.info klogd: hdc: DMA interrupt recovery
syslog.info klogd: hdc: lost interrupt

 I have also installed slackware on it quickly to see if its not the cd-rom at fault and I had no problems.

Anyhelp would be appreciated. Thanks

---

### Post by maudalo on 2005-02-15
I experienced similar problems on a Dell Latitude D266XT, eventually I found a workaround.
Just accept the normal linux boot, when the installer asks about the language press Alt-F2
to get into a shell, then modprobe manually 'ide_cd', 'ide_generic' and 'isofs'. Now you
can go back to the installer with Alt-F1 and continue the installation. (Notice, if you try to
mount the cdrom yourself, it seems like the installation script gets confused).

---

### Post by CyrilleMortreux on 2005-02-15
[QUOTE=u_d]Hi I am trying to get Ubuntu on my Dell Latitude C600 laptop but it keeps freezing to a blue screen. It seems to be during the install just after you select the country info where it is detecting hardware to find cd-rom that the screen seems to freeze. This might help for someone trying to help me with this problem.

In one console I get:
(none) user.notice cdrom-detect: Searching for ubuntu installation media
(It seems to stop just after that message.)

In another console:
insmod /lib/modules/2.6.8.1-2-386/kernel/fs/isofs/isofs.ko
(It freezes after that message to)

Also the cd-rom starts and then stop and repeats doing this with messages from syslog:
syslog.info klogd: ide-cd: cmd 0x28 timed out
syslog.info klogd: hdc: DMA interrupt recovery
syslog.info klogd: hdc: lost interrupt

 I have also installed slackware on it quickly to see if its not the cd-rom at fault and I had no problems.

Anyhelp would be appreciated. Thanks[/QUOTE]

try that when the CD boots :

boot: linux noacpi pci=noapic

It should work.

---

### Post by rvfh on 2006-11-25
What worked for me (alternate CD):
- proceed with install until the keyboard selection dialog
- select your keyboard if not American English but DO NOT proceed to next step (hardware detection)
- disable DMA support: Alt-F2, Enter, hdparm -d0 /dev/hdc
- proceed with install: Alt-F1, Enter

The install might be slower because DMA is off, but any attempt to re-enable it freezes the install.

Note: you might want to add the line 'hdparm -d0 /dev/hdc' to your /etc/rc.local once the system is installed.

---

### Post by Pvt.Addams on 2008-01-21
I know this thread is pretty old, but I just want to thank rvfh for his answer :)

I just wanted to install xubuntu 7.10 on a very old notebook (64mb ram, amd k6) and this was just the solution - thank you VERY much :KS

---

