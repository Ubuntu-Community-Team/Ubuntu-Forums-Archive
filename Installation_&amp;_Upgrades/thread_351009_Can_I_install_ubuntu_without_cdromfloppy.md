---
title: "Can I install ubuntu without cdrom/floppy?"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by djvishnu on 2007-02-01
This is the case: ive got ubutnu running on my laptop, then the cdrom broke, then i did some things i shouldnt have done and i want to reinstall the whole thing, is there any way to install without cdrom or floppy? usbstick?

i have heard roumers about a windows intaller, so maybe i could use my windows (dual boot) to do this?

---

### Post by chriscando on 2007-02-01
Ive never heard of windows being able to help with anything Linux related.

But, I have heard of installing a os over a network. I have never done this before and I think its called a PXEboot. Basically it intails setting up one computer on your network as a server and your other computer will boot with its network card. You might look into this.

---

### Post by dannyboy79 on 2007-02-01
well. couldn't you boot to winxp. then download the iso file. then save the iso on your hard drive so that when you boot to your current ubuntu install you;ll be able to access it. then boot to current ubuntu install. then you can mount the iso file by following this guide. once it is mounted, couldn't you run it???? I am not sure just trying to help you think outloud.

One other thought, what if you download the live cd iso within winxp. then use an iso explorer or extractor within winxp and simply extract the entire iso contents onto your hard drive. then mount your ubuntu install's partition using the fs-driver for winxp. then simply put all the folders and files in their correct place from within winxp and then pray to the heavens that when you try to boot to ubuntu it works. these are some off the wall suggestions but you never know. the network install is the safest way to go though.

or what if you copied the iso to a usb flash device and made it bootable and then simply click on install to hard drive icon after it boots up?


here is a link that explains how to do it. [http://www.howtoforge.com/installing_linux_without_cd_or_dvd](http://www.howtoforge.com/installing_linux_without_cd_or_dvd)

---

### Post by djvishnu on 2007-02-02
Wow, thanks! that guide looked really great, ill try it out.

Another question - Grub uses its own special hd/partition naming/numbering, like **hda partition 1 = (hd0,0)**. Is it possible to tell grub to load from an external disk, for example through usb? (typically /dev/sdc1 or something ln linux)

---

### Post by dannyboy79 on 2007-02-02
yes, it is possible. you need to search this forum and find a thread about booting to an external usb disk. I believe your bios might have to support this or maybe not if you install grub in your booting hard drive in it's master boot record and then just add a line in it for booting the external hard drive. just not sure what grub would call a sdxx (example: sda1) drive but I am sure this has been done.

actually i found this thread for ya, check it out  [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)
it's for installing Brezzy but it should be any different than Dapper or Edgy or Fiesty. good luck. once you figure this out, please post back so I know how to do it as well as I am thinking of doing this.

---

### Post by djvishnu on 2007-02-02
After skimming through that thread I understand that it's about booting from and ext usb drive. (right?)

I actually dont need that, ive already got grub in mbr on my first harddrive - like you said, my problem is **what would grub call my usb drive?** I have no idea. :confused: 

grub is weird

---

### Post by dannyboy79 on 2007-02-02
the answer is there, I just read thru it again. according to the tut, it states that grub refers to hard drivers no matter if they are hda or sda as (hx,x) where the first x is the driver (your very first ide channel and the master drive on that channel) and the second x is the partition. To help you understand what I am talking about, his comment is, "BACKGROUND: I have an internal hard drive (western digital) already in my system with Windows XP Pro installed (which shows up initially as drive HDA in the UBUNTU partitioning phase of the install). My external USB drive is a Seagate 40GB Portable External Hard Drive that was purchased at Walmart for around $120" 

See I don't know what you are trying to do because you specifically asked me above, "Is it possible to tell grub to load from an external disk, for example through usb?" and I answered your question. Then I found a better way, you tell me you have ubuntu installed already, can you get to the internet thru that ubuntu install???? if you can, than download a new .iso of the os you want. then follow this thread [http://www.howtoforge.com/installing_linux_without_cd_or_dvd](http://www.howtoforge.com/installing_linux_without_cd_or_dvd)
which will start the installer from the .iso you downloaded onto your computer. 

you can always do trial and error can't you???

why don't you just try to add your own grub entry and see what happens, the worst that'll happen is that grub will tell you it can't boot to that partition, i think that's error 15 or 17. not sure. the bottom line is that you have to install ubuntu ONTO that usb drive first. i have pasted that above, then you can play around with grub.

---

### Post by djvishnu on 2007-02-12
I've got the iso image running from a partition on my harddrive, but now ive got another problem:

The installer says "cant mount cdrom, do you want to try again?"

Is there some way i can tell the installer to use /dev/sda9 instead of my cdrom drive?

---

### Post by dannyboy79 on 2007-02-12
i don't understand the error? did you do what it said?
mount -t iso9660 -o ro,loop=/dev/loop0 cdimage /mnt/cdrom

if you mounted the iso then the iso contents should be all within the location that you mounted it? next you were suppose to copy everything from the iso onto a newly create partition.  did you do that? just please follow the tut, I have not done it myself but someone has and it has worked for them so it must work.  did you reboot and use Grub, sourced from any other Linux, to boot up the kernal and initrd files of this temporary directory, thereby either activate its installer if it has one or it should have started up and look just like a live cd. then you should be able to click on the install button and install it where ever you want.

---

### Post by djvishnu on 2007-02-12
Thanks for quick replies!

Yes i have done that, copied all the files to /dev/sda9. I am using the text install of ubutnu. I got the kernel and the installer running, but after selecting language and keyboard it complaints that it cant mount the cdrom. 

I figured i'd try myself, so i ctrl-alt-f2'd to a busybox shell and tried to mount /dev/sda9 to /cdrom myself, but then i got this error: (not word by word, didnt write it down)

# mount /dev/sda9 /cdrom
mount: cannot mount device. Invalid argument

I dont even know if this is the smart way to do this - i thought maybe there was some kernel argument i could use to redirect cdrom rom /dev/sda9.

Do you understand what im trying to say?

---

### Post by dannyboy79 on 2007-02-12
no I am sorry I don't understand this as I have never done it. i know when I installed ubuntu it never asked me about mounting a cd-rom? why would the installer have to mount a cd-rom? are you sure that you are BOOTING the new partition /dev/sda1? the install should simply ask you where to install the os, nothing abot mounting a cd-rom? I am sorry that I can't help since I have never done this, I only read it and it sounded like it would work since that guy actually used that method for 12 different os's. i don;t know what else to tell ya.

---

### Post by djvishnu on 2007-02-13
:)

