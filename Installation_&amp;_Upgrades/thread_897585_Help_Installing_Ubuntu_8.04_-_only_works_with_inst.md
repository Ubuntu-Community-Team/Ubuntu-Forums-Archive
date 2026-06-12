---
title: "Help Installing Ubuntu 8.04 - only works with install cd in drive"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by jrwdunham on 2008-08-22
Here's my problem.  (I'm quite new to this stuff, so bear with me if I trip up the terminology.)  I have downloaded, burned and installed Ubuntu 8.04 Hardy Heron (for 64-bit machines) on a computer with the following specs:

-AMD Athlon(tm) 64x2 Dual Core Processor 4200+
-Two hard drives: (1) PRIMARY IDE MASTER (200 GB), (2) FIRST SATA MASTER (320 GB)
–Memory: 2 GB

***** The problem is that the OS does only boots when the install cd is in the cd drive. *** **

WITHOUT the install cd, GRUB offers me the following options:

```
-Ubuntu 7.10, kernel 2.6.22-14-generic
-Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
-Ubuntu 7.10, memtest86+
-Other operating systems:
-Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda1)
-Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda1)
-Ubuntu 7.10, memtest86+ (on /dev/hda1)
```

When I select the first option (```
Ubuntu 7.10, kernel 2.6.22-14-generic
```), I get ```
file not found
``` and <RETURN> brings me back to the GRUB menu.

When I select the fifth option (```
Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda1)
```), the screen reads ```
kernel alive ...
``` and something appears that looks like the Ubuntu startup screen but it's all distorted.  Then after a while I see a black screen that reads ```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash) Enter 'help' for a list of built-in commands. (initramfs)
```.  This seems like another dead end to me.

It is no surprise to me that these 7.10 OSs don't boot properly, since from within Ubuntu 8.04 (Partition Editor) I have messed around with (i.e., deleted) the partitions on both drives.  And besides, I don't want Gutsy Gibbon, I want Hardy Heron!  I used to have other GRUB options for booting various Windows OSs as well, but those have disappeared - probably as a result of the aforementioned partition-messing-around-with.  But let me stress, I DON'T WANT OR NEED WINDOWS OR ANY OTHER OS AT THE MOMENT - I JUST WANT UBUNTU 8.04 AND NOTHING ELSE, NO DUAL BOOTING.

So...


WITH the install cd in, I get a Ubuntu screen which begins by forcing me to choose a language.  After choosing 'English', I am given the following options beneath the Ubuntu logo:

```
-Try Ubuntu without any change to your computer
-Install Ubuntu
-Check CD for defects
-Test memory
-Boot from first hard disk

```
Let me say that if I choose the fifth option, ```
boot from first hard disk
```, I see a GRUB menu with the following four options:

```
-Ubuntu 8.04, kernel 2.6.24-19-generic
-Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
-Ubuntu 8.04, memtest86+
-Other operating systems:

```
If I select the first option (```
Ubuntu 8.04, kernel 2.6.22-19-generic
```), Ubuntu starts up fine and everything works.  (No, it's not a live session: it doesn't say 'live session' in the top left-hand corner and all the files and settings that I have saved over the last couple days are still there.)  So, basically Ubuntu 8.04 works for me so long as I remember to have the install cd present and select 'English' and then select 'boot from first hard disk'.  This isn't a terrible hassle, but it should be smoother than this, right?

So, I thought maybe if I re-install things will work better.  When I select ```
Install Ubuntu
```, it reads ```
Loading Linux Kernel
```, the Ubuntu logo and progress bar appear and then again I see the black screen with ```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) Enter 'help' for a list of built-in commands. (initramfs)
```.

And even if I try to run the OS as a ```
live session
```, I get the same result as when I select ```
Install Ubuntu
```, as described just above.

So basically I can't reinstall and I can't boot the OS without going through the rigamarole described above.  I have read a bunch of forums, looking for people with similar problems, but so far I haven't been able to solve my own.  

One thing I did do was edit the /boot/grub/menu.lst file from the Terminal after booting Ubuntu in my circuitous way.  I commented out (a) the boot options for Gutsy Gibbon (```
Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
```, ```
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
```, and ```
Ubuntu 7.10, memtest 86+ (on /dev/sdb1)
```) as well as (b) the boot option for Ubuntu 8.04 that I must have installed on the sixth partition of my second hard drive (hd1,5) (```
Ubuntu 8.04.1 (8.04) (on /dev/sdb6)
```).  I know that this had an effect because when I used to have the cd in and select ```
boot from first hard disk
``` I would get 8 boot options instead of the four listed above.  

It seems to me that GRUB is reading the wrong menu.lst file.  I just can't figure out which one its loading.  The OS that I am successfully booting is (I think) on the first partition of the first hard drive (hd0,0) - I conclude this from the fact that the first option in the menu.lst file (the one I select to boot successfully) has the value ```
(hd0,0)
``` for root.  The kernel line has the following value: ```
/boot/vmlinuz-2.6.24-19-generic root=UUID=8e5f2c86-e3a8-4694-be20-151386714596 ro quiet splash
```.  

In blind desperation, I have tried the following: WITHOUT THE INSTALL CD IN THE DRIVE, I wait for the 7 non-functional boot options appear and then I press 'c' to get to the GRUB command line.  I enter the following: ```
root (hd0,0) <Enter>
``` then ```
setup (hd0) <Enter>
``` and I get the following: 
```
	Checking if "/boot/grub/stage1" exists... yes
	Checking if "/boot/grub/stage2" exists... yes
	Checking if "/boot/grub/e2fs_stage1_5" exists... yes
	Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded. succeeded
	Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
	Done.
