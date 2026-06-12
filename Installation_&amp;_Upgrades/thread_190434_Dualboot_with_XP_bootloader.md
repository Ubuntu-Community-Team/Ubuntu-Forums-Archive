---
title: "Dualboot with XP bootloader"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Tuntis on 2006-06-06
Alright.

So, I'd like to install Ubuntu BUT I want to boot it using the Windows Bootloader. Do NOT ask. (Well, mainly due to Norton Ghost 2003.)

I can install Ubuntu just fine, but the actual questions are:

1) How would I do a dualboot with the Windows bootloader?

2) How do I get BACK the Windows XP bootloader for now:

The problem with recovering the bootloader is:

1) Windows 98 bootdisks can't recover it (fdisk /mbr)
2) Update CD DOES NOT HAVE THE RECOVERY CONSOLE (it's not bootable)
3) I can not install the recovery console for 2 reasons:
 3.1) My XP CD is an original version WITHOUT SP2, what I have installed
 3.2) It won't let me install as the Windows bootloader isn't in place.
4) I have no floppy drive.

---

### Post by Zalbor on 2006-06-06
The only way I know to do that would include installing GRUB then using the XP recovery console to overwrite it. If you don't have this it can't be done as far as I know.
Hopefully someone will know better, but try to find a CD with the recovery console.

---

### Post by six on 2006-07-03
I'm hoping to do a detailed "how-to" in the next few days, as I wanted to do exactly the same thing.

For now, as a quickie :D if you have Ghost 2003, you can use the rescue floppies to reset your MBR so you can boot back into Windows. The command is:

gdisk 1 /mbr

I have Ubuntu, Kubuntu, Edubuntu, Xubuntu, Fedora Core 5, openSUSE and Mandriva installed (so far). You install each one in turn, accepting the default of installing Grub each time in the MBR. After you've updated the Kernel, you need to trim the /boot/grub/menu.lst file down (just keep the latest Kernal & recovery options).

Then you'll need to (re)install Grub to the current distro's partition. Do a df, mount or sudo fdisk -l if you're not sure of it. Then issue the command:

sudo grub-install /dev/hda6

(if hda6 is where your distro resides). Then do a:

sudo dd if=/dev/hda6 of=/home/{user}/Desktop/ubuntu.lnx bs=512 count=1

which will generate a file on your desktop. Copy this to a common (FAT32) partition, or USB stick. Reboot with your Ghost rescue floppies, and issue the GDISK 1 /mbr command to remove [the default] Grub install. Reboot again, and you should go back into Windows. Copy the ubuntu.lnx file into C:\ then open a DOS prompt. Issue the commands:

attrib -h -s -r boot.ini
notepad boot.ini

and add the line

c:\ubuntu.lnx="Ubuntu Linux"

at the bottom, then save it. It's probably a good idea to hide the boot.ini file again with:

attrib +h +s +r boot.ini

Restart Windows, and you should be presented with the NTLDR's multi-boot option screen, which is completely independent of Grub. Use the cursors to select an OS, and check you can boot in and out of both.

You don't need the Windows rescue utilities at any time - but you do need to have Ghost's GDISK.EXE utility. (Maybe an old Win98 rescue floppy with FDISK /MBR might work, but I can't verify it).

I have a custom rescue mini-CDR with Ghost 2003 and Partition Magic on it. It's got me out of trouble many a time. :D 

I'll post a link to my more detailed how-to in a few days, after I've written it...

EDIT: here's the link to my HOWTO thread...

[http://www.ubuntuforums.org/showthread.php?t=208951]("http://www.ubuntuforums.org/showthread.php?t=208951")

---

