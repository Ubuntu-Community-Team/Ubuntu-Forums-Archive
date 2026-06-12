---
title: "Grub not loading with dual boot"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by snoops on 2006-06-01
Hi,

I downloaded the ubuntu 6.06 desktop amd64 edition, then proceeded to install. 

My main windows drive is a sataII drive with 133GB of unpartitioned space. Windows is on the other 100GB. 

I went through the graphical installer, and created three partitions - a 2GB swap partition, 130GB root partition, and a 800MB /boot partition. 

Then I was asked to specify mount points - all my drives were detected - yay!
So I specified the three partitions I just created, then clicked next - now I was presented with a summary of the install. I clicked install. 

It said it was copying files, unpacking files etc..Then it said it was installing grub, then said grub was scanning for hdd's with bootable partitions. 

After that I was told the install was complete and that I needed to restart!

So I clicked restart now, took the cd out. The machine reboots, and xp loads. 
No grub. I thought I just missed the boot loader screen..but it doesn't seem so :( I tried rebooting again to double check, and sure enough, there was no boot loader to be seen - xp would load straight away.

I spoke in the freenode irc channel..and another user told me he had the same problem and didn't know how to resolve it. So here I am trying to work out the issue.

Thanks!

---

### Post by sanderjd on 2006-06-01
Same problem, posted about 45 seconds ago. Also using SATA, maybe this has something to do with it? Another thing I thought of is that I also have a drive on ide, is Grub being installed in the MBR on this drive instead?

---

### Post by snoops on 2006-06-01
I also have an IDE drive connected, so fingers crossed it didn't install grub into the mbr of that drive.

---

### Post by sanderjd on 2006-06-01
I bet this is exactly what happened. I am going to try re-installing grub manually.

---

### Post by zXen on 2006-06-01
Same thing just happened to me...This happened on a few occasions on the earlier Ubuntu versions and I managed to fix them by going into the installation setup and changing the bootflags.
 Could someone show me where you can edit the bootflags after installation?

---

### Post by snoops on 2006-06-01
I might try installing it without the IDE drive connected - see if that changes anything. Some more insight on the issue would be great - if anyone can lend a hand I'd much appreciate it :)

Oh and tell me how you go with your install sanderjd.

Thanks

---

### Post by sanderjd on 2006-06-01
well, one solution that worked for me, is changing my boot order. I am now booting off of the drive that doesn't actually have any OS on it. Its silly, but it works.

---

### Post by snoops on 2006-06-01
Oh, wow.. So it really did install itself into the mbr of the IDE drive?

---

### Post by zXen on 2006-06-01
So, is there any way to change the bootflags within Ubuntu like in the previous versions?

---

### Post by ozroy on 2006-06-01
I had a problem with the desktop CD and installing from there. Everything installed fine until it got to grub and then it crashed failing to install grub.

Upon investigating everything was installed fine except grub. Using update-grub, or grub-install resulted in errors that I think is related to my SATA drive. It's a brand new system that only has a SATA drive. With much screwing around I was able to install grub manually and now everything works fine.

---

### Post by catlett on 2006-06-01
Just a quick note to snoops. Your wasting space. /boot only needs to be 50mb (or even less, grub fits on a floppy) Root will not exceed 5gb, if you wanted to go overboard do 10gb but 130 is wasted space. 2gb swap is wasted  space as well. Most ubuntu users don't even go into their swap. Only people who do video editing and stuff of that nature need a big swap file. The rule of thumb is twice your ram. Even then you don't need more than 1gb (I run 512mb and never touched it)
You should partition like so
/boot 50mb
swap 1gb
/ (root) 10 gb
/home "whatever is left"gb

Home is where all your documents,mp3s, downloads etc will go. Root is just the base install and whatever programs you might install after.


