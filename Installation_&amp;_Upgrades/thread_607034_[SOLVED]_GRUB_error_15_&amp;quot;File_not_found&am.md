---
title: "[SOLVED] GRUB error 15 &amp;quot;File not found&amp;quot; after upgrade from Feisty to Gutsy"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2007-11-08
The initial problem after the upgrade, which was performed with 'gksu "update-manager -c"', was that GRUB  ignored  /boot/grub/menu.lst.  This was solved by deleting all the files in /boot/grub, restoring menu.lst, and running "sudo grub-install hd0"

The section of menu.lst that fails to load is:[INDENT]title           Ubuntu 7.10, kernel 2.6.22-14-generic
   root            (hd0,0)
   kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
   initrd          /boot/initrd.img-2.6.22-14-generic
[/INDENT]The kernel file /boot/vmlinuz-2.6.22-14-generic and  and ram disk /boot/initrd.img-2.6.22-14-generic entries (which were created by "update-grub")  point at files that are definitely there.

This section of menu.lst loads perfectly:[INDENT]title           Ubuntu 7.10, kernel 2.6.20-16-generic
   root            (hd0,0)
   kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet splash
   initrd          /boot/initrd.img-2.6.20-16-generic
[/INDENT]Help!!

David

---

### Post by tech9 on 2007-11-08
> **davidkahn said:**
> The initial problem after the upgrade, which was performed with 'gksu "update-manager -c"', was that GRUB  ignored  /boot/grub/menu.lst.  This was solved by deleting all the files in /boot/grub, restoring menu.lst, and running "sudo grub-install hd0"

The section of menu.lst that fails to load is:[INDENT]title           Ubuntu 7.10, kernel 2.6.22-14-generic
   root            (hd0,0)
   kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
   initrd          /boot/initrd.img-2.6.22-14-generic
[/INDENT]The kernel file /boot/vmlinuz-2.6.22-14-generic and  and ram disk /boot/initrd.img-2.6.22-14-generic entries (which were created by "update-grub")  point at files that are definitely there.

This section of menu.lst loads perfectly:[INDENT]title           Ubuntu 7.10, kernel 2.6.20-16-generic
   root            (hd0,0)
   kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/md0 ro quiet splash
   initrd          /boot/initrd.img-2.6.20-16-generic
[/INDENT]Help!!

David

download supergrub disk iso and make a recovery CD
[http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)

---

### Post by davidkahn on 2007-11-08
Thanks.  I can now boot the Gutsy kernel.

Super GRUB showed that the Gutsy kernel was on hd1 rather than hd0.  So changing "root            (hd0,0)" to "root            (hd1,0)" allowed  /boot/vmlinuz-2.6.20-16-generic to boot.

The only thing left to understand is how it is possible that the new kernel is on a different disk, as the two hard drives in this PC are in a Linux software RAID array (versus having a hardware RAID controller), and one would therefore expect that their contents would be identical.

---

### Post by tech9 on 2007-11-13
> **davidkahn said:**
> Thanks.  I can now boot the Gutsy kernel.

Super GRUB showed that the Gutsy kernel was on hd1 rather than hd0.  So changing "root            (hd0,0)" to "root            (hd1,0)" allowed  /boot/vmlinuz-2.6.20-16-generic to boot.

The only thing left to understand is how it is possible that the new kernel is on a different disk, as the two hard drives in this PC are in a Linux software RAID array (versus having a hardware RAID controller), and one would therefore expect that their contents would be identical.

Your Welcome!

---

