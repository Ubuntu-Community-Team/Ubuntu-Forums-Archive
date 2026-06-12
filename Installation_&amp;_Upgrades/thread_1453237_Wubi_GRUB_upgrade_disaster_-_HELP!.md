---
title: "Wubi GRUB upgrade disaster - HELP!"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by Wtwine on 2010-04-13
Hi 

I really need some urgent help please.

I run my laptop on dual boot Ubuntu 9.04/Windows XP, with a Wubi installation.

In anticipation of upgrading from 9.04 to 10.04, I upgraded from grub-legacy to grub 2 as suggested on various sites.

Now when I boot, I get "error: file not found"  and it enters grub rescue mode. When I type "boot", it says "no loaded kernel".

I can't boot into Ubuntu or Windows.  I can access my Windows partition via file manager when running Ubuntu from Live CD

I have tried various solutions from various sites but to no avail (e.g. replacing wubildr with patch, because it is only for 9.10    _[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)_)

I need this machine for work today, so I am really stuffed!  Please help ASAP if you can - much appreciated.

I'm a relative noob, but this may help - output while following instructions on one of the sites (while running Ubuntu from live cd):

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12132    91717888+   7  HPFS/NTFS
/dev/sda2           12133       12921     5964840    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
mount: mount point /mnt/sys does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ dpkg-reconfigure grub-pc
/usr/sbin/dpkg-reconfigure must be run as root
ubuntu@ubuntu:~$ sudo dpkg-reconfigure grub-pc
Package `grub-pc' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: grub-pc is not installed

---

### Post by crom.osec on 2010-04-13
Have you tried:
```

sudo update-grub

