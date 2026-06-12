---
title: "Installing on external HD"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by nibiru8722 on 2011-01-02
So, here's the deal.
I have a 1.5 TB USB hard drive that I want to install Ubuntu on. I don't want to install Ubuntu on my internal because my internal doesn't have enough room to install it next to Windows and I have too many programs on Windows that I don't know if I could replace on Ubuntu.

My friend has been trying to help me with this but isn't making any sense. I use Ubuntu on my netbook and love it, and would love to put it on my external HD to use on my desktop as well.
Is there any simple, foolproof way to do this?

---

### Post by lithopsian on 2011-01-02
Should be fairly straightforward, but I'm guessing it has trouble seeing your external drive early enough to boot from it?  How far have you got?  Installed?  Not even installed?

If you are scared to even start, then the basic steps should be straightforward.  Run the installer from your CD or similar.  Point at the external drive.  Create or point at the partition to use, and let it go.  Fingers crossed it will create an initramfs with the drivers to mount your external drive and boot from it.

You might have to fiddle with Grub afterwards but fingers crossed it usually gets it right even for dual boot.

---

### Post by nibiru8722 on 2011-01-02
> **lithopsian said:**
> Should be fairly straightforward, but I'm guessing it has trouble seeing your external drive early enough to boot from it?  How far have you got?  Installed?  Not even installed?

If you are scared to even start, then the basic steps should be straightforward.  Run the installer from your CD or similar.  Point at the external drive.  Create or point at the partition to use, and let it go.  Fingers crossed it will create an initramfs with the drivers to mount your external drive and boot from it.

You might have to fiddle with Grub afterwards but fingers crossed it usually gets it right even for dual boot.

Wait, none of that made sense to me.
No, I haven't started yet, because yes, I'm a tad scared to do so.

---

### Post by kansasnoob on 2011-01-02
You may find this helpful:

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If it confuses you at all let us know.

---

### Post by C.S.Cameron on 2011-01-03
Following to install 10.10 to external USB.
Adjust partition size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "NTFS file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by nibiru8722 on 2011-01-03
> **C.S.Cameron said:**
> Following to install 10.10 to external USB.
Adjust partition size to suit:


Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.




And see, that's the part I'm afraid of. I don't wanna do anything with the internals of the PC cuz with my luck I'd break it. But I also am afraid I'll overwrite Windows if I don't.

---

### Post by nibiru8722 on 2011-01-03
> **kansasnoob said:**
> You may find this helpful:

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If it confuses you at all let us know.


Alright, this guide helped a LOT.
Going to use the "Try Ubuntu" thing tomorrow, make sure it goes alright with my computer as far as hardware specs, etc.
Then on Wednesday, I'm going to attempt this.
If anyone has any more suggestions/tips, I'd appreciate it greatly.

---

### Post by nibiru8722 on 2011-01-04
A few last things -- my friend said that for an external HD I don't need any swap space since it's on an external.

Also can I install it using my netbook and still have it work on my desktop?

---

### Post by nibiru8722 on 2011-01-04
Well, I installed it. Everything seemed to go well, but the drive doesn't seem bootable and Windows won't even recognize it as storage anymore. So now I've got a dead drive and no Ubuntu.

---

### Post by cipherboy_loc on 2011-01-04
> **nibiru8722 said:**
>  but the drive doesn't seem bootable and Windows won't even recognize it as storage anymore

Okay, so boot from the LiveCD again, and run the boot info script that  is in my signature. Post the contents of the README file in CODE tags.

Also, if you selected the whole thing to be used for Ubuntu, all your documents would have been deleted and the external hard drive would have been formatted to a format that Windows cannot read.

Cipherboy

---

