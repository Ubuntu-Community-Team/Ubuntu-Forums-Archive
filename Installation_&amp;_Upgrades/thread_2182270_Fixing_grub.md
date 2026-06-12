---
title: "Fixing grub"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by Victor_Lai on 2013-10-20
Hi guys,

I am reinstalling a Home Server that I've installed Ubuntu 12.04 LTS server edition on.
Reinstalling from a USB key (since the server didnt have any CD roms), and I keep getting stuck on installing grub-pc into /target.

I then started attempting the grub recover from [http://opensource-sidh.blogspot.ca/2011/06/recover-grub-live-ubuntu-cd-pendrive.html](http://opensource-sidh.blogspot.ca/2011/06/recover-grub-live-ubuntu-cd-pendrive.html).

Followed every step and was OK until I attempted:

```
update-grub2***update-grub*** 
***update-grub*** 



```

The chroot prompt complains that 
```
THe program 'update-grub2' is currently not installed.  You can install it by typing: apt-get install grub2-common
```

When I try to install grub2-common, I get the usual Do you want to continue [Y/n]?

As I enter y, I get

```
Media change: please insert the disc labeled 'Ubuntu=Server 12.04.3 LTS _Precise Pangpolin_ - Release i386 (20130820.2)' in the drive '/media/cdrom/' and press enter
```

When I press enter, the same message keeps coming.

I exited the apt-get by Ctrl-C.  When I check the /media/cdrom/ folder, there is nothing in there.  I tried to mount /dev/sdb1 (where my USB is) and shell tells me that according to mtab, its already mounted there....

I am completely lost :confused::confused::confused:

Help is much appreciated....

---

### Post by Victor_Lai on 2013-10-20
Attached screenshot

---

### Post by oldfred on 2013-10-20
It looks like your chroot also wanted to install the full desktop, did you want that?

From a live installer run this, or download it as a new repairCD.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Victor_Lai on 2013-10-24
Hello,

Finally got around to making this report....  I am going to try the repair tonight.

The report that was generated

[http://paste.ubuntu.com/6296984/](http://paste.ubuntu.com/6296984/)

Much thanks for anyone that could help and thanks to oldfred already!

---

### Post by oldfred on 2013-10-24
Grub did not install. What was the error on grub-pc? It looks like it is missing entirely as you have no grub in MBR nor grub.cfg nor core.img.

From boot-Repair you can do a purge (in your case nothing to purge) and total reinstall. I would suggest that.

Do you have pc on working Internet? Boot-Repair or install of grub-pc really needs that. You may be able to change source to DVD or flash installer, but better to use Internet.

---

### Post by Victor_Lai on 2013-10-25
Thanks oldfred.

I ran boot-repair and it fixed grub and I was able to install the server again!
Much thanks again!

---