Yes i am booting the installation cd:

This is the grub config that launches it:

title Ubuntu Alternative Install
root (hd0,8)
kernel /install/vmlinuz ramdisk_size=16384 root=/dev/ram rw
initrd=/install/initrd.gz

(i found this from the isolinux.cfg file on the livecd)

I have copied all the files from the image i downloaded to /dev/sda9 (hd0,8). It starts up installer and everything looks fine, but it seems to want to copy the files needed from the cdrom drive. 

This is my theory: Grub loads the kernel (with the installer) into memory and executes. When the kernel is running by itself it never mounts /dev/sda9 (where the cd-files are). The first thing that happens in the setup process is choosing language, choosing keyboard, then it loads some drivers (ide, floppy, cdrom with others) and then it says "failed to mount cdrom, would you like to try again?" 

When i am in the installer i can ctrl-alt-F2 into a busybox-shell, where i can see that /dev/sda9 isnt mounted anywhere. However, in the setup process, it IS possible to skip the mount-cdrom-step, so if i just could mount /dev/sda9 on /cdrom manually i guess i could get the process running again.

---

### Post by dannyboy79 on 2007-02-13
why are you booting to a live cd???? you're suppose to be booting from the initrd.gz
 or whatever it is that you copied from the mounted iso file and put it into the /dev/sda9 partition or whatever. I have a feeling that you are not following the instructions correctly. you told me that you already had an installation of ubuntu done did you not? if you can see that /dev/sda9 isn't mounted anywhere than you are clearly NOT using /dev/sda9 initrd.gz are you? also this line doesn't look correct either: kernel /install/vmlinuz ramdisk_size=16384 root=/dev/ram rw

