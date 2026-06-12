---
title: "Error on boot &quot;Read Error&quot;"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by PDD on 2010-05-10
Hi Folks,

I have just installed Ubuntu 10.04LTS however when I attempt to boot the HDD I get the following error message

Read Error

Thats it nothing else, I am able to boot a USB installed version of Ubuntu 10.04LTS no proble. I can boot a Live CD of the same version no problem but when I installed it to the hard drive it just seems to fall over. I've tried adjusting the boot order, putting the HDD first and removing everything else but no joy. Im a linux n00b so no idea what to do next apart from go back to windows :-( Any and all help would be greatly appreciated. 

Regards,

Dave

---

### Post by mikewhatever on 2010-05-10
Boot from the USB, open Applications->Accessories->Terminal and post the output of the following:
sudo fdisk -l

---

### Post by PDD on 2010-05-17
Hi Folks,

Sorry about the long delay, wasn't in the best of health. Output below:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a94df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19569   157185024   83  Linux
/dev/sda2           19569       19930     2898945    5  Extended
/dev/sda5           19569       19930     2898944   82  Linux swap / Solaris

Disk /dev/sdb: 8166 MB, 8166309888 bytes
255 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         993     7974855    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(992, 210, 63)

It is marked as a boot partition (I think) so no idea why it is not booting up. Any feedback appreciated. 

Dave

---

### Post by complience on 2010-05-21
Am getting the same error.

I have tried swapping to new both the Harddrive and DVD drives.

I have tried multidifferent CDs/ISO burned on different machines, different Disks, even tried a ubuntu install CD from a magazine.

Always the same error..
Can install from a usb but not a CD

---

### Post by kansasnoob on 2010-05-21
To really get a better idea of what's going on we need to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kalmos on 2010-10-23
Perhaps I can revive this thread. I have the same error as the original poster.

I'm working on my relatives' computer. I find that it mysteriously has more problems than any other computer I know of.

**There were weird Windows problems...**
So, I installed Windows 7 on it a few months ago. I made sure to create a limited account for my relatives, and did not tell them the admin password, so they couldn't install anything or change important settings. Eventually things got weird. RealPlayer was installed twice; I uninstalled RealPlayer, reinstalled, and two days later RealPlayer was not working anymore. At some point before this, the computer did not boot into Windows. It hung at a black screen, eventually displayed some sort of "Windows Recovery" window, and my relative followed through with that. It was back to normal after completing the recovery.

**I installed Ubuntu 10.10...**
Tired of dealing with Windows, I put Ubuntu 10.10 on a new partition, so now it's a dual-boot machine. It worked great until today.

**The Error**
Today I started up the computer, waited for a few minutes, eventually a black screen comes up with only the text "Read Error". That's it, no other text, just "Read Error" in the top left corner.

I checked the BIOS to see if it said anything strange about the HDD. Nope. I tried to boot from the same USB from which I originally installed Ubuntu 10.10. After 10-15 minutes of waiting for the Ubuntu animation to finish, I lost my patience. The first time I installed from USB, everything went much more quickly.

Now I grabbed the HDD, plugged it into my own computer, and lo and behold I can read it without problems. Backed up the data, and ran [boot_info_script]("http://sourceforge.net/projects/bootinfoscript/") to see what's up. Well, I don't know how to interpret all of the information, but it seems like there are no errors.


I'm not sure what to do now... I have new hard drives that I can use, should I just use them? Is this disk not reliable anymore? Should I just avoid dual-booting? Should I try to boot from USB again and wait for more than 20 minutes for it to boot?

If I can get it running again, I'm putting Ubuntu 10.10 only, and I'll use a virtual machine with Windows so we can use the Cannon scanner (ugh).

I hope someone has some experience dealing with this issue. I'd appreciate any advice you can give me. Thanks in advance! I'll be happy to give more information if it would help to figure out what's going on.

Attached is the RESULTS.txt generated by boot_info_script055.sh. The "bad" hard drive is **sdb**.

---

### Post by imwithid on 2010-11-25
Partially solved: Reason &#8211; Insufficient power.

