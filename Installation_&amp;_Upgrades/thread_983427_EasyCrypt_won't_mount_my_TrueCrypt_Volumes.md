---
title: "EasyCrypt won't mount my TrueCrypt Volumes"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Elliander on 2008-11-15
I am trying to Mount a TrueCrypt Volume in Ubuntu (latest version updated) and I installed:

truecrypt-6.1-setup-ubuntu-x64

Which was downloaded from the TrueCrypt downloads page. I also have EasyCrypt installed from the Synaptic Package Manager.

When I click "Open a Crypt" it gives me the ability to browse and select the file, which I have stored on an external drive, I am then told to type in my Administration Password, then I am given a prompt to enter the password for the file.

The files were previously created under Windows XP, they have FAT32, and both have hidden volumes. So there would be two passwords I can use.

Neither password opens it.

I think the problem might be that the mount path keeps saying /media/

When it isn't top level. But I don't want to move the files there. And it won't accept me typing it manually where the files are located.

I also am wary that it isn't giving me any of the options I would see under windows. Such as write protecting a hidden volume. etc.

I would just like for Ubuntu to be able to Mount these Volumes that work just fine in windows with all the options I have under windows. One would think that since both Ubuntu and TrueCrypt are open source this would be possible but I can't find any other programs to let me mount my volumes.

---

### Post by Elliander on 2008-11-15
Well this complicates things...

When I click "about" in Easy Crypt, it says that True Crypt is not installed. But when I click again to install True Crypt it says it is installed. But I can't find a way to run just the True Crypt.

---

### Post by Elliander on 2008-11-15
I also tried GDecrypt

I am able to select the file to mount, but "Mountpoint" is just a drop down of existing Drives. It gives me no option to create a new drive letter to use, and if I choose any of the drives listed it says:


Mountpoint /media/WD Passport is not empty!
Mountpoint /root is not empty!
Mountpoint /media is not empty!

So I am really stuck. Nothing seems to work and I just want to be able to Mount a single file.

---

### Post by Elliander on 2008-11-16
Well this is incredibly annoying...

I figured out how to set it to mount, but first it can't read the file because It can't see spaces in file names. Now because the Partition Name for the USB Hard Drive has two names it can't read it.

Is there any way to get either of these programs to work with my existing file structure, or do I need to rename everything to conform? And how do I rename the hard drive?

---

### Post by Elliander on 2008-11-16
Since I could not figure out how to change the partition name in Ubuntu, I switched to Windows where I can just right-click, properties, rename label. I then rebooted, back into Ubuntu, and tried again.

When there were no spaces in any of the files leading to the TrueCrypt Files, I was able to Mount as a Disk Image using GDeCrypt. I was then able to view the files just fine.

However, I still can't seem to get Easy Crypt to work and I would like to.

Also, it unsettles me to think I needed to use Windows to get it to work right in Ubuntu. How can I make a switch from windows if I will always need windows to fix every little problem?

I tried using Wine to run the windows version of TrueCrypt, but Wine apparently doesn't support it.

Shouldn't Ubuntu be able to read and write without error in partitions that uses spaces in the name? Shouldn't Ubuntu be able to as easily as windows change the name of partition labels?

I'd write that much as feedback, but can't seem to find a place to suggest anything.

I would still like it if someone can at least point me in the right direction on how to do even half the things I seem to need windows for.

I want to make a full switch from windows but I just can't do it as long as I seem to need windows for the simplest of tasks.

---

### Post by Elliander on 2008-11-16
Ugh. Just when I think I have it figured out, I can't unmount it.
[B]

Unable to unmount truecrypt1[/B]

umount: /media/truecrypt1 is not in the fstab (and you are not root)


And now I notice that if I was logged into windows and it crashes (which happens allot) on next boot I have no access at all to any of the partitions that windows would use unless I log back into windows then log off and hope it doesn't crash. Ugh.:mad:

---

### Post by celavi on 2008-11-27
seems like easy crypt doesn't like the latest version of truecrypt. i had the same issues. works fine with truecrypt 5.1a from the website.

---

### Post by nnn= on 2010-12-18
*

---

### Post by AbdRahim on 2011-03-01
I cannot unmount truecrypt crypts with Easycrypt in Ubuntu 10.10 either. I have to open Nautilus as root and unmount it through Nautilus, which gives an error, but unmounts it. Also opennining it tells me I have an invalid password but mounts it anyway. Seems buggy somewhere. Can't afford to loose files.

---