```

?

---

### Post by Wtwine on 2010-04-13
I assume you mean at grub rescue>, since I can't get into terminal

When I enter 'sudo update-grub' at 'grub rescue>', I get a message saying "unknown command 'sudo'".

---

### Post by crom.osec on 2010-04-13
you could try to boot with a live cd and then use chroot to change the root to your linux root disk and then update-grub.

I haven't tried this until now, but it should work:
- Booting with live-cd you'll get internet access and also you can access your disks.
- You can use fdisk -l to see your partitions and find out which is the root drive (it should be something like /dev/sda ).
- You then move the root to that drive using chroot. You'll need this because I think that update-grub is looking at config files based on the current root.

---

### Post by Wtwine on 2010-04-13
Thanks for your help crom.osec

I booted from cd, went to terminal and typed fdisk -l.  Nothing happens, just new "ubuntu@ubuntu:-$" appears (worrying!).    

Any way, my linux root was at sda1 if I remember correctly, but when I enter "chroot /dev/sda1", I get the following message:
"chroot: cannot change root directory to dev/sda1: Not a directory"

This doens't look good!

---

### Post by Wtwine on 2010-04-13
Some more info that may help:

After booting from cd, I opened Gparted.  It shows /dev/sda1 (ntfs)  which is flagged as "boot", and /dev/sda2 (fat32) which is the HP-recovery partition.  So now we have confirmed that /dev/sda1 is correct , so why can't I chroot /dev/sda1??  Also tried chroot /dev/sda, but get same error ("not a directory")

When I enter "cat /proc/partitions", I get the following:

7   0    691260       loop0
8   0    97687784   sda
8   1   917178888  sda1
8   2    5964840     sda2

When I first encountered the grub probel, i followed instructions on a Ubuntu Grub site for Wubu installatins.   I had entered "set root=(loop0)" in grub rescue> as instructed,  but when I entered "linux boot/vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro" I got an error saying "linux" was an unknown command.

As a last resort, if I uninstall WUBI, will I be able to boot into Windows agains, and reinstall WUBI, or will this grub problem persist even if WUBI is uninstaled?  All my documents are backed up, so it's not the end of the world if I unisntall WUBI.

---

### Post by Wtwine on 2010-04-18
Well, nothing on any relevant threads worked for me, until I stumbled across one mentioning Super Grub Disk.  I downloaded and installed it on my USB flashdrive and booted up from USB.  This enabled me to boot into Windows, but not Ubunu.  Thereafter, booting from HDD presented the dual boot options, and Windows booted fine, but Ubuntu still returned file errors 11 and 15.  I tried everything suggested on various sites to no avail.  Fortunalety, I had all my files backed up, so I eventually bit the bullet and uninstalled Wubi in Windows.   I reinstalled Wubi (can't install Ubuntu natively as I have a bad sector on my hard drive) and now dual boot works perfectly again.

I am now happily back in Ubuntu.  I obviously lost my previous configuration and additional software installations, but it only took me a day to get back to where I was previously.

Won't mess with grub again unitl I really have to!

Cheers.

---

### Post by oldfred on 2010-04-18
With wubi you are using the windows boot loader in the MBR, you would not install/reinstall grub to the MBR.

There is a bug that appears with grub in wubi and NTFS partitions. You should still run this fix.

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Wtwine on 2010-04-19
Ok.  Thanks.

---

### Post by doubleiro on 2010-08-28
Hi evryone, 

even though the problem is declared as "SOLVED", i got nearly the same issue and found another way to fix it. 

Situation: I got a netbook without cd-rom-drive and no usb-boot-option in the bios. I installed Win-XP and used a wubi-installation of Xubuntu as well. 
After the kernel update from 9.10 to 10.04 the new Grub2 MBR has been written over my old one - due to a inattentive user (me :) ). After a reboot i permanently ended up with the grub-recovery-console, unable to boot any of my kernels. 

My Solution: I took off the hard disk, put it into a external usb drive (cost me 10€) and connected it to a working Win7-PC. Then i used the tool "Testdisk" to analyse the partitions on the external usb-drive. My hard drive was found imediatly, and testdisk offers an option to "write testdisk MBR on Drive". After one second the operation was finished and i rebuild the hard disk into my netbook. Instantly i could boot with my old Bootmanager, every Kernel is working still fine (so to say Xubuntu wubi and WinXP). 

For some of you this might be a better solution than the XP-Boot-Cd or the wubildr-fix, espacially for those like me who don't even have a cd-drive.


OFF-TOPIC: By the way, if you want to install any operating system on a netbook without cd-drive and no usb-boot-option by factory setting, use the PLOP!-Bootmanager. It must be written into the MBR of your Hardrive (same procedure as above, means taking the hard drive out the notebook, into an external case and connect it to another pc) and offers you a usb-boot-option. Thats how I remake my operating systems... 

Greetz

---

### Post by JOSEA.MESA on 2010-10-05
Hi everybody:

I had the same problem with grub, I though that I had loosen my information 

I ran the fix that suggest oldfred at [http://sourceforge.net/apps/mediawik...lems:Wubi_9.10 ]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

and It works fine.

thank you

---

### Post by stanelie on 2010-10-12
Hum, just had a similar problem while upgrading from Ubuntu 10.04 to 10.10, with wubi.

I fixed it by copying the wubildr located in C:\ubuntu\winboot\ to c:\, overwriting the one already there.

---

### Post by redfish907 on 2010-10-13
> **stanelie said:**
> Hum, just had a similar problem while upgrading from Ubuntu 10.04 to 10.10, with wubi.

I fixed it by copying the wubildr located in C:\ubuntu\winboot\ to c:\, overwriting the one already there.

Thank you!  I had the exact same problem, and your solution fix it.

---

### Post by rgstrator on 2010-11-22
Hej everybody,

Just FYI, even though I _DID_ check on "use grub" during the update, I still got the problem- even more disturbing is the fact that I was not upgrading between any major Ubuntu versions, but I think an automatic kernel upgrade slipped through- all by the default Ubuntu desktop settings.

If you're new to this, don't panic; this is a boot loader error so your data is almost certainly intact.

I don't know if this is redundant, but after doing *this* [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)  -(*replacing wubidlr*) I thought I would try the 'built-in' solutions on **Super Grub Disk **([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) (*read also their Wiki, it explains step-by-step how to make a USB boot disk*) - more specifically, I wiped out the MBR through the appropriate menu option (which had absolutely no effect), but the option that repairs & boots the _WINDOWS_ chainloader (the one with the very unhappy smileys like this :(((((((((((((((((((( ) worked immediately, instantly fixing everything.

I think that this happened because a 'wubi'-ubuntu loads through the windows loader anyway (a 'boot linux' entry is added on the windows loader, and -if selected- then grub is called and boots whatever linux you got).

A word to the Ubuntu developers: All the above can be devastating to the simple user, since without the knowledge of how to make and use a USB boot a netbook can be rendered useless, just by going through a perfectly innocent-looking trivial system update. I would assume this can be very common, as a person on one of the first posts did NOT check on the "use grub", and I DID check on it during the upgrade, but BOTH ways seem to lead to a bricked system.

---

