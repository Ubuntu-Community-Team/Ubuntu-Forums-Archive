---
title: "Ubuntu Installion freezes at the beginning"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Aireas on 2008-11-04
my laptop's specs:
Compaq CQ50-215NR Notebook
AMD64 Athlon Dual-Core QL-60
2.00 GB RAM
NVIDIA GeForce 8200M G
Using Ubuntu 8.10

Problem:
   I insert the Ubuntu installation CD and restart the computer. I am able to pick a langauage and then select "Try Ubuntu without any change to your computer". The Ubuntu logo then appears with a progress bar that goes back and fourth for about a minute and then freezes. I have tried several times and it always freezes at the same spot (over the first 2.75 bubbles). 

   I have tried the 32-bit version burned on the laptop at the slowest speed (10x), the 64-bit version burned on my desltop computer at (4x) and the 32-bit version burned from my desktop at (4x). They all freeze up at the exact same point. Has anyone encountered this issue? Thank you for your time! :confused:

---

### Post by Partyboi2 on 2008-11-04
Remove the splash screen to find out where it is freezing. At the main menu press F6 and remove the word Splash, then press enter

---

### Post by Aireas on 2008-11-04
Thank you for responding! I removed the splash and got the following message: 

[   0.520320] EDD information not available.
[   0.936362] VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
[   0.936487] Please append a correct "root=" boot option; here are the available partitions:
[   0.936669] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

---

### Post by b3nzilla on 2008-11-05
My ubuntu installation is also freezing at the beginning.  During installation questions, it's freezing at the location selection, or sometimes even at the previous step.  Is there a way to install without using the gui?

(My laptop is probably 4 years old or so, so it doesn't have amazing specs, but i haven't had any problems installing before).

---

### Post by Aireas on 2008-11-05
I have tried two more times to install without the splash up and both times I got the message:

[End of Trace]

when it froze up. I let it sit for an hour hoping that it was just scanning the memory but nothing happened. What does this mean?

---

### Post by shields on 2008-11-05
My boot disk freezes at various places on install.  Sometimes on the boot.  Sometimes at the desktop.  Sometimes when you click the partition editor.  Sometimes when you click INSTALL.  There's really no rhyme or reason.  I've given it about three days and it's just not working with this machine.  I am going back to 8.04.

---

### Post by Aireas on 2008-11-12
Is there something in the installation command line I can change or add to help the installation process?

---

### Post by SylmarAvenue on 2008-11-12
Same problem, except that after doing what was said earlier, I get this error:

Buffer I/O error on device fd0, logical block 0

It goes into the rundown of different things for install, all with [OK] by them, then it hits some sort of prompt, then it goes into black screen w/ loss of keyboard function, no mouse pointer, etc.

Whatever the hell the developers of 8.10 did, y'all really did a number on our system.

---

### Post by shields on 2008-11-13
I went back to 8.04 and it works fine.  I use Intrepid on my machine at home, but not at the office.

Evidently Intrepid is not ready for prime time when it comes to my office machine.  :(

---

### Post by Partyboi2 on 2008-11-13
> **Aireas said:**
> Thank you for responding! I removed the splash and got the following message: 

[   0.520320] EDD information not available.
[   0.936362] VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
[   0.936487] Please append a correct "root=" boot option; here are the available partitions:
[   0.936669] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
Did you try checking the cd for defects (one of the options at the main menu of the ubuntu live cd) If that passes without any errors maybe try installing using the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/intrepid/").

---

### Post by Partyboi2 on 2008-11-13
> **SylmarAvenue said:**
> Same problem, except that after doing what was said earlier, I get this error:

Buffer I/O error on device fd0, logical block 0

It goes into the rundown of different things for install, all with [OK] by them, then it hits some sort of prompt, then it goes into black screen w/ loss of keyboard function, no mouse pointer, etc.

Whatever the hell the developers of 8.10 did, y'all really did a number on our system.
" Buffer I/O error on device fd0, logical block 0" refers to the floppy. Try disabling the floppy in the bios if you have one, if not then at the main menu screen press F6 and add
this to the end of the line.
```
all_generic_ide irqpoll
```

---

### Post by shields on 2008-11-13
> **Partyboi2 said:**
> Did you try checking the cd for defects (one of the options at the main menu of the ubuntu live cd) If that passes without any errors maybe try installing using the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/intrepid/").

Yeah -- the CD is good.  I used it on another PC, and checked it.  I didn't try the alternate.  8.04 is fine.

---

### Post by Aireas on 2008-11-16
thanks! Using the alternate CD diffently made progress! I was able to install Ubuntu and partition the hardrive using the alternate CD however when I try to boot into Ubuntu, it continues to freeze at the same point in the booting process. I looked at some other threads and some folks that had this problem said that using the latest kernel fixes this, however without Ubuntu installed, I don't know how to update the kernel. I also don't know what the latest linux kernel is. Can anyone point me to the latest kernel as of November 16.

---

### Post by Partyboi2 on 2008-11-16
> **Aireas said:**
> thanks! Using the alternate CD diffently made progress! I was able to install Ubuntu and partition the hardrive using the alternate CD however when I try to boot into Ubuntu, it continues to freeze at the same point in the booting process. I looked at some other threads and some folks that had this problem said that using the latest kernel fixes this, however without Ubuntu installed, I don't know how to update the kernel. I also don't know what the latest linux kernel is. Can anyone point me to the latest kernel as of November 16.

You could see if you can find a ubuntu live cd (gusty, hardy etc)  that you can successfully boot. I had a problem the other day where I needed to use a live cd I use Intrepid but don't have a cd for it so I tried a hardy live cd which would not boot so  I ended up  getting a gusty live cd to boot. If you have success booting a live cd you can try to chroot into your intrepid install and updating it.
From a live cd
Open a terminal (Applications>Accessoires>Terminal)
```
sudo mkdir /media/tmp
``````
sudo mount /dev/sda? /media/tmp
```You will need to know the correct partition to mount and replace ? with the correct number if you do not know what the partition number is you can type in a terminal
```
sudo fdisk -l
```Then look for the correct partition number for linux, if for example yours looked like this (which it wont) 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5671    45552276    7  HPFS/NTFS
/dev/sda2            5741       18746   104470695    f  W95 Ext'd (LBA)
/dev/sda3           18747       19457     5711107+   b  W95 FAT32
[COLOR=Red]/dev/sda4            5672        5740      554242+  83  Linux[/COLOR]
/dev/sda5           18485       18746     2104483+  82  Linux swap / Solaris
```You would replace ? with 4 (sudo mount /dev/sda4  /media/tmp) as this would be the partition that you need to mount
Then chroot 
```
sudo chroot /media/tmp
```then upgrade 
```
apt-get update && apt-get upgrade
```

---

