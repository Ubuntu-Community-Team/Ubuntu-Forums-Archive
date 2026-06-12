---
title: "Install issue: initramfs failed to set xfermode"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by underwog on 2007-12-11
I am trying to install Ubuntu 7.10 on a new machine for the first time using the LiveCD. I keep getting (initramfs) ata3.0 failed to set xfermode errors. I have searched and found the irqpoll/grub fix, but that applies to a system that is already installed. I can't get more then 10secs into the install. Here are the details: :confused:

Abit IP35-Pro, bios V14, Q6600@3.7Ghz (9x412, yes the PCIe and PCI busses are locked; no OC yeilds the same result), 4x1GB DDR2-800@DDR2-824, ATI 1950XTX, Segate 7200.10 400GB SATA HD, DVD IDE drive. The box is Windows Prime95 25.3  small FFT stable 24hrs+ and Memtest 1.70 stable.

The HD has two partitions with XP64 installed on one of them
XP64 ~100GB
Raw Partition~the rest (created it during the XP64 install)
8MB unallocated

The DVD drive was used to install Ubuntu 7.04 LiveCD onto a different system just a few days ago and it worked fine:

ECS RD480-A939, Opteron 165@2.7Ghz, 2x256MB DDR400, Nvidia 7600GT, Samsung 300GB SATA HD, and the same IDE DVDRAM drive.

 I tried playing around with the SATA/IDE controller options in the bios (IDE/AHCI), SATA as bus master, etc. I don't think I tried every combination, but I tried quite a few.

Thanks.

---

### Post by ImALittleTeaPot on 2007-12-12
_system_
Abit IP-35 Pro
Radeon X1950XT
seagate 320GB
Lite-On DVD RW+-
Q6600 2.4Ghz
2x 1Gb corsair 800mghz DDR2
triple boot Vista/XP/Gutsy


As you can see, my system is quite similar to yours, and I have been a having the exact same problem. When I tried to install 7.10 I got the (initramfs) ata3.0 'failed to set xfer mode(err 40) or somth'n like that. 

Then, for no reason at all, after several attempts, 7.10 installed, but upon trying load after install, the orange bar would just hang. 1 out of about 3 times ubuntu would load (using gutsy right now). I read your post, tracked down the irqpoll thing, did it,  and ubuntu has loaded a few times in a row, but still to early to tell if the irqpoll thing has solved the problem. 


I'm skeptical about this irqpoll thing, as some people have said it hasn't worked, but atleast 7.10 boots...sometimes. Will update.

---

### Post by underwog on 2007-12-13
After much playing around and trying out a SATA DVD drive, I was able to install Ubuntu 7.10 just fine. The key was that I had to disable the JMicron chip. Even without a floppy, ide DVD, and just a SATA DVD/HD it would not boot from the Live CD. However, once I disabled the JMicron chip (under PCI settings) it worked right away.

---

### Post by ImALittleTeaPot on 2007-12-14
That would make sense.  I think the JMicron driver is for external hard drives, which i never use. I think I may have had that installed before I wiped my bios back to factory settings. Never re-installed it though. 
    And it just so happens that the adding irqpoll to the end of a kernal line in menu.lst seems to have solved my load problem too.

_UPDATE 12-24-07_
irqpoll "fix" has ceased to work. Orange bar hangs when loading from HD. Getting error message "ata5.00 failed to set xfermode(err_mask=0x40)

---

### Post by underwog on 2007-12-18
Well, after getting Ubuntu 7.10 to work fine and playing around with my new OS, I decided that if I had really fixed the problem it should be repeatable. So I tried installing from the LiveCD again...it failed. After much playing I am still unable to boot/install from the Live CD. Tried many different settings as well (floppy/no floppy, various SATA modes, JMicron enable/disable). Nothing worked. I am downloading the alternate CD to see if that fixes anything. It appears that the LiveCD with my hardware is random at best.

I should note that I wasn't having any problems booting to 7.10 for almost a week (did not use the irqpoll "fix"). Then I tried the reinstall (failed to boot the LiveCD with the same initramfs/ata xfermode error) and now it sometimes won't boot from the HD (the orange bar hangs at the start). Also should note that this is the 64bit version.

---

### Post by underwog on 2007-12-19
So I tried the alternate CD with no luck. I was actually able to get the system to boot with the JMicron chip enabled and with the LiveCD! It seems that the systems ability to boot from either CD is "random." With my origional bios settings that worked before it took several failed boots before it worked. With the JMicron chip enabled it took about 10 boots before it worked. I kept a record of my booting/bios options and will post those later. Ended up reinstalling twice and booting 40+ times with various options. Seems like this is more then just a non-supported chip on the MB. Also I am putting together another system that is nearly identical, so I will have something to compare it against. Will post results tonight.

