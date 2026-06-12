---
title: "boot problems + a few other random questions"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by Fragrant Seahorse on 2008-10-11
hey

I'm running 8.04 on a single hard drive with no windows or any other OSes and yesterday my system froze up, I reset and none of the options in grub would allow a boot to complete. 

The latest few kernel options and their recovery modes returned a code 15 error saying that a file couldn't be found without even starting boot. 

Two of the earlier options started a boot in both regular and recovery modes, went through a bunch of text and then terminated with the message "rcS -sulogin main process (4662) terminated with status 127".

I've been searching the archives and forums for hours looking for a way to find a fix to work from the livecd so I don't have to reformat and lose all of my data (150gb or so) that has a bunch of school stuff in it as well.

I've cleared an e2fsck (returned errors which were fixed) made an attempt at the process outlined in this thread:

[http://ubuntuforums.org/showthread.php?t=600644](http://ubuntuforums.org/showthread.php?t=600644)

here are the completed first and second steps, but as you can see the third fails:

ubuntu@ubuntu:~$ sudo mkdir /media/hardy
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/hardy
ubuntu@ubuntu:~$ sudo chroot /media/hardy
/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

I'm pretty confused about what this could mean... Is there something obvious I've missed form the instructions in the thread? 

Does anybody have any ideas about how to make the livecd reinstall the basic elements of the OS that are broken without the risks of a total reinstall? 

However detailed your instructions are I'm sitting here with a pen and paper so please don't hold back.

Thanks in advance!

---

### Post by caljohnsmith on 2008-10-11
It might take a lot of troubleshooting at this point to figure out what the problem is; is it an option for you to mount your Hardy partition, copy all your important files/data to another drive or partition, and just reinstall? Then of course you can copy everything valuable back. It might save you a lot of time in the long run, so is this a possibility?

---

### Post by Fragrant Seahorse on 2008-10-11
It's definitely an option, I'm just unsure about how to go about it.

I have stuff in the documents, images, videos and music folders that I'd like to save.

Is there a way to access all of these things from the live cd? (I'm running it now but the drive just seems like an endless maze of folders and I don't know where to look for my things).

Additionally, is there a way to use the dvd burner while running the livecd? I'm not sure if it's possible to take it out

---

### Post by caljohnsmith on 2008-10-11
It would be helpful if you can post:
```
sudo fdisk -lu
```
Unless you set up a separate partition for your "home" folder when you installed Ubuntu, then if you go to /home/<your username> in the main Ubuntu install partition, that should have most what you want to save. It will probably be helpful to open a file browser as root so you don't run into permissions problems, and then you can just copy/paste from the browser:
```
gksudo nautilus
```
Give that a shot and let me know if you run into problems.

---

### Post by Fragrant Seahorse on 2008-10-11
> **caljohnsmith said:**
> It would be helpful if you can post:
```
sudo fdisk -lu
```



Here is what it returned: 


Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeb87e168

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   576958409   288479173+  83  Linux
/dev/sda2       576958410   586067264     4554427+   5  Extended
/dev/sda5       576958473   586067264     4554396   82  Linux swap / Solaris



> 
Unless you set up a separate partition for your "home" folder when you installed Ubuntu, then if you go to /home/<your username> in the main Ubuntu install partition, that should have most what you want to save. It will probably be helpful to open a file browser as root so you don't run into permissions problems, and then you can just copy/paste from the browser:
```
gksudo nautilus
```
Give that a shot and let me know if you run into problems.

OK I found all of my folders and docs. Will I be able to use my dvd burner here?

---

### Post by caljohnsmith on 2008-10-11
Yes, you could try and burn your files to CD/DVD, but it would be much better if you have another drive (maybe a USB flash drive) where you could copy those files to; sometimes you can run into problems with the CD/DVD burners. But if you want to give them a try, the one that works best for my computer is "k3b", and you can install it with:
```
sudo apt-get install k3b
```
After you install it, it should show up in one of the menus in the "applications" menu on your desktop. If you have any problems with it, you could also try "brasero" or "gnomebaker" (just replace k3b above with brasero or gnomebaker). If you do burn a CD/DVD, I would highly recommend you make sure you can access all your data on it from another computer just to make sure the burn went OK. Let me know how it goes.

---

### Post by Fragrant Seahorse on 2008-10-17
Hi,

Sorry it took me so long to respond. I went through with the reformat and had a bunch of other problems so it has taken this long to get everything sorted out. I just wanted to stop by to say thanks for all of your help!

---

### Post by caljohnsmith on 2008-10-17
You're welcome, and I'm glad to hear you got it sorted out; cheers, and hope you don't run into a similar problem anytime soon. :)

---

