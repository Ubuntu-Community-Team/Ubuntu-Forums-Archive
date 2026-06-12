---
title: "problem installing UBUNTU server 11.10 32bit"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by ganewbie on 2012-02-23
I got couple of error message as attached pictures. now cannot reboot.
Can somebody give me detailed instruction to fix this problem, please note that this is the first attempt to run my own server. I need to install the Kernel manually.

---

### Post by MAFoElffen on 2012-02-23
> **ganewbie said:**
> I got couple of error message as attached pictures. now cannot reboot.
Can somebody give me detailed instruction to fix this problem, please note that this is the first attempt to run my own server. I need to install the Kernel manually.
I will try to help ypu.  Sort of an Ambiguous Error... without more background info.

What hardware are you installing on?  Motherboard or make/model, Processor(s), RAM, Video, Drives. Drive controllers.

Did you set up and RAID Storage? If so, was it firnware, software or hardware RAID?

Did you try to reinstall -- where it got the same repeated error?  

Where in the Install process did it get those errors?

---

### Post by ganewbie on 2012-02-23
-I am installing it on an old Dell GX280. not sure about the configuration but it is likely 1gb memory and CPU Pentium 4. 
-I did not setup RAID storage.
-I did and got the same error.
-Not sure where in the install or how to describe it.

---

### Post by MAFoElffen on 2012-02-24
> **ganewbie said:**
> -I am installing it on an old Dell GX280. not sure about the configuration but it is likely 1gb memory and CPU Pentium 4. 
-I did not setup RAID storage.
-I did and got the same error.
-Not sure where in the install or how to describe it.
Okay, I'm looking at that computer's specs. Depending on the case style, you can have up to two drives. The mother board maxes out at 1MB RAM, 

The Ethernet NIC??? It is cryptic:
```

Integrated network interface with ASF 1.03 support as defined by DMTF.   Capable of 10/100/1000 

```
Doesn't tell me what brand, model or chipset.  Some are installed normally in an install and some require non-free firmware... 

The board chipset is an Intel Grantsdale chipset. The video, some came with an onboard Intel GPU, whereas some came with an optional Video card that it doesn't say what that was.

I'm assuming that you have access to the internet from another PC.

What version of Server are you installing?  Via CD?

Does the CD pass a md3sum? At the first menu, does it pass the disk test (to check the CD file integrity)? 

I know you are installing server, but to try to do some testing on this box... Does it run the desktop of the LiveCD? If so, please post the results of
```

lspci

```
I know you are tired of installing and it will most likely stop at the same point as the other 2 times, but...

Server installs in virtual terminal tty1, the system messages are displayed in tty4. So when you get locked up in tty1, press <Cntrl><Alt><F4> and it will take you to tty4. If you press <Shift><Page up> you can scroll up a page at a time. <Shift><Page Down> scrolls down. Copy down any system error messages that you think are pertinent. Then Press <Cntrl><Alt><F1> to get back. 

If it doesn't let you get back to the Install Step Menu where you can stop and exit the install, then Press <Cntrl><Alt><F2>, then 
```

shutdown -P now

```
will shut everything down cleanly.

---

### Post by ganewbie on 2012-02-24
Thanks for the reply, I have the GX280 small desktop chassis.
The same PC used to run Ubuntu desktop 11.4
"Does the CD pass a md3sum? At the first menu, does it pass the disk test (to check the CD file integrity)?"
Sorry I do not know how to check this for you. Or not sure how to answer.

"Server installs in virtual terminal tty1, the system messages are  displayed in tty4. So when you get locked up in tty1, press  <Cntrl><Alt><F4> and it will take you to tty4. If you  press <Shift><Page up> you can scroll up a page at a time.  <Shift><Page Down> scrolls down. Copy down any system error  messages that you think are pertinent. Then Press  <Cntrl><Alt><F1> to get back. 

If it doesn't let you get back to the Install Step Menu where you can  stop and exit the install, then Press  <Cntrl><Alt><F2>, then"
It looks like you want me to re-install again, I can do that but I get back home tonight, in 10 hours.

Thanks for the great help.

---

### Post by MAFoElffen on 2012-02-24
> **ganewbie said:**
> Thanks for the reply, I have the GX280 small desktop chassis.
The same PC used to run Ubuntu desktop 11.4
"Does the CD pass a md5sum?"

It looks like you want me to re-install again, I can do that but I get back home tonight, in 10 hours.

From a terminal session, change directory to where your downloaded ISO is and
```
[FONT=monospace]
[/FONT]md5sum ubuntu-11.10-server-i386.iso

```It will calculate the md5 checksum of your download ISO file.  Compare that to this:
> [FONT=monospace]
[/FONT]881d188cb1ca5fb18e3d9132275dceda *ubuntu-11.10-server-i386.iso
Also- did you burn that disk at the lowest speed? (Hint) I volunteer at a computer recycler.  Testing drives- you'll be surprised at how many don't pass our tests.  Things might be fine burning and reading to the same drive... but are a different story going from one drive to another.  Burning at a low speed really does make up for some of those differences.

Yes, reinstall and get those system error messages.  Some more messages may be in the system log... if you jumped to tty2 (instructions in previous post) and did
```

tail /var/log/system.log

```It would display the end of the syslog.

I guess an explanation would be if we found what it was doing to to lead up to that error, what that error entailed, then we could try to address that.

If it ran 11.04 desktop, then it should run 11.10, whether Desktop Or Server. I've installed Server on boxes that wouldn't run Desktop.  Less Overhead and Text-Based.  ::curious::

---

