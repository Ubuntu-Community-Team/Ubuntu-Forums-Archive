---
title: "New installation of 12.04 Issues"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by UM3BUNTU on 2012-05-10
Any help with this problem would be greatly appreciated.

System Specs: 

Acer AS 1410
CPU: Intel Core 2 Solo SU3500
Video: Intel GMA 4500MHD 
RAM: 4GB 

Issue: 

I apologize if I'm vague or unclear at any point. I am fairly new to Ubuntu and have only played around with it a couple of times.

I wiped the computer and did a clean install of Ubuntu 12.04. No issues during install and format ran without a hitch. I then ejected the CD and rebooted the computer. Upon reboot, I was taken to the GRUB menu to select to boot to Ubuntu or Recovery mode. Attempting a normal boot bring up either a completely blank screen with no error message or a black screen with flashing cursor. 

Attempting to boot into Recovery Mode brings up a host of messages; the last one being '[33.362505] ata1: EH complete' but then the system just hangs there. I have attempted a clean install of Ubuntu multiple times and have confirmed that the Live CD works with no problems.

I have seen a few forums where it's said that the nVidia drivers may play a part in this issue but have not seen any definite fixes that I could do. The only thing I haven't tried so far is a complete wipe of the drive with DBAN and attempting another install. Let me know if I need to provide any additional information and thank you for any help with this issue.

---

### Post by Mark Phelps on 2012-05-10
The black screen with flashing cursor is normal.  It will stay like that for a while and then go completely black.  Ubuntu 12.04 can take some time to boot.  Give it a few minutes and see if the flashing cursor remains.

---

### Post by Jack the R on 2012-05-10
Maybe something in this thread will work - [Link](http://ubuntuforums.org/showthread.php?t=1965820)

I've read about the nvidia problem while trying to solve my problem ( I don't have an nvidia card), and it appears to be solveable.  The answers you want are out there.

---

### Post by darkod on 2012-05-10
If you have Intel video I don't see how nvidia drivers would play a role.

It might be better to run the boot info script to make sure everything is in place. You can find it in the link in my signature. Post the results as explained there.

---

### Post by ishehroze on 2012-05-10
I am new with alternate installation. Need a tutorial to get help. I tried creating a alternate usb but it demands a cd at some point. Also having the 'can not mount /dev/loop0' issue with 10.10

---

### Post by darkod on 2012-05-10
> **ishehroze said:**
> I am new with alternate installation. Need a tutorial to get help. I tried creating a alternate usb but it demands a cd at some point. Also having the 'can not mount /dev/loop0' issue with 10.10

And how is that connected to this thread???

Anyway, I think the alternate install depends on running from cd, it expects the cd. If running it from usb stick you can do the workaround presented here:
[http://ubuntuforums.org/showpost.php?p=9705738&postcount=2](http://ubuntuforums.org/showpost.php?p=9705738&postcount=2)

---

### Post by UM3BUNTU on 2012-05-11
Thank you everyone for your help. I haven't resolved the issue yet. I was concerned with GRUB overlapping with the Windows MBR since I installed 12.04 over Windows 7. I have since completely blanked out the disk and am going to start all over again today and will try and isolate every little problem as it comes up.

---

### Post by dino99 on 2012-05-11
you might look at adding boot option, like nomodeset or noacpi

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by UM3BUNTU on 2012-05-11
Unfortunately, I can't even get to these options. I just got done installing Ubuntu on a completely blanked out disk. Everything seemed to be normal and worked fine. I then rebooted the computer and have now been welcomed by a completely blank screen. It looks as if Ubuntu is trying to load but it's been sitting here for the better part of 20 minutes.

Update: I did a manual power of off the machine and have gotten to the GNU GRUB loader menu. I don't really know what to try from here since I haven't been able to get past this point before.

Update 2: Ok, I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=1743535") by using the xforcevesa kernel option to bypass any possible video problems. I was able to log in to my profile via command. I'll keep doing some digging. Any more help would be greatly appreciated.

---

