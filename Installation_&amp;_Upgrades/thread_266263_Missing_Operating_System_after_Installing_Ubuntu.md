---
title: "Missing Operating System after Installing Ubuntu"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by Duwi on 2006-09-27
I got a Thinkpad T60 this week and tried to install Ubuntu on it.
I read several webpages that warned me of not installing grub into the MBR of my hdd to keep the ThinkVantage button functioning. So I didn't, when the installation program asked me where to install grub I decided to put it into the / partition Linux system.
After rebooting I was honestly expecting Windows to boot up, since I thought I never touched the Windows bootloader. What I found was that I got a message
Operating System missing. Nice....

So I rebooted again and kept pushing the ThinkVantage button, lucky me, that one was still working and I got into the recovery software.
I can now of course restore factory settings and start all over again, but would prefer to somehow, restore my MBR and than do the chain-thing to get to my grub. (modifying boot.ini to link to a file that grub is supposed to give me)

Does anyone can help me?


I used the Ubuntu alternative installation CD and installed in OEM mode.

thanks a lot

Maik

---

### Post by Jeremy23 on 2006-09-27
Don't panic, your operating systems are *probably* still there.

If you boot up with your Windows XP or Windows 2000 installation disc and start the recovery console, the fixboot and fixmbr commands are your friends.

You may then want to follow the gist of this: [http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

The above link will take you to a Red Hat guide for booting Linux via the Windows boot loader. What you want is to keep your Windows MBR intact and use the Windows boot loader to load GRUB. Perhaps you may find something useful in there, but I'm still too newbie with Linux to help you any further.

I personally think that installing GRUB to the MBR is harmless - I've never had any problems with it. However, if what you say is true then I guess it's a bad idea.

---

### Post by Jonie on 2006-09-27
See my similar post. 

[http://www.ubuntuforums.org/showthread.php?t=255117](http://www.ubuntuforums.org/showthread.php?t=255117)

You can also use testdisk to write new mbr in case when original one is corrupted. What's specific to portable computers is that they hold a hidden fat32 partition to deploy and restore oem windows install.

In your case it seems that GRUB declined to install. It might fail when partition table has some bugs. You might have also changed the active partition.

So:

play with testdisk and see whether:

Windows partition is marked active (this will probably be the second partition as the first will be hidden fat32)

If not, mark it. Then write testdisk mbr code.

If you computer doesn't still boot, but hangs without displaying Missing Operating System anymore, XP boot sector may be corrupt.

Testdisk is also handy here. Use the following advice ONLY if the partitions layout has been changed (you shrinked or moved XP partition). Fiddling with NTFS boot sector (given it's NTFS and not FAT 32) may render file system inaccessible. In advanced options hightlight XP NTFS partition. You can then rebuild boot sector. It will take some time, as it will scan for MFT. Then it will tell whether new BS is different and would ask should you write new BS. FIXBOOT from Recovery Console does NOTHING but restoring BS from backup, what in more complex scenarios will not help.

---

### Post by Fatjoint on 2006-09-27
Seeing the "Operating System Not Found" error after installing Grub usually means that your boot.ini is pointing to the wrong partition for the start of Windows.

---

### Post by Duwi on 2006-09-27
thanks for all the replies.
I really appreciate them.
I have to admit, I paniced (since a T60 is not the most affordable Laptop purchase for a grad student) and reinstalled the factory settings using the recovery partition that I was still able to get into.

But supposedly the Linux partitions that I created during the Ubuntu Installation are still there.
I just don't know how to get there and get the file needed to change the boot.ini to start grub (that is not installed in the MBR)

In case one of you has some information about how to boot into my (hopefully still there) Ubuntu and than convince grub to create me a file that I can copy into c:\ on my windows.
that would really help

thank a lot
Maik

---

### Post by Jonie on 2006-09-28
If you installed GRUB in the boot sector of Linux partition, you have to boot Linux off the cd, then copy this boot sector to a file on floppy

mount dos formatted floppy on /mnt/floppy:

mount /dev/fd0 -t vfat /mnt/floppy

dd if=/dev/hda3 bs=512 count=1 of=/mnt/floppy/grub.bin


unmount floppy

umount /dev/fd0

I assume /dev/hda3 as your Linux partition (hda1 fat32 EISA config, hda2 XP, hda3 Linux) but YMMV anyway

boot into Windows, copy grub.bin to the root folder C:\

and edit boot.ini

in [operating systems] add

C:\grub.bin="Ubuntu Linux 6.06 LTS"

You probably will have to unset read-only flag from boot.ini in order to save it.

That's it.

---

### Post by Duwi on 2006-09-28
Thanks for the help,
that is what I attempted to do.
But it seems that I failed.
after modifying the boot.ini, I was offered to go to ubuntu (or better the grub loader, so I chose it, .. end of story, nothing happened, just cursor blinking with a black background.

I am really not experienced and everything is pretty new to me, so there is very likely a mistake from my side.

However, I messed it up. I reinstalled Ubuntu and grub is now in the MBR everything seems to work, besides my ThinkVantage button, that now brings me to Grub, not to the system rescue.

I thought about the following.
I don't mind to over and over reinstall Windows. With all those automatics that come with a thinkpad and the exellent support I just have to worry about my data.

So can I, when I feel more comfortable, uninstall grub, reinstall it into the boot think of my ubuntu partition, than copy it to an external medium
afterwards I would reinstall Windows using my rescue disks, than modify boot.ini to provide a link to the ubuntu disk?

Lots of questions, and I really don't have a clue on how to do it all. Just was trying to be logical after reading soooo many internet sides.

thanks a lot,
I guess it was to much for a beginner like me.
But I will keep fighting. hopefully with plenty of support from here.


Maik

---

### Post by Jonie on 2006-09-29
So we're not giving up ;)

I think this will shed some light:

[http://www.thinkwiki.org/wiki/Rescue_and_Recovery](http://www.thinkwiki.org/wiki/Rescue_and_Recovery)

There you are how to boot thinkvantage again with grub.

You can find there:

- how to restore IBM bootloader, but I will personally stick to GRUB.
  then you will have to install GRUB to boot sector of linux partition and make it active, what will still give you a chance to boot IBM recovery through BIOS
- how to add an entry to GRUB to boot ThinkVantage, what is better idea, since  GRUB is already setup, no more fiddling, besides GRUB is fine

---