### Post by darkod on 2012-02-24
> **ganewbie said:**
> -I am installing it on an old Dell GX280. not sure about the configuration but it is likely 1gb memory and CPU Pentium 4. 
-I did not setup RAID storage.
-I did and got the same error.
-Not sure where in the install or how to describe it.

/dev/mapper/... IS a raid device. But that shouldn't stop ubuntu server installing grub and the kernel successfully.

Make sure you know what you are installing onto. If you don't want to use raid, you obviously have one. That could be the reason it fails also, although the server version is usually very good with raid.

---

### Post by MAFoElffen on 2012-02-25
> **darkod said:**
> /dev/mapper/... IS a raid device. But that shouldn't stop ubuntu server installing grub and the kernel successfully.

Make sure you know what you are installing onto. If you don't want to use raid, you obviously have one. That could be the reason it fails also, although the server version is usually very good with raid.
So with that in mind... I'll suggest 2 plans.

1. Boot on a LiveCD and go to it's desktop. Open a terminal session.
```

fdisk -l

```to find the X in sdX of your "drive"
```
[FONT=monospace]
[/FONT]sudo mdadm --zero-superblock /dev/sdX

```--OR--

2. Boot into your BIOS settings. Note the drive's make and model.

Boot on an Ultimate Boot disk. Go to Disk Utilities. Use a disk utility of that make to do a low-level format. 

Boot on a GParted disk to create a logical ext4 and a logical swap partition.

Note- I have these CD's and more already. Computer Recycler / I get a lot of used parts cheap. On drives, we always do allot of tests and do a low level format. Start out clean, mark out any bad sectors, etc. I prefer this at it sets my mind at ease.

--OR--

3. Boot on a GParted LiveCD. Delete the partition table. Add a partition table. Partition the drive.
---
Boot on the Server Install CD and try to install.
//

---

### Post by darkod on 2012-02-25
I might have spoken too early. On second look, the /dev/mapper/... device from the image looks like LVM.

Are you trying to install with LVM too? In that case, are you aware that you need separate /boot partition outside the LVM? Did you create it?

When using LVM you can't have the boot files in a boot folder on your root partition. You need a separate /boot partition, without exception. If you didn't do this your install is probably failing because of this.

At first it confused me because hardware raid, fakeraid, and LVM devices all start with /dev/mapper/... It's not always easy to tell what it is from one look.

The software raid devices start with /dev/mdX.

---

### Post by MAFoElffen on 2012-02-25
> **darkod said:**
> I might have spoken too early. On second look, the /dev/mapper/... device from the image looks like LVM.

Are you trying to install with LVM too? In that case, are you aware that you need separate /boot partition outside the LVM? Did you create it?

When using LVM you can't have the boot files in a boot folder on your root partition. You need a separate /boot partition, without exception. If you didn't do this your install is probably failing because of this.

At first it confused me because hardware raid, fakeraid, and LVM devices all start with /dev/mapper/... It's not always easy to tell what it is from one look.

The software raid devices start with /dev/mdX.
He said he had a small chassis case... Of that model = One 3 1/2" drive bay.

I'm thinking that if he got rid of everything on that drive (everything else on that box checks out hw-wise) that it should do fine.  He's not sure of the memory, but I've installed server w/ 64MB.

EDIT-- Besides, Its a fresh install. Nothing there to save and wouldn't hurt anything.

---

### Post by darkod on 2012-02-25
The OP seems to have stopped responding so far. I am almost definitely sure it's the LVM issue.

The LVM device names are with syntax /dev/mapper/nameofVG-nameofLV which corresponds to the first image about the grub error. The kernel error is probably because the kernel also goes in /boot folder and if the OP never created separate /boot partition as required for LVM use, the kernel install (or trying to read it) would give some error.

In case the OP wants to continue, or anyone reading this in similar situation, just create a /boot partition outside the LVM and off you go.

---

### Post by MAFoElffen on 2012-02-25
> **darkod said:**
> The OP seems to have stopped responding so far. I am almost definitely sure it's the LVM issue.

The LVM device names are with syntax /dev/mapper/nameofVG-nameofLV which corresponds to the first image about the grub error. The kernel error is probably because the kernel also goes in /boot folder and if the OP never created separate /boot partition as required for LVM use, the kernel install (or trying to read it) would give some error.

In case the OP wants to continue, or anyone reading this in similar situation, just create a /boot partition outside the LVM and off you go.
Yes. I agree.

I think deleting the partitions and partition table... and starting over (without using RAID or LVM) would be the same and easier.

I have a bunch of 2.5GB drives that I thought were too small for anything but maybe a separate /boot. What a pain and wasted investment in time those were.

Either way he does, it's going to entail partioning and formatting.

Hey Darko... Sending you a PM for something private.

---

### Post by ganewbie on 2012-02-29
Thanks to all, tried many different CDs and everytime it will come up with different error, then I moved to USB that came up with another new error. 
Finally I tried 10.4 from USB and it works first time. I will be asking many more questions as I am very green to servers.
But basically how do I open a web browser?

---

### Post by MAFoElffen on 2012-02-29
> **ganewbie said:**
> Thanks to all, tried many different CDs and everytime it will come up with different error, then I moved to USB that came up with another new error. 
Finally I tried 10.4 from USB and it works first time. I will be asking many more questions as I am very green to servers.
But basically how do I open a web browser?
```

sudo apt-get install elinks

```Because Server is meant to stay light with just the applications "you" want on it, you have to install applications on to the base system. A browser isn't installed as a default.

Because you need a browser to turn in bug reports and for "other" app's, I install the above browser on all my servers. It is light, text based and seems to be able to handle more web page formats than others I've tried.

---

