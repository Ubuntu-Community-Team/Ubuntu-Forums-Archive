---
title: "PC won't boot, GRUB doesn't appear at startup, boot-repair cancels itself"
date: 2014-11-09
forum: Installation &amp; Upgrades
---

### Post by owen7 on 2014-11-09
I had a GRUB dual boot Win XP and Ubuntu 7.10. Yesterday under Windows XP,  I made mistake to format some free (Ubuntu ? ) partition. It finished without error. It maybe  destroy some Ubuntu information.

When I restart the computer today, got error:

GRUB Loading Stage 1.5,
GRUB loading, please wait
Error 17

After search the forum, I created Boot-Repair disk (usb), and Ubuntu-Secure-CD 32bit (usb). Tried to boot from both USB, run Boot-Repair, but got same error,

grub-pc purge cancelled, please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

My BootInfo summary link is [http://paste.ubuntu.com/8892845/](http://paste.ubuntu.com/8892845/)

I can access my files on driver C:, D:, E: from Ubuntu Live Session

Many thinks in advance !

---

### Post by yancek on 2014-11-09
> Error 17 : Cannot mount selected partition

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.  Usually happens when trying to directly boot a windows partition rather than chainloading it.  Your version of Ubuntu (7.10) has not had any support for over 5 years and is totally outdated.  Based on the output you posted, it looks like you deleted a logical partition which resulted in partitions with higher numbers being changed.  You Ubuntu is on sda6, which in Grub Legacy which you have would be (hd0,5).  Your menu.lst file shows it as (hd0,6) which would be sda7.

The simplest fix would be to boot any Linux Live CD, mount the sda6 partition then go to the /boot/grub/menu.lst file and change the entries for Ubuntu on each of the root lines shown below by replacing the 6 with a 5.

```
root        (hd0,6)
```

It would also be a very good idea to upgrade to a supported version.  Since your current system is so old, the only way you can do that is a fresh install of 12.04, 14.04 as long term support versions or the most recent 14.10.  Check the minimum hardware requirements at the Ubuntu site to compare with your hardware.

---

### Post by owen7 on 2014-11-09
Hi yancek,

Thanks for your reply. I boot from Boot-Repair-Disk, used FileManager PCManFM, navigated to /media/lubuntu/[COLOR=#000000]6570b185-97b2-49e1-bf86-daf67975fe87/boot/grub, then select Tools->"Open Current Folder as Root", open menu.lst file, changed all the entries of  root (hd0,6) to  root (hd0,5)

[/COLOR]Reboot the PC, got same GRUB Error 17. Tried the Boot-Repair again, Ubuntu did something, then "[COLOR=#000000]grub-pc purge cancelled.." error again.

[/COLOR][COLOR=#000000]The new [/COLOR][COLOR=#000000]BootInfo summary link is [/COLOR][http://paste.ubuntu.com/]("http://paste.ubuntu.com/8892845/")8911957/[COLOR=#000000]

I looked at the end of the link, there are lots of "Failed to fetch [http://.](http://.)..,  404 file no found"

Many Thanks ! 
[/COLOR]

---

### Post by oldfred on 2014-11-10
Boot-Repair will not work. 
It wants to do a full grub purge and reinstall from repository. 
But repository for your version has long been closed.
It also is really set for newer grub2 since grub2 has been standard since 9.10. It will purge all versions of grub and reinstall a nice clean version of grub2 from repository. Even if repository was open there was no grub2 with your version.

You still show in grub boot stanza:
root        (hd0,6)

Grub legacy counts from zero and grub2 now counts from one. With grub 2 sda1 is hd0,1, but with grub legacy it is (hd0,0)
Or your new entry should be (hd0,7) for sda6.

---

### Post by yancek on 2014-11-10
The boot repair output in your last post still shows the entries for root as:  root (hd0,6) which won't work.  The other problem is that Grub in the mbr is looking on partition 7 for the boot files and they are on partition 6 (sda6).  A simple fix for this if you still have the 7.10 CD would be to boot it, open a terminal type sudo grub.  That would get you the grub prompt (grub>) where you would type:  root (hd0,5) (hit the Enter key) then type:  setup (hd0) (hit the Enter key) and when it finishes, type quit and hit Enter.  If you don't have the Ubuntu 7.10 install CD or any other Linux with Grub Legacy, that won't work.  

The end of the boot repair page indicates there was an option to re-install Grub2 which you did not select.  I'm not familiar with boot repair so don't really know how that would work.

---

### Post by owen7 on 2014-11-10
Hi Oldfred,
changed default grub root devices to groot=(hd0,5) in file sda6/boot/grub/menu.lst , reboot, still same error as before.

Also, changed all groot=, root= entry to (hd0,7) in /boot/grub/menu.lst, reboot, same error

How can I remove GRBU 0.97 and boot to Windows directly ?

---

### Post by oldfred on 2014-11-10
You can use your Windows install disk and from repair console run fixMBR command. That adds the Windows boot loader to the MBR.

Boot-Repair using advanced mode may install the syslinux boot loader which works just like the Windows boot loader. 
Windows type boot loaders, just check partition table for boot flag and jump to that partition's boot sector to find more boot code. Any Windows type boot loader should work for that. 

But you know XP is now obsolete and while you can run it, you never should connect to Internet with it.

---

### Post by yancek on 2014-11-10
> changed default grub root devices to groot=(hd0,5) in file sda6/boot/grub/menu.lst , reboot, still same error as before.


As I indicated in my previous post, that won't help as you have the boot code in the mbr still pointing to sda7 and you would need to chroot into the system and install Grub again to the mbr.  That would work if you still had your 7.10 install CD or some other Linux CD with Grub Legacy.  You would probably be better off updating your Ubuntu since your system is very outdated.

---

### Post by owen7 on 2014-11-10
Thanks yancek and oldfred for your help ! Problem solved. GRUB loaded, booted into Windows again.

Downloaded and burned a Ubuntu 7.10 desktop 32bit DVD, boot to it, and open a terminal .Then followed yancek's notes: 
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit

some issue I made: 1) I created a Ubuntu 7.10 usb disk, boot to it. then when I type roob (hd0,5), it's said no such device. 2) When boot to Ubuntu 7.10 DVD, open a terminal. At the beginning, I just type "grub" , that doesn't work. Later I use "sudo grub", it worked.

Many thanks to Ubuntu forum again.

---

### Post by yancek on 2014-11-10
> some issue I made: 1) I created a Ubuntu 7.10 usb disk, boot to it. then when I type roob (hd0,5), it's said no such device

That is because the usb device sees itself as sda or (hd0) so it probably would have worked with root (hd1,5).  Don't have that problem with a DVD so when using a flash, always run fdisk or use gparted to see which drive is seen as sda.

---

