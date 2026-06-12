---
title: "Breezy Badger hangs when installing Grub"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by Innova on 2005-11-16
I did a search and saw a few other posts with a similar problem.  However, either they didn't have a solution, or the solution didn't work for me.

Here is my setup:

Athlon 64 X2 3800+
Epox EP-9NPA+Ultra (nForce4 Ultra)
Hitachi Deskstar 7k250 (First partion (100 GB) is NTFS with Windows XP Installed)  The drive is hda (Primary on IDE0).
NEC ND3540A Primary on IDE1
Geforce 6800 GS

I have been using Redhat and Fedora for years on my old computer.  I just bought this one, and decided to try Ubuntu.  For that reason I decided to go with the i386 version, and not deal with any 64bit problems, at least not yet.

The installation goes fine.  I told Ubuntu to use the remaining 150 GB on my disk, and used the default partitions.  I get all the way through the installation, even creating the first user.  Then the installation tries to install GRUB to the MBR, and it just hangs.

After I rebooted the MBR was messed up and I couldn't boot into ubuntu or windows.  I tried to use windows recovery mode, and fixmbr, but even that didn't work.  I had to completely reinstall windows.

Does anyone have any solutions or workarounds for this problem?  I don't currently have a floppy drive, so installing grub there won't work.  (Can you install grub to a SD card on a USB reader?)

Any help is appreciated.  I would really like to get this working, so I don't have to re-install Windows again.

---

### Post by yesplease on 2005-11-16
You can use the procedure which is used for a floppy disk, instead of writing to floppy with /dev/fd0 you write to the dev for the usb stick. 

I used this procedure for floppy once [http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+floppy+howto](http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+floppy+howto)

but there is another procedure with the rescue mode of the install disk (you have to search for it).

I am not so sure if it was necessary to reinstall windows, but you already did that.

---

### Post by Innova on 2005-11-17
No one knows what the cause of the hang could be?  I would really like to make sure that I don't mess up my XP installation.  It didn't matter last time, but now I have alot of other things installed.  (I tried to get it to boot, but kept getting a hard disk error, even after fixmbr.)

---

### Post by Innova on 2005-12-10
I would really like to give Ubuntu another try, but I know it will just hang again.  Has anyone else scene this problem with similar hardware and found a solution?

---

### Post by yesplease on 2005-12-11
It is hard to say something about the cause of this problem. Check the bios options for something that prevents writing to the mbr.

I think you should be able to install ubuntu. When the only problem is writing to the mbr, a workaround is to write grub on another bootable medium, like a bootable usb stick.

You can do that after install with: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)
where you change /dev/hda to the bootable usb stick.

---

### Post by ejm on 2005-12-30
I struggled with this issue where the installer would hang and finally give an error when installing grub. The answer for me was to select ReiserFS instead of ext3 during partitioning and GRUB installed fine.

After I had success with this, I repeated the installation and it worked a second time, so it seems to me the combination where this problem occurs is:
-  Ubuntu
- ext3
- GRUB
- i386 build
- amd64 hardware

I did not experience this problem when I installed Debian etch on the same hardware using the i386 build, ext3 and grub.

---

### Post by ZAxisMapping on 2006-03-30
I was encountering the same exact issues with grub install hanging at 0% for a Ubuntu install on my second SATA drive /dev/sdb (/dev/sda has windows).  I switched the root Ubuntu partition to ReiserFS and the installer had no issues with apt-get install grub!!!

The question I have now is....do I really want to be running ReiserFS?  AND, will there be any issues with permissions, etc., for transfering files back and forth from an ext3 filesystem?

---

### Post by ZAxisMapping on 2006-03-30
I also found success doing the following:

[http://ubuntuforums.org/showthread.php?t=66160]("http://ubuntuforums.org/showthread.php?t=66160")

This allowed me to stick with ext3.


Read my entire experience here:

[http://ubuntuforums.org/showthread.php?p=877125]("http://ubuntuforums.org/showthread.php?p=877125")

Hopefully these will work for you.  There seems to be many people encountering issues with the grub install.

---