I was experiencing a similar problem, however, it depended on the system that it was hooked up to. Currently, I am using an USB external hard drive for both storage and as a quick alternative to an Ubuntu Live CD (for use on computers that may have problems or whose installed systems are a mess). I recently switched from a Seagate Momentus 7200.4 500GB low power drive to an old Hitachi 5400 100GB inefficient drive. Since it worked well with my laptop with a higher guage short USB mini-B cable, I've tried to avoid the Y-cable as I only have two usb ports and a USB-eSATA combo port (which requires a converter if it is to be used as a USB port) on my laptop.

Installed on this hard drive is Ubuntu 10.04.1 x86 with updates current to yesterday. It was installed on a HP Pavillion DV4-1225dx. On this system, upon reboot, I got the &#8220;Read Error&#8221; which then was followed by two other lines of warnings and then to the BASH screen. I am not an advanced user, so I chose to reboot and afterwards, everything was fine.

I should mention that I was booting DIRECTLY from the hard drive. I was NOT using the internal system's GRUB boot loader to boot from the external drive's OS.

When I tried to boot directly on my desktop system (a custom build Intel system), I simply got the &#8220;Read Error&#8221;. When I tried booting via the internal hard drive's GRUB boot loader, I simply got a black screen. I tried booting directly via a Gateway Quad Core AMD desktop at a friend's house and got the same black screen.

It kicked in that perhaps the energy demanded on this drive required a Y-cable. After hooking it up, it worked on my Intel desktop. On my HP laptop, it also worked via the Y-cable. Using the single cable, it usually works as the current is usually sufficient but lies within that range where sometimes it is not. I will be testing it on the same Gateway system this weekend as well as a Dell laptop to verify that this is the case.

The only problem I have now is with an old Gateway 450ROG laptop (a Pentium M based system). It is not possible to boot from an external device, despite the latest BIOS update, however, I cannot even use the GRUB boot loader. I get the following error:

```
error: no such device xxxxxxx-4xxx-xxxx-xxxx-xxxxxxxxxxxx.
error: hd1,1 cannot get C/H/S values.
error: you need to load the kernel first.

Press any key to continue...
```

I have yet to find a solution to this problem. I have a USB to DC barrel connector that I will use to verify that there is insufficient current to drive this device, however, I doubt that power is the issue here.

[Edit]
I should also add that I had the same results using Ubuntu 10.10 x86.

---

### Post by imwithid on 2010-11-26
I started to dig a bit deeper into the GRUB boot loader and upon boot, I wanted to see what devices were being detected, so I went to the command line option and typed "ls" when prompted and all I saw was something like:

```
GRUB> ls
(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)
```

It did not see my external hard drive which I was trying to boot from by using the GRUB boot loader (since my old laptop cannot boot from USB devices - thanks Gateway).

Digging deeper yet, I remember formatting the drive on a 64 bit system (partitioning via GParted) Having edited the GRUB menu at boot, I noticed a PAE extension to the usual linux image file pertaining to (hd1,1).

It may be the reason why I cannot boot from an external drive on an old laptop using the GRUB boot loader. I am in the process of verifying this as I have formatted the hard drive, repartitioned and currently in the process of reinstalling Ubuntu 10.04.1 x86 directly from this laptop. I should know in the next few minutes.

[Edit]
The change is null. The PAE extension is no longer there (I was expecting such a result), but it seems the problem is more complex.

---

### Post by thuleni on 2010-12-01
I changed my motherboard battery last night, and now get "Read Error" on booting to Ubuntu, on dual boot system.  This is the most frustrating thing in an otherwise great operating system.  It is the second time I have encountered this issue (last time was a change of power supply).  

I fixed it last time after three days of re-loading Grub2 and playing around Grub 2 updates, etc.  Fixed it eventually, but as usual, no idea of what evntually fixed it.  I think I found a web page buried deep in the 'net, which talked about device.map.  Do you think I can find it again - not yet - day 2 searching for the answer...

---

### Post by jrarrmy on 2010-12-23
Hey there,

I could use some help please..

I just tried installing a couple virtual programs and a couple reboots later I get this read error: msdos1..
Now I can't boot at all except from usb, is there any way I can manually uninstall vmware and another virtual program so I can boot my drive again?

Thanks so much,
Jeremy

---

### Post by carlosfilho88 on 2012-02-25
Today I had the same error. I was using my desktop and suddenly it stopped. When restarted, I saw the "read error" and then I despair. I did some procedures that you talked, but doesn't resolved. Simply open my computer, reconnected all the cables and everything is working perfectly.

---

### Post by oldos2er on 2012-02-25
Closed, necromancy.

---

