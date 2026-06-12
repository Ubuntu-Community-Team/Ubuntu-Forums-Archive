---
title: "Reinstalling windows 7"
date: 2015-03-25
forum: Installation &amp; Upgrades
---

### Post by louis18 on 2015-03-25
Hi
Well i installed lubuntu, but after having difficulties with certain aspects I am wanting to go back to windows 7. However I deleted the windows partition like an idiot... I have a windows 7 ISO on my harddrive, but i am struggling to run the dvdusb windows tool to mount it there so I can run it during boot. 
Can anyone help me with this problem to get back to windows?
I'm pretty desperate,
Thanks,

---

### Post by yancek on 2015-03-25
How are you able to run the dvdusb tool windows if you deleted windows?  Are you trying to use some Linux tool to boot it?  You won't get Grub or any bootloader to directly boot a windows iso file.  I don't know if windows can do that.  Where is the windows ISO on your hard drive?  Is it on the Ubuntu partition or on a separate partition?  You can extract the windows iso then copy it to a flash drive or a separate partition on a hard drive formatted as ntfs and boot it from Grub on Ubuntu.  This is explained in detail at the link below.  This explains using a flash drive but it works from a hard drive also as long as the partition is in ntfs format.  If you use a hard drive, don't put anything else on the partition.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

I'd read through the entire page before beginning so you have some understanding.  Post back if you have questions.

---

### Post by louis18 on 2015-03-26
Hi,
I was trying to use wine to run the dvdusb tool but to no avail, had some errors when i ran it in terminal. 
I am following that guide but im having a problem opening the iso with disk image mounter and get an error about the file being too large? When i mount it with archive mounter I just have one read me .txt and no other files.
Any help?
Cheers

---

### Post by Mark Phelps on 2015-03-26
If you have Wine working, another Windows USB-creation tool that MIGHT work is RUFUS.  From what I recall (used it long ago), it works without installing, so it may be more forgiving with Wine.

---

### Post by yancek on 2015-03-26
I had the same problem with windows 10 so had to loop mount it.  You need to first navigate to the directory where you have the windows 7 iso file in a terminal.  Then create a directory as a mount point for it.  For example, if you have the iso in your /home/user/Download directory first do this:

```
cd /home/user/Download
```

Then create the directory:

```
mkdir windows7
```

If the iso is not in your /home/user directory, you will need to prefix the command with sudo; sudo mkdir windows7.  Also, you don't need to name it windows7, but whatever you name it make it simple for yourself and don't put any spaces in the name.

Then in the directory run this:

```
sudo mount -o loop windows7.iso windows7
```

You will need to replace "windows7.iso" above with the exact name of the iso and remember that it is case sensitive.  You should then see a number of files and directories/folders for windows and you should be able to proceed to the next step.  This worked for me with windows 10 so I would expect it to work with windows 7?

---