notice how the one in the tut is loading root NOT from /dev/ram but looks like this:
title Arch Install
  root (hd0,8) 
  kernel /isolinux/vmlinuz load_ramdisk=1 prompt_ramdisk=0 root=/dev/rd/0  
  initrd=/isolinux/initrd.img 

so I am not sure what else to tell ya but it just doesn't appear as though you are doing everything correctly. are you sure that sda is hd0? 

actualyl I just found this by googling. it states:
8)Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

9)Type the below commands in terminal 2

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected.

The install should be working now on your PC

You can refer this from here


here is the link to the entire thing. [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)
 good luck

---

### Post by djvishnu on 2007-02-15
Actually - i found a much simpler solution!

Instead of using one of the ubuntu cd install images and copying/launching from the new partition, i downloaded the ubuntu minimal install image (8mb), copied the contents to the new partition and fired it up through grub. No need for mounting anything at all for the install, the whole thing was loaded into memory.

AND i found out how to use usb drives with grub! Just use the grub command line, write "geometry (hd" and press tab, it autosuggests the available disks.

---

### Post by dannyboy79 on 2007-02-15
well I am glad you got it working but I wish you would have tried the last solution I gave you as I would have liked to write up a how-to with the added tip about mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0. anyway, have a good one.

---

### Post by djvishnu on 2007-02-16
Actually I tried that, this is what i found out when I was in the setup program and CTRL-ALT-F2 out to a shell (busybox):


- the / root file system was a ramdisk, and /dev/sda9 where i had my files were not mounted anywhere. (setup thought i was using a cdrom and tried to mount /cdrom)
- My partitions were detected correctly as /dev/sdaX
- I was unable to mount /dev/sda9 to /cdrom manually - i do not know why. Actually i couldnt mount any ext2/ext3 filesystem to anywhere.
- I was able to mount vfat filsystems!
- I tried to put put the .ISO on a vfat system, mount the system and then mount the image on /cdrom - but it complained the loopback interface did not exist.
- I tried your tip, but it failed since /dev/loop0 didn't exist in the first place.

if you want to test this out yourself, its really easy to format a usbstick to ext2, copy all the files from the cdimage to it, look in /isolinux/isolinux.cfg to find out what kernelr and what parameters to use - then add an entry to grub's menu.1st. to find out what grub calls your usbstick, just run "sudo grub" and use the geometry command i talked about.

---

### Post by dannyboy79 on 2007-02-16
you were suppose to mount sda9 to cdrom. when the system failed and wanted to know where to find the iso, you were suppose to do this:
8)Next run through the installation until it fails to find the .iso file. Then change to terminal 2 with (Ctrl-Alt-F2). Hit enter to activate this console.

9)Type the below commands in terminal 2

mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

10) Change back to terminal 1 (Ctrl-Alt-F1), scan again and the ISO will be detected

your comment " I tried your tip, but it failed since /dev/loop0 didn't exist in the first place." I am guessing again that this is because you were using a live cd iso. It stated that at the top of the link I provided in post #13. None the less, I'll give this a try to validate the how-to that was written. It's the link I provided in post 13. Glad you're good to go.

---

### Post by djvishnu on 2007-02-16
Hm. i think we are talking past eachother :confused: .

If you boot up the installations cd and ctrl-alt-f2 to the console (when the cd mount failes) does *not* exist - so "ln /dev/loop0 /dev/loop/0" cannot be done.-

Im not sure what you define a live cd as - but i have been using the "alternative" ubuntu installation cd - which does not boot into X, just text-gui-mode.

---

### Post by dannyboy79 on 2007-02-16
This guy just wrote it Jan 21, 2007. Are you saying that he would spend all this time to write up a how-to that didn't work? ALso these people are just making stuff up as well??
 [http://www.ubuntuforums.org/showthread.php?t=298719&page=3](http://www.ubuntuforums.org/showthread.php?t=298719&page=3)

 I can't comment other than what it states as well as what you have stated to me. You descibed stuff that didn't sound correct to what the instructions said that is all I was saying along with the fact that this was just done less than a month ago with Ubuntu Edgy Eft.

here it is once again:
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

I will try it soon and let you know, maybe it doesn't work for all hardware??? The point is that you got ubuntu installed. glad you're a user now!

---

