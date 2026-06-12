---
title: "Fubar MBR &amp; Grub issues"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by piercethelutheran on 2013-08-12
Runing 13.04 & Windows 8 on a Y500 Lenovo Idea pad with 1tb drive and 16GB ssd.

I have windows 8 on there but after some poor choices in installation techniques, then windows 8 partition is inaccessible. I have not missed it much seeing as I have been able to run my favorite MMO's on there, but my offline games and things are still on that partition.

It did the thing where grub loads the windows boot loader and then it says it was unable to find the installation.

Below is the log from Boot-Repair

[http://paste.ubuntu.com/5979601/](http://paste.ubuntu.com/5979601/)

I ran the recommended fix but it gave said 
Boot successfully repaired.

[INDENT]Please write on a paper the following URL:[/INDENT]
[INDENT][http://paste.ubuntu.com/5979649/](http://paste.ubuntu.com/5979649/)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]In case you still experience boot problem, indicate this URL to:[/INDENT]
[INDENT]boot.repair@gmail.com or to your favorite support forum.[/INDENT]
[INDENT]
[/INDENT]
[INDENT]You can now reboot your computer.[/INDENT]
[INDENT]Please do not forget to make your BIOS boot on sdb (1000GB) disk![/INDENT]
[INDENT]
[/INDENT]
[INDENT]The boot files of [The OS now in use - Ubuntu 13.04] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
[/INDENT]

The last part of the message is confusing and I need some help understanding it.

To be honest I had more questions when I decided to write this but I'm blanking. I'm willing to answer your questions if there are some.

TLDR: I want to be able to properly dual boot both windows 8 an 13.04 without wiping either partition.

Also, I'm sorry I know that hard drive is hideously organized and partitioned.

---

### Post by piercethelutheran on 2013-08-12
Also Sdb5 is the windows data and sdb8 is the 13.04 install. Those ones need to be preserved.

---

### Post by oldfred on 2013-08-12
What Windows entry are you using?
Did you turn off fastboot in Windows as that is permanent hibernation and causes all sorts of issues.
Did Windows boot with secure boot off?

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bkpbootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

See also link in my signature for lots of info and many useful links on UEFI.


 Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

       
  [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

---

