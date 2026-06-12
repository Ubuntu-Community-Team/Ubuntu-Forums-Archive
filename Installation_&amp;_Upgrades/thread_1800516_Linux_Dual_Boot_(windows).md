---
title: "Linux Dual Boot (windows)"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by BulgarianBoy on 2011-07-09
Hello everyone,
Recently I have been trying to get this game to work with virtual machines but it got really difficult after I learned that maple has patched the ability to run it on VM. SO it brings me to my second plan. I have Linux installed and only Linux I want to make it dual boot where I have windows xp professional installed. I know that if I wanted to do that it would be best to wipe everything and just run the windows xp cd, then it would be best to install linux on a small part. So my question, is it possible to install Linux ( already have it installed) and then install Windows xp without wiping anything? If it is and you know of any tutorials could you please help me out?

---

### Post by An Sanct on 2011-07-09
Welcome to the forums!

Well, you should not wipe anything.

It is simplest to install Windows first and then Linux, since Ubuntu will not mess up Windows. If you do it the other way around, Linux and then Windows, Windows _**will**_ mess up Linux booting, but that can be repaired with a Live CD/USB - its just a hassle :)

Here is a [walk through with screenshots]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") its for 9.04 ... so rather old, I would skip some menu.lst parts (step 2., and parts of step 5.), since they do not apply for newer versions of Linux any more.

Please tell which version of Ubuntu are you trying to use with windows and I will get you the 100% accurate procedure to do so.

---

### Post by YesWeCan on 2011-07-09
That guide is fine if you have Grub-legacy, but does not apply to Grub2. So it depends how old you Grub is.
grub-install -v will show the version, 0.x is old, 1.9x is grub2.
The GParted bit is fine.

Use a live CD/USB same Ubuntu version as your HD install.
You don't really need to back Grub2 up, you can just reinstall it.
If, after you have done repartitioning and installing XP, your Ubuntu partition is called sda2 on disk sda,
[COLOR=Navy]sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

and after booting Ubuntu,
[COLOR=Navy]sudo update-grub[/COLOR]
to add XP to the Grub boot menu

---

### Post by An Sanct on 2011-07-09
+1 I agree here. I was trying to get a little more information out of him :) like the version of Ubuntu he wants to dual boot with Windows XP. That way, I could provide him with 100% accurate instructions.

PS. Again, let me note, that the link I provided in my previous post has *extremely* outdated information and can (**and will!**) harm you install, if it is not Grub (version 1) and Ubuntu 9.04.

---

### Post by BulgarianBoy on 2011-07-09
Hello Everyone,
So let me get this straight I can install windows xp after I have Linux installed? The version I am using is "Ubuntu Release 10.04 (lucid)" I will be back in four hours I have work.

---

### Post by oldfred on 2011-07-09
YesWeCan posted an example of how to reinstall grub2's boot loader after a windows install.

You will have to create a primary partition (sda1 thru sda4) formated NTFS with the boot flag for XP to have a place to install.

If you need more info than posted above.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot version:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by BulgarianBoy on 2011-07-09
I am really lost everyone is saying install windows first I dont want to do that because it will delete everything and my linux will be gone so I would have to re install it. And what is this Grub2 and grub legacy dont know what those are.

---

### Post by oldfred on 2011-07-09
Grub is a boot loader, just like the windows boot loader that is normally in the MBR.

To understand how windows works review the pictures here:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

All BIOS based computers boot from BIOS to MBR - master boot record or first sector on drive. Boot loaders now just have startup code in the MBR and jump to the rest of their code to continue to boot.

If you have a primary partition left to use you do not have to install windows first.

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

---

### Post by BulgarianBoy on 2011-07-09
I liked the pictures they actually were very helpful. Well I found a tutorial on how to do it and it is very detailed, but i got stuck. I was backing up my files and it says "no backups found in the target directory" And I dont know how to fix this. Did a little research and found that I need to enter some lines of code and based on the output of the code I can see why I cant backup something to do with permission.

code:  ls -l /var

output:
total 52
drwxr-x---  3 root root  4096 2011-07-09 20:05 backup
drwxr-xr-x  2 root root  4096 2011-07-09 01:10 backups
drwxr-xr-x 19 root root  4096 2010-12-04 17:53 cache
drwxrwxrwt  2 root root  4096 2011-01-30 07:35 crash
drwxr-xr-x  2 root root  4096 2010-08-16 02:48 games
drwxr-xr-x 68 root root  4096 2011-07-08 23:33 lib
drwxrwsr-x  2 root staff 4096 2010-04-23 03:11 local
drwxrwxrwt  3 root root    80 2011-07-09 20:05 lock
drwxr-xr-x 17 root root  4096 2011-07-09 17:37 log
drwxrwsr-x  2 root mail  4096 2010-08-16 02:32 mail
drwxr-xr-x  2 root root  4096 2010-08-16 02:32 opt
drwxrwxrwt  3 root root  4096 2011-07-08 16:25 parallels
drwxr-xr-x 18 root root   880 2011-07-09 19:47 run
drwxr-xr-x  9 root root  4096 2010-10-22 21:23 spool
drwxrwxrwt  3 root root  4096 2011-07-09 20:23 tmp

second code: sudo ls -l /var/backup
second output:
total 4
drwxr-x--- 2 root root 4096 2011-07-09 20:05 2011-07-09_20.05.24.756358.moris-laptop.ful


Any ideas. I am probably going to have to re post this because I am starting a new topic inside a topic.

---

### Post by Marky FAQ on 2011-07-10
Yes, but I think you need to install windows first because GRUB boot-loader needs to be the major boot-loader of your system, and if you install linux and then windows, the boot loader of windows will replace GRUB, You will not be able to run linux.

Linux then Windows.
It works.

---

### Post by oldfred on 2011-07-10
If you are getting no system, it can be you have no boot loader in any bootable device particularly the hard drive. But a few BIOS (primarily Intel motherboards) check that a boot flag is on a primary partition before it will even try to boot. That assumes windows as grub does not need boot flag, but if you have an Intel motherboard put a boot flag on any primary partition. If installing windows it has to be on the primary NTFS partition that you install into.

More info on partitions and mounting.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

If it is NTFS it will show root as owner, but the way you mount it will give you permissions:
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by BulgarianBoy on 2011-07-10
I think I am just going to wipe everything, and install windows first. this is just way to hard.

---

### Post by An Sanct on 2011-07-10
> **Marky FAQ said:**
> Yes, but I think you need to install windows first because GRUB boot-loader needs to be the major boot-loader of your system, and if you install linux and then windows, the boot loader of windows will replace GRUB, You will not be able to run linux.

Linux then Windows.
It works.

Yes, that is the preferred way, but if you do it the other way around (sometimes it cannot be avoided), you can remake Grub (1/2) the default boot manager ...

---

