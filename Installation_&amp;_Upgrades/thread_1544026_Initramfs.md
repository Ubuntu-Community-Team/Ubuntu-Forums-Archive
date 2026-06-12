---
title: "Initramfs"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by Nwwmac on 2010-08-01
I tried to install Mint 9 (pretty much equivalent to 10.04 as far as I know) on my parents old HP PC running Windows XP SP3. I was quite surprised when the boot CD, which I used successfully at home on a more modern computer (aluminum iMac 7,1) failed to boot. I had hoped to at least be able to show them the interface before trying a real install. 

The error message was quite cryptic: 

Initramfs

Unable to find a medium containing a live file system. 

I was able to get a list of commands after that but the few I tried to use to bypass the issue - continue, etc. did nothing. I tried to boot a second time using 'compatibility mode' and the result was the same. A memory test did not turn up any problems. 

My parents computer is a few years old but it runs XP alright. The main HD has about 30 GBs free and the video card is from an Nvidia Geoforce. I think it has 128 MB of video memory. Of course I can find out more if need be. 

Any advice on how to proceed would be welcome. I've got no idea how to troubleshoot this one. My own install went flawlessly and I hear about Ubuntu being great on older hardware (less demanding).

---

### Post by DarkEnergy.0 on 2010-08-01
Depends.

Are you running on disk or installed

---

### Post by DarkEnergy.0 on 2010-08-02
If youre running on cd yo shouldnt have any problem try erasing the computer cache by disconnecting it and taking off the battery.

Then put the cd in again.

If the black screen console appears without starting up normal try.

```
init= bootarg
```

If you have it installed and the same console appears try the same code.

If not then youll have to reinstall it again.

---

### Post by Nwwmac on 2010-08-02
The computer only has XP so far and is a desktop computer. I'm not sure what is meant by "erasing the computer cache by disconnecting it and taking off the battery". 

The boot from the CD starts normally but does not succeed, ending with the Initramfs error on a black text screen.

---

### Post by weiersc on 2010-11-28
I have a very similar problem and can also not yet figure it out.

I have always run Ubuntu on this particular PC. 10.04 worked quite well. Then I did an upgrade (over the Internet) and when I tried to reboot the computer it gave the same initramfs message. I found that when I selected an older kernel in GRUB I was able to boot properly, but I keep feeling that there are lots of problems with this. Today a new kernel was installed during one of the updates. I tried to reboot again, but still the same initramfs message. 

So I decided that I've had enough and decided to just re-install 10.10 from CD. But to my surprise the CD would not boot - with the same initramfs message - cannot find a medium containing a live file system. So it is obviously somethign wrong with 10.10's installation.

I don't know where to begin to look to try to solve this problem. Do I purge and re-install GRUB? Is there some set-up file that I can edit so that the computer recognises the right hard drive?

Hahah - I just don't have enough knowledge to know where to begin searching for an answer.

---

### Post by matt_symes on 2010-11-28
Hi

Does this thread offer any solutions (its a bit old but...)

[http://ubuntuforums.org/showthread.php?t=1332782](http://ubuntuforums.org/showthread.php?t=1332782)

Kind regards

---

### Post by weiersc on 2010-11-28
I think I read through that thread carefully and tried the following without success:

1. I made a bootable flashdrive using Ubuntu's startup disk creator, but haha, then it seems my particular system does not offer an option to boot from a flash drive.

2. I burnt a brand new copy of 10.10 onto a cd - it gives me the initial screen and then eventually it just goes back to the initial error: "Unable to find medium containgin a file system".  I typed exit, and then it gave me the following:

cp: cannot create '/root/var/log/': Is a directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init-bootarg.

I typed "exit" again ... then I got a kernel panic and then everything hung.

3. I hae also downloaded the latest build of Ubuntu Natty and tried to boot from that DVD. Exactly the same problem except that it is now BusyBox v.1.17 giving the problem and not BusyBox 1.15.

4. When I put in the 10.04 cd it boots perfectly. I might have to install 10.04 again, which would be a bit of a shame as 10.10 works really well on my laptop.

5. Note: I also disabled quick boot in my Bios.

Any ideas?

---

### Post by matt_symes on 2010-11-28
Hi

Looks like this was a known bug in 10.10 beta. 

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/543875](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/543875)

> When trying to boot Ubuntu 10.04 beta1 64bit on the Primary Slave IDE CD-ROM drive it fails with the message:
stdin: error 0 (repeated over 25 times)
 BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu9) built-in shell (ash)
Enter 'help' for a list of built-in commands
 (initramfs) Unable to find a medium containing a live file system.
 **If I switch my CD-ROM drive over to Primary Master IDE then it will boot no problem.**
 I'm not using any of the other IDE ports, my HD is SATA.

What i highlighted was the posters solution.

Kind regards

---

### Post by weiersc on 2010-11-28
OK, I'm going to open my box and try to switch those cables. I've never messed around with the cables before, but it can't do damage as I really want to find a solution.

I am a bit skeptical however. I don't think the problem lies with the cdrom alone. I think it is the same problem that I get when I try to boot up with the latest two kernels (Linux 2.6.35-23, and 2.6.35-22.) The computer boots fine with 2.6.32-25.

The problem started after I did a network upgrade of 10.04. The problem with the cdrom is just an additional problem over and above the initial problem.

---

### Post by matt_symes on 2010-11-28
Hi

> The problem started after I did a network upgrade of 10.04. The problem  with the cdrom is just an additional problem over and above the initial  problem.

Yes, quite possibly. It not a problem i have ever had though so its difficult to diagnose.

Kind regards

---

### Post by weiersc on 2010-11-28
Unfortunately I am still in trouble:

The DVD/CD Drive and the Hard drive are both Sata drives. I basically switched the two Sata cables.

The 10.10 cd still boots up and gives me the option to install Ubuntu or boot the Live CD or check the disk for defects - It does not matter which option I choose - The splash screen comes up and the little white dots appear for about 2 minutes while the drive whirrs away, and then the cd powers down and I get a message: Unable to find a medium containing a life file system.

When I boot from the first (only) hard drive choosing the kernel I get the message:
Gave up waiting for root device. Common Problems:
- Boot args (cat /proc/cmdline)
 -check rootdelay = (did the system wait long enough?)
 - Check root = (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/c831c109-3108-4756-931b-efb7ad65376a does not exist.
Dropping to a shell!

How else do I try to get to the bottom of this?

Edit:
I tried to boot with the Natty Disk again and I found a way to disable quiet and splash to get some sense of what happens when I boot:  
The message that keeps coming up is something like:
[drm:drm_edid_block_valid] *ERROR* Raw EDID:
[dm] nouveau 0000:00:12:0 DDC responded, but no EDID for DVI-D-1

---

