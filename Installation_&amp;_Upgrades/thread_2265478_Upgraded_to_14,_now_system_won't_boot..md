---
title: "Upgraded to 14, now system won't boot."
date: 2015-02-15
forum: Installation &amp; Upgrades
---

### Post by mn_voyageur on 2015-02-15
This morning, I tried to upgrade from 12 to 14.  Once the system rebooted, the screen shows the Ubunut dots, then displays the error messoage:
[INDENT]Filesystem check or mount failed
A maintenance shell will now be started.
Control-D will terminate this shell and continue booting after retrying
filesystems. Any further errors will be ignored
root@********:~# [/INDENT]

It will not reboot.  If I force the reboot, it returns to this screen.

Any help would be apprecaited.

MarkN

---

### Post by monkeybrain20122 on 2015-02-15
My answer is always the same. Backup your data and do a fresh install, which would take about 20 minutes as oppose to hours. This is what you should have done in the first place instead of 'upgrade'. It is not worth the troubles trying to fix a blotched 'upgrade' as you are not really sure what went wrong, even if you manage to get it working now there may be some hidden issues which will manifest as hard to diagnose problems later on. 

'Upgrade' takes long and it is not very reliable especially if you have modified your system in some significant ways (customized config files, ppas, third party software, proprietary drivers etc) Intuitively one would have an incentive to 'upgrade' instead of fresh install if one has modified things significantly and wants to keep them, but this is exactly when 'upgrade' is likely to leave you with a broken system. If your system is pristine you may as well do a fresh install as it is a lot faster. So I see really no reason to go the route of 'upgrade'.

---

### Post by grahammechanical on 2015-02-15
> [COLOR=#000000]Control-D will terminate this shell and continue booting after retrying[/COLOR]

Did you Ctrl-D? What happened? At the Grub boot menu you can go to Advanced Options for Ubuntu and run Recovery Mode and at the Recovery Menu you can select fsck - check all file systems. See what happens.

Regards.

---

### Post by mn_voyageur on 2015-02-15
Ctl-D adds "exit" but repeats the same error.

I can boot to Recovery.  However, "fsck - check all file systems" did not do anything.  I will reboot to the recovery screen, if you have some suggestions.

---

### Post by mn_voyageur on 2015-02-15
[INDENT]/lib/recovery-mode/recovery-menu: line 76: /etc/default/rcS: no such file or directory
fsck from util-linux 2.20.1
/dev/sda1: Unattached inode 10879998


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
[INDENT](i.e., without -a or -p options)[/INDENT]
mountall: fsck / [614] terminated with status 4
mountall: Filesystem has errors: /
[/INDENT]

Do I force a restart?

monkeybrain20122

I will execute a fresh install, if this is unsuccessfull.  I have upgraded several other computers without any problems.  That is why I chose to run the upgrade.  (FYI - I spent the last two days copying and runing binary checks of my hdd prior to this upgrade.)

---

### Post by efonde on 2015-02-16
> **mn_voyageur said:**
> This morning, I tried to upgrade from 12 to 14.  Once the system rebooted, the screen shows the Ubunut dots, then displays the error messoage:[INDENT]Filesystem check or mount failed
A maintenance shell will now be started.
Control-D will terminate this shell and continue booting after retrying
filesystems. Any further errors will be ignored
root@********:~# [/INDENT]

It will not reboot.  If I force the reboot, it returns to this screen.

Any help would be apprecaited.

MarkN

Perhaps this thread could solve your problem: [http://ubuntuforums.org/showthread.php?t=2181768](http://ubuntuforums.org/showthread.php?t=2181768) .

---