```

But when I try entering permutations of the kernel value that I read from the menu.lst file, such as ```
kernel /boot/vmlinuz-2.6.24-19-generic <Enter>
``` or ```
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=8e5f2c86-e3a8-4694-be20-151386714596 ro quiet splash
``` or ```
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=8e5f2c86-e3a8-4694-be20-151386714596
```, I get ```
Error 15: File not found
```.

When I enter simply ```
kernel /vmlinuz <Enter>
``` and then ```
boot <Enter>
```, it looks like it's going to boot until it stops at the line ```
[ 610.384148] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
```


In a similar vein, I tried the following.  WITH THE INSTALL CD IN THE DRIVE, I choose 'English', then I select ```
Boot from first hard disk
``` and at the GRUB menu (the one that boots successfully if I choose the first option) I enter 'c' for a command line and, similar to above, I enter ```
root (hd0,0) <Enter>
``` ```
then setup (hd0) <Enter>
``` and I get the following: 
```
	Checking if "/boot/grub/stage1" exists... yes
	Checking if "/boot/grub/stage2" exists... yes
	Checking if "/boot/grub/e2fs_stage1_5" exists... yes
	Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded. succeeded
	Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
	Done.
```
<< note the '16 sectors' this time instead of '17' - what does this mean? >>

But when I try entering ```
kernel /vmlinuz <Enter>
``` and then ```
boot <Enter>
```, it looks like it's going to boot until it stops at the line ```
[ 58.627438] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
```

Similarly, if I try entering ```
kernel /boot/vmlinuz-2.6.24-19-generic <Enter>
``` and then ```
boot <Enter>
```, I get ```
[ 79.507154] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
```

And finally, if I try entering ```
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=8e5f2c86-e3a8-4694-be20-151386714596 <Enter>
``` (or even ```
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=8e5f2c86-e3a8-4694-be20-151386714596 ro quiet splash <Enter>
```) and then ```
boot <Enter>
```, I get another ```
[...] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
``` error.  Note that this time I get 'unknown-block(0,0)'...


I know that I have gone on and on here, but I hope someone can see through the detail to what's really going on and give me some much-needed advice.  I really like Ubuntu (so far everything is working, even the d-link wireless card I just bought!) and would like to see it running smoothly.  

Thanks!

p.s., Don't know if this is relevant, but I originally created the Ubuntu install cd by downloading the .iso file and burning the disk on another computer (a Mac, using Disk Utility) and then installed Ubuntu on my PC.

---

### Post by mattduckman on 2008-08-22
i'm not sure what the issue is, but i do suggest that you try downloading the alternative installer and using that to completely reinstall ubuntu from there. you can get it from the download page ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)) by clicking the check box at the bottom

---

### Post by Mrwasab1 on 2008-08-24
just as an idea, i would remove one hard drive while you install Ubuntu, that way you know where the installation is going.

Seems like the master boot record could be stuffed.

get yourself this little app [http://www.toms.net/rb/](http://www.toms.net/rb/)
put it on a USB stick or floppy disk if you have a drive and boot with that.
Then 
```
dd if=/dev/zero of=/dev/hda bs=512 count=1
```

**Note** that hda will need to be replaced with what ever your hard drive is, so if its your sata drive it will probably be sda.

that should clear the MBR, try to reinstall Ubuntu after that while only having one drive plugged in at a time.

hope that helps

---