---

### Post by ImALittleTeaPot on 2007-12-23
Hmmm, interesting.  I've done a reinstall with the 32 bit and ubuntu usually loads....But every once in a while i get an "ata5.0 failed to set xfer mode (err_mask = x40)" instead of "ata3.0 ......".  I've been looking around the forums, but If anyone else is having these problems, I can't find a disscussion on it.  I'll compare the results that you post with my system when you put it up.

_UPDATE_
Alright. The "ata5.0: failed to set xfermode (err_mask=0x40)" errors are far more frequent, along with the load hangups. I've lost faith in the "irqpoll fix". 

 ---->another update: the last time Gutsy updated itself, irqpoll was wiped from the kernal line "kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=7eec31fb-03e9-40cd-861a-efe58a7aec56 ro quiet splash (irqpoll goes here)".  Had to replace it by editing grub from the boot menu, but I still don't consider this the "fix" (read that this option hurts performance)...but it boots again.  

Did some digg'n around. I'm new at this..like i said, but here's what i've go so far.
1. found out 'ata' errors are synonymous with hardware issues
2. During a hang from a normal boot, I'll get the error message (with ata5.0 error messages too)
              a.** root = bootarg cat proc/cmdline or missing modules ls dev/**
              b."**home/dev/disk/by-uuid/7eec31f**(filename with lots of numbers)** does not exist**".
3. I Rebooted into grub, hit 'e' to edit options, added** acpi=off** (not irqpoll this time...it booted) to first boot option, loaded into desktop, went looking for the file. Low and behold..its sitting there smiling at me in the /dev/disk/by-uuid folder, even though its not being read during boot. 
4. This is a web definition--> "A UUID (Universal Unique Identifier) is a 128-bit number used to uniquely identify some object or entity on the Internet" (notice that the "missing file" has something to do with the UUID) 


I can't find what device pertains to this "missing file" in my /dev folder. Maybe the Hard Drive since 'disk' is part of the file-path name????? i don't know.

---

### Post by Ux64 on 2007-12-26
My thread about same problem: [http://ubuntuforums.org/showthread.php?p=4010877#post4010877](http://ubuntuforums.org/showthread.php?p=4010877#post4010877)

It seems that problem is P35 chipset related. I'm using 64 bit version. Everybody didn't mention if they're using 32 or 64 bit version. So I assume some of you are using 32 bit version. I'm using 64 bit version.

About setting irqpoll. I think it's not right. Because most of time, system works fine. It's just some random boots, like 2 of 10 that fail. It tells that setting irqpoll isn't required actually. Something else is causing the problem.

I'll be very curiously tracking this problem. Is there any motherboard BIOS updates which might help? Or does kernel require fixing?

ImALittleTeaPot - Thanks for notifying me about this thread.

I'll add my original message here, because this thread is longer.

> 
**SATA drives give errors (set XFERMODE) and prevent booting**

Thing is that if I reboot it usually doesn't reappear. Which is really strange. Maybe hardware fault, maybe not?

[[IMG]http://picozilla.com/files/141839timgp0878.jpeg[/IMG]](http://picozilla.com/en/141839/imgp0878.jpeg.html)

Chipset is Intel P35 and motherboard is Intel P35-Express.

Exact error:
```

ata1.00: failed to set xfermode (err_mask=0x40)

```

I get this error twice and then system hangs.

Drive is  Samsung T166 / 500 GB. (SATA naturally w NCQ support)

Ubuntu is 7.10 GG / 64 bit (with latest updates)


---

### Post by US41 on 2007-12-30
I am getting the same error. I created a 100 GB partition to install Ubuntu onto, and when I boot from the install CD I burned, I get one of two errors:

1. The progress bar hangs and the floppy starts seeking even though it should not be accessing the floppy. That happens 20% of the time.

2. 80% of the time I get the initramfs error above, and Ubuntu will not install.

My system:

Motherboard: Abit IP35pro (P35 Chipset)
SATA DVD burnder/reader (Sony DRU 810 1.0f)
2 Gigs of Ram
Nvidia 8500 GT
Standard Floppy
Creative X-Fi

---

### Post by US41 on 2007-12-30
I found the solution to getting past it. Apparently on motherboards, such as the Abit IP35 Pro, the Sata controllers 1-4 are double-booked and the OS cannot read them. 

To fix the problem:

1. Open your PC box
2. Unplug your SATA cables from SATA ports
3. Plug them into the highest numbered ports you have (I moved mine from SATA 1/2 to SATA 5/6)

Viola. The live CD runs and I have installed Ubuntu.

---

### Post by Ux64 on 2007-12-31
> **US41 said:**
> I found the solution to getting past it.

Arrggh! Nice work a round. I'm wondering if this would solve my problem too. I gotta try it. ;)

---

### Post by ImALittleTeaPot on 2008-01-04
Thanks! It appears that this fixes my problem.

---

### Post by Pjotr123 on 2008-01-10
I will try this solution on a PC of a friend of mine, who wants a dual boot. Will this shift of SATA number affect his current Vista installation?

---

### Post by Ux64 on 2008-01-20
I don't know if it's related. I think. But I have encountered now logical file system (ext3) corruption. 

During fsck system said something assuming write trough caching. Has anyone else encountered that message before? 

And it was really during check, check was something like 4% complete when I got that message.

I'll provide more details soon.

P.S. FS corruption lead to firefox losing all settings. And Evolution to lose email profiles. And currently file system is read only so X won't start. But I won't use that system before I got more information and details.

- Thanks! I hope that anyone else doesn't have this bad problems with P35 chip set.

---

### Post by Septh on 2008-01-20
I'm having trouble with my new P35 based motherboard and gusty, unforuntatly I cannot plug my hdd's in to the top 2 ports are they esata ports and I don't want to run my cables outside my case lol, I've tried the alpha of hardy and the live Cd works fine, so at least its been fixed for the next release, just wish I could get gusty to run on my new pc as windows full time is doing my nut.
Anyone else know how to solve this?

---

### Post by Ux64 on 2008-01-21
Here are some more error messages. For some reason system gives that error message during fsck. I don't know what it means. Or if it might be the source of the problem. 

Assuming Drive Cache: Writetrough

Read only  filesystem my current problem.

But before that I had serious problems with filesystem, so I assume there is a reason why file system is right now in read-only mode.

Cross reference:
[http://georgia.ubuntuforums.org/showthread.php?t=670910](http://georgia.ubuntuforums.org/showthread.php?t=670910)
[http://georgia.ubuntuforums.org/showthread.php?t=670700](http://georgia.ubuntuforums.org/showthread.php?t=670700)

---

### Post by Septh on 2008-01-21
There is a patch released for this bug on launchpad, but you can only patch a installed and working kernal as far as I know, so it's a bit of useless patch.
I might try putting longer sata cables in for the time being to test if plugging them into 5 and 6 will work.

---

### Post by Septh on 2008-01-21
Ok found the solution to my problem, if i change my bios settings for the controller to AHCI from ide, I can boot to the live CD no problems, just had some fun though as that breaks windows, but this is fixable after a quick google search of it, 
If anyone wants the details then ask :-)
Mac

---

### Post by aspire5020 on 2008-01-26
You are a god. Thanks a lot.

---

### Post by jcrouse on 2008-02-12
I have an Abit IP-35 Pro and am having the exact same issues. So what exactly is the fix? My HD is on SATA 0 and my CD/DVD on SATA 1. My BIOS is currently set to IDE. I am hoping I can leave it that way but realize I may need to change it. If I follow correctly I think I should move my HD to SATA 5 and my CD/DVD to SATA 6 and set my BIOS to AHCI. Is that correct?

Thanks,
John

---

### Post by BassKozz on 2008-02-16
> **Septh said:**
> Ok found the solution to my problem, if i change my bios settings for the controller to AHCI from ide, I can boot to the live CD no problems
Which Controller do I need to change and where is the setting in the BIOS?
I have an IDE CD-ROM drive and SATA HD, and Ubuntu LiveCD can't see my SATA HD...
> **Septh said:**
> 
...just had some fun though as that breaks windows, but this is fixable after a quick google search of it, 
If anyone wants the details then ask :-)
Mac
Can you please share "details"... I am having the [exact same problems]("http://ubuntuforums.org/showthread.php?t=698912")
Thanks in advance Mac,
-BassKozz

**_EDIT:_** Nm, found a fix: [http://forums.pcper.com/showthread.php?t=444831]("http://forums.pcper.com/showthread.php?t=444831")

---

### Post by aussiedaddy on 2008-02-18
I have been suffering from this problem.  I had installed on a PC with an abit motherboard (P35 chipset) with 3 SATA hard disks and a SATA CD/DVD drive.  Booting was only successful occasionally and seemingly getting worse.  I rather gather its an issue with the P35 chipset and SATA drives.  I tried setting the controller to AHCI mode but that just gave me a BOOT DISK FAILURE from the BIOS.  Set back to IDE mode - still not booting. Removed two SATA hrad disks - no better. Removed the CD/DVD (as OS already installed) - no better.  Changed the 1 remaining SATA hard drive to SATA 6 (from SATA 1) and it booted OK.  This could just be a fluke but it has made me hopeful.  Will report back after further testing.

---

### Post by Ux64 on 2008-02-18
> **jcrouse said:**
> I have an Abit IP-35 Pro and am having the exact same issues. So what exactly is the fix?

Does your system also freeze "randomly" during boot process? 

I still have this problem. So I need to boot multiple times to get system running.

I don't know which log I should watch so I could locate in detail where the problem lies.

I haven't had any corruption problems since I started to run sync before every shutdown. I haven't had enough guts to do shutdown without that process. Because getting everything messed up wasn't too fun.

Has anyone been getting NCQ to work succesfully? My NCQ status is 0/32 which (AFAIK) means that it's not being used.

---

### Post by aussiedaddy on 2008-02-18
Since changing my hard disk to SATA 6 from SATA 1 I have rebooted many times without a problem so for me at least it appears to be the solution

---

### Post by beyboo on 2008-03-13
I have an Abit IP-35 e mobo. The interesting part is that it has sata ports 1,2 and then 5&6. They have shorted ports 3&4 to differentiate  between the e and the pro mobos. 

I was happy with my gutsy install and the solution of moving the HDD to the top end SATA ports 5&6. now I have a 3rd SATA HDD and it has to go to 1 or 3 and I started facing this problem again.

Has anyone tried compiling the latest kernel on this - any luck ? I am gona give it a try in a day or two. Will post the results. 

Where is this patch someone referred to earlier ?

Thanks !

---

### Post by makko on 2008-03-15
Hey Guys,

I've had this problem too..

I'm using a n Abit IP35 Pro Board and a Q6600.

I went into the BIOS and disabled the JMicro onboard chip. Thel live disc would then load but I couldn't access my IDE drive (JMicro must control the IDE part of board.) I installed ubuntu fine then wen back into the BIOS and enabled the JMicro chip to regain access to my IDE drive.

Ubuntu is booting fine now..No probs as of yet. Apart from the fact that I haven't a clue how to use linux but that's nothing that time won't fix :)

In the BIOS I went into:

onboard pci device > storage controller > disable..then enable after ubuntu install if you need to use IDE..I'm not too sure what else it controls, maybe RAID also..

Hakko

EDIT: Now it's gone back to normal.. I need to disable to JMicro chip I want to be able to boot into ubuntu.. Kind of awkward cause i'm using and IDE drive at the moment.. I think the kernel may need to be patched.

---

### Post by Ux64 on 2008-03-16
I got rid of problem when I enabled IRQ.

No more data corruption. Failed boots etc.

---

### Post by makko on 2008-03-17
How do you enable IRQ and what exaclty does this do??

---

### Post by PopnPaul on 2008-03-18
> **ImALittleTeaPot said:**
> _system_
Abit IP-35 Pro
Radeon X1950XT
seagate 320GB
Lite-On DVD RW+-
Q6600 2.4Ghz
2x 1Gb corsair 800mghz DDR2
triple boot Vista/XP/Gutsy


As you can see, my system is quite similar to yours, and I have been a having the exact same problem. When I tried to install 7.10 I got the (initramfs) ata3.0 'failed to set xfer mode(err 40) or somth'n like that. 

Then, for no reason at all, after several attempts, 7.10 installed, but upon trying load after install, the orange bar would just hang. 1 out of about 3 times ubuntu would load (using gutsy right now). I read your post, tracked down the irqpoll thing, did it,  and ubuntu has loaded a few times in a row, but still to early to tell if the irqpoll thing has solved the problem. 


I'm skeptical about this irqpoll thing, as some people have said it hasn't worked, but atleast 7.10 boots...sometimes. Will update.

I've got an IP35-E and an e6750 @ 3.6ghz and 8800GT and it does the EXACT same thing. Even the part where it randomally installed. I think ABIT mobos hate linux.

---

### Post by QuantumAvatar on 2008-04-05
I have an Abit IP35 Pro with two internal HD's and Hardy 32-bit Beta. I can verify that moving your SATA HD's to the high ports (5 and 6) fixes all your woes. It even fixed a PCI x1 usb hub problem i was having a while back. I love the ubuntu forums!

---

### Post by makko on 2008-04-25
I wonder will ubuntu 8.04  fix this problem??

---

### Post by GammaPoint on 2008-05-30
I'm doing my first build and ran into this problem as well. I took my DVD-RW and HD SATA cables and moved them from #1 and #2 to #5 and #6 and now I'm formatting my HD within the Ubuntu LiveCD (which I wasn't able to get anywhere near before). So it *looks* like this has fixed my problem.

Thanks for all those who posted. It was a real help :)

---