### Post by JunCTionS on 2007-11-14
Not so solved for me :(
same issue, after a buggy attempt (actually after the second attempt, first one didn't mess the system up so much) to upgrade Feisty Fawn to Gutsy Gibbon using the Adept Updater it stopped (just like the first time) so I rebooted to retry since it said another program was still using adept.

apparently it still has the old options of the GRUB (2.6.20-16 and 2.6.20-15) the first doesn't work (File Not Found...) and in the second KNetworkManager "doesn't find any network devices

Also both the -15 and the -16 are in (hd0,0) so it's not about which partition the kernels are in. 

any thoughts? 
So far I've: 
[LIST]
[*]Tried deleting all files in /boot/grub (backing them up first) and restoring menu.lst and "sudo running grub-install hd0" succesfully
[*]Downloaded and booted the Grub Super Disk, again "succesfully" fixing the grub
[*] Tried several combinations of (hd0,0) (hd0,1) (hd0,2) (hd1,0)(hd1,2) with which it changes the error to "unable to mount partition" or something like "invalid disk"
[/LIST]
I'm running on a Toshiba Sattelite with one HDD (so I'm not following the GSD's suggestion for 2 or more disks). It has a Windows Vista partition (that I have to run to have Internet now).

---

### Post by davidkahn on 2007-11-14
I am  fairly certain that the problem is not with GRUB, but rather that you haven't correctly installed the Gutsy kernel yet.  Both of the kernels you listed are Feisty.  If you do not have the file /boot/vmlinuz-2.6.22-14-generic then your system probably never got to the point were it installed the Gutsy kernel.

I have never heard of the Adept updater.  Is that specific to Kubuntu?  Have you tried upgrading using the standard method:[INDENT][https://help.ubuntu.com/community/GutsyUpgrades?highlight=%28upgrade%29](https://help.ubuntu.com/community/GutsyUpgrades?highlight=%28upgrade%29)
[/INDENT]If installing the Gutsy kernel is all that you need to do, it is possible to do with apt-get.

---

### Post by JunCTionS on 2007-11-14
it does have the three possible vmlinuz files (.20-15, .20-16 and .22-14) but as you noted it aparently didn't update de GRUB or something.
another thing I had tried before was changing 20-16 to 22-14 in all the parts of the menu.lst where it appeard.
As for Adept, yeah, silly me, forgot this is the **ubuntu**forums ;), it's the GUI package manager for KDE.

I will try to do the install, problem is, I don't have Internet access on kubuntu anymore (as noted before) so I guess I'll try to do it from the liveCD (didn't want to download it since I have some shipits on the way, but when the updater showed me the shiny "update distribution" button I just couldn't resist).

still, any other suggestions are welcome. (been looking at the other threads as well, none work).

---

### Post by davidkahn on 2007-11-14
I noticed that you have run grub-install.  Have you also run update-grub?  That's the program that updates /boot/grub/menu.lst.

---

### Post by JunCTionS on 2007-11-14
:lolflag: that was probably a noobie mistake

it... made progress. added the new kernel to the GRUB list of now three (times two per their recovery modes plus memtest plus Vista).

but... :( 
running it now gave me a diferent problem (don't know the ethics here, please tell me if I should start a new topic).

So it says:
"Starting up ...
[     19.026583] PCI: BIOS BUG #81[49435000] found
[     19.689177] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

it has always told me about the Bios bug, I think before it had less detail, but I just say it in case it might have anything to do with the new kernel not dealing with this bug as well as the previous kernel did. (guessing not).

anyways, as of this topic... I guess it worked to fix the "File not found".

P.D: Also happens for the .20-16 kernel only with different numbers at the start (guessing these are times or something), and another line more at the end [0.671680] <6> Time: tsc clocksource has been installed. 
Also in both cases caps lock blinked, the .20-14 still "works" (without network)

---

### Post by davidkahn on 2007-11-15
Your problem is beyond my capabilities, except to note that it's a Virtual File System error.  You should definitely start a new thread, because this one is not going to attract help from the people you need.
 
I Googled "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)" and got some useful results.  You might want to do this before creating the new thread.

Good luck.

David

---

### Post by gos1 on 2008-03-09
i have the same problem . And I deleted all the files in the /boot/grub and cannot re-install right now . When I run the command sudo grub-install hd0

 I get this error message 

ubuntu@ubuntu:/mnt/disk/boot$ sudo grub-install hd0
Could not find device for /boot: Not found or not a block device.

 What should I do now

---

### Post by davidkahn on 2008-05-05
Take a look in /boot/grub/device.map.  Mine says:[INDENT](hd0)    /dev/sda
(hd1)    /dev/sdb
[/INDENT]You're probably not going to see an hd0.  But the correct device should be obvious.  Note that it's okay to say /dev/sda (which is a SATA drive) rather than hd0.

---