P.S. For anyone else wondering. If you have limited space on your hard drive you can install with less. /boot (you don't necessarily need a boot) but if you want one keep it 50mb or less. swap 512mb, / (root) 5gb is enough, you can get away with 3gb. home is the balance. Home is important because linux will let you reinstall and format root and boot but leave home alone. So you can upgrade without loosing your personal data.

---

### Post by snoops on 2006-06-02
Thanks..I was just trying to give as much detail on the problem - because not even being able to boot ubuntu is a problem :D

I've got 2GB of ram, and I did know about the twice your ram rule of thumb, but I thought over 2GB was massive overkill - I do however do quite a bit of video editing the like, so I thought it couldn't hurt. I probably should have a seperate home partition actually - next time I get around to installing (once this problem is fixed) I'll create a partition for home, and as you say 10 or so GB for /.

---

### Post by mattchambers on 2006-06-02
I had this problem with Ubuntu 5.10 and again with 6.06 release. I eventually gave up before but I am really wanting to get GRUB working this time around as I love Ubuntu.

Like most others in this thread I have Windows installed on a SATA drive but I have an IDE drive connected that is hda while my SATA drives appears as hds1 or something I am not sure when looking at drive information on the live CD of Ubuntu. The installer makes no mention of Windows when letting the wizard do everything, I am not sure if it should mention that it detected Windows or not.

Any information on editing the GRUB settings or moving the boot partition or whatever needs to be done would be helpful.

EDIT: I tried sanderjd's fix "well, one solution that worked for me, is changing my boot order. I am now booting off of the drive that doesn't actually have any OS on it. Its silly, but it works." It worked for me too. So yes, GRUB's boot was installed to my IDE drive with no OS's on it simply because it is the first drive. I assume this is a default behavior of GRUB or the Ubuntu install script.

---

### Post by catlett on 2006-06-02
Grub overwrites the mbr. So it wants to be at the head of the drive. It doesn't care what else is on the drive. All grub does is pass you along to the partition your install is on.
It appears there is a bug in the grub installation. If you are lucky enough to have a spare drive that is ide it looks like a solution is to make that the master and grub will write to the front of the disk in the mbr range i.e. first sector of the master drive   and boot you to your sata drive.
My advice...Use the text install cd. Get away from the live cd installer. It has zero options doesn't let you review grubs os detection or determine where it is going to go. 
Follow the dual booting link in my signature to hermans site and you will get a graphic of the text mode install. When you run this installer it will tell you if grub detects windows or other os's but MORE IMPORTANTLY it will allow grub to install to a floppy. Since there appears to be an issue with ubuntu's grub and sata drives, install grub to a floppy and then you will be able to boot to your install with the floppy.
Once you get a workable floppy and can access your drive then you install grub to your hard drive. This way if grub still doesn't work from the hard drive, you have the floppy. To install grub open the terminal and enter ```
grub-install /dev/hda
``` THAT IS FOR IDE, sorry I don't know sata. Google or you may already know what sata drives are seen as in linux (I guess you could run fdisk -l to get a listing) Here's grubs link about installing from the command line just in case  [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall)

---

### Post by snoops on 2006-06-02
I'm going to try this in an hour - rip out my IDE drive, try it with just the sata, and see what happens. Fingers crossed. I remember my XP installation had the same problem - I had a sata and a ide connected..I installed XP on the sata, but it wrote the boot manager to the IDE. 

I had to rip out the IDE and install XP again on the sata for the boot manager to stay on the SATA.

Thanks guys.

---

### Post by ozroy on 2006-06-02
I only have SATA drives and had to install grub manually. Here is a really quick rundown of how I did it.

1) Boot into the desktop version of Dapper. Using the rescue mode on the text installs proved to be a hassle due to some terminal issues.
2) start an xterm and mount the root partition of your new install onto the media/ directory
3) bind the dev folder to the /media/dev folder using *mount -o bind /dev /media/dev*
4) chroot to your new install using *chroot /media*
5) copy the grub stage files from /lib/grub/i386-pc/ to /boot/grub
6) Now start the grub shell by typing *grub*
7) Install grub to the MBR
  7.1) Find out which device has your root partition by typing *find /boot/grub/stage1*
  7.2) type *root (hd0,4)* but replace (hd0,4) with the device found in the previous command.
  7.3) type *setup (hd0)* to install to the MBR
8 ) Now make sure your grub menu.lst file is configured properly and you should be able to boot into your new install.

---

### Post by zXen on 2006-06-02
Is there no way to change the bootflags like in the older Ubuntu versions?

---

