---
title: "Boot problem"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by gandzo on 2012-10-11
I was working on Ubuntu 12.04 for the whole day without restarting. At one point, the system couldn't start any application - I can't remember what the exact message was, but it was something along the lines "couldn't find chromium-browser in usr/bin" and the same message when I tried to open any other application. I've restarted the computer, but now Ubuntu won't start, not even in safe/repair mode. The message I get is:

run-init : /sbin/init: no such file or directory Kernel panic - not syncing : Attempted to kill init Pid: 1, comm: run-init not tainted 3.2.0-31-generic #50-ubuntu 

Here is my boot-info result: [http://pastebin.com/wtNkBbUv](http://pastebin.com/wtNkBbUv)

---

### Post by darkod on 2012-10-11
If you hold Shift during boot so that the grub2 menu shows up, then select previous Versions and in there try to boot the 3.2.0-29 kernel, does it boot correctly?

---

### Post by gandzo on 2012-10-11
> **darkod said:**
> If you hold Shift during boot so that the grub2 menu shows up, then select previous Versions and in there try to boot the 3.2.0-29 kernel, does it boot correctly?

Grub menu shows up even if not holding shift. I've tried booting the kernel, kernel in 'safe mode', older kernel version, older kernel version  in 'safe mode' - every time the same error message.

---

### Post by gandzo on 2012-10-11
When using Boot repair with default settings I get this message:

An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1273225/](http://paste.ubuntu.com/1273225/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] 

You can now reboot your computer.


The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by darkod on 2012-10-11
Sorry, I don't have any ideas. That message about the boot files being far is not very relevant since the results say they are at 50GB from the start of the disk. Even if your BIOS is affected by the limitation to read boot files, the limit is 137GB which means your current boot files are below this limit and should be readable in any case.

---

### Post by gandzo on 2012-10-11
I've managed to solve the issue. Mind you, I'm unsure what exactly caused it but here's what happened:

I've tried to check disk (disk is fine) and later Purge and Reinstall Grub. The Boot Repair program couldn't help me so I tried this instructions: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) but got stuck on chroot command - "cannot run command `/bin/bash': No such file or directory". The problem was, I had the required directory and the only solution i found  was that you should check if you have a 32 bit installation and trying to repair it with the 64 bit (or the other way around), but that wasn't my case, I have a 64 bit installation and a 64 bit Live disc. Just in case, I went to check the file that was mentioned, ld-linux-x86-64.so.2 and I discovered that for some reason, my lib64 folder was gone and I only had lib32 and lib. Having nothing smarter to do, I created the lib64 folder, copied the symbol/shortcut ld-linux-x86-64.so.2 from lib32 to lib64... and suddenly chroot worked :) I proceeded with the instructions in the post linked here and it all worked; after the restart I managed to log into my system and so far everything seems to be working :)

---

