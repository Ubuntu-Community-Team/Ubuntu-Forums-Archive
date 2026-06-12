---
title: "Fresh ubuntu 14.04-2 install freezes"
date: 2015-06-20
forum: Installation &amp; Upgrades
---

### Post by gu22 on 2015-06-20
Hi folks,

I have put a clean install of 32 bit Ubuntu 14.04-2 LTS on a 80 gig drive, the drive was erased before the install. The system has 2 gigs of ram and has a Intel core 2 duo as the CPU. Ubuntu will install ok and will boot up,  some programs work like the writer, calc, and presentation app. But then if I choose to get info on the sytem, it will just hang and freeze up at that point, also happens if I try to use Firefox. The only way for me to get out of the system freeze is to do a reset. I am kind of puzzled as I don't know what's causing the problem. I did get a notification that there was some kind of system problem and I sent off the bug report, something related to "couldn't handle paging request". This system is pretty plain vanilla so I am not sure what I should check out. I do have a USB and Firewire card installed along with a fax modem card, wonder if I should take these out to see if that has any effect. I am going to try a different install of an earlier version 12.04 LTS to see if that gives me any problems but I will wait to do that until I get some feedback from someone here on the forum to see if I can fix the current install.

If you have any idea, suggestions, please let me know as I don't know what else to try. I have done 3 reinstalls and fiddled around but to no avail.

Thanks for any help you can give, I will be happy to give further details on system if they are needed.

GU22

---

### Post by gu22 on 2015-06-20
Update to my problem...

I took out the USB/Firewire card and the fax modem card. The only things hooked up to my system are the keyboard and mouse, the VGA cable to the monitor, and the disk drive. There are no other peripherals attached.

Same behavior as before, the libreoffice apps seem to work but when I try to get info on the system or if I try to use Firefox it will freeze just like before. So, it doesn't look like those cards I had installed were the problem.

GU22

---

### Post by ubfan1 on 2015-06-20
2G of ram might be marginal, especially with unity.  Do you have a swap partition on the disk?  You could try another desktop with less memory requirements, or give Lubuntu a shot.  Lubuntu should work better since it defaults to another desktop.  What video do you have?  Anything proprietary like Nvidia?

---

### Post by gu22 on 2015-06-21
> **ubfan1 said:**
> 2G of ram might be marginal, especially with unity.  Do you have a swap partition on the disk?  You could try another desktop with less memory requirements, or give Lubuntu a shot.  Lubuntu should work better since it defaults to another desktop.  What video do you have?  Anything proprietary like Nvidia?

I had a different system with only 512MB of ram and it worked ok but it was slow as molasses, I think the video drivers were not correct. I played around with that for a while, it was stable, everything I did worked but it was just super slow regarding screen redraws/updates. I fiddled a bit too much trying to adjust the vid driver and I screwed things up because after that, I'd only get a black screen.

When I did the install I just let the installer do it's thing, do I have to create a swap partition myself ?

I think the video is some kind of Nvidia card.

I took your suggestion and downloaded the latest Lubuntu, put that on a disk and tried installing that. Everything seems to be going ok but about halfway through, the install will just hang, geeze, don't know what is causing this new problem ! Nothing I have done so far has worked with exception of that second system with 512 Mb of ram but it was slow.

Not sure what I am going to do now.

GU22

---

### Post by mörgæs on 2015-06-21
Have your tried the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by gu22 on 2015-06-22
> **mörgæs said:**
> Have your tried the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

Thanks for your info, I went out and downloaded that, I was able to make a complete install finally without it locking up, lubuntu looked pretty nice. But after the install when I try to do something, the same problem happens, the system will freeze up !

Lubuntu shouldn't be that difficult to set up since this machine is fairly plain vanilla,  there is something strange going on. I don't understand why Windows Xp will run on the machine yet I cannot get some kind of Linux up ??

Well, if anyone has more ideas, please let me know. Somebody's got to have an answer as to why this is going on....

I am going to try an install on a totally different computer to see if I can get a better result.

The one question I have is...I do have a much newer computer that I can use to make some kind of install, if I get Ubuntu or Lubuntu running, can I take the drive out once it is set up and use it in an older machine  ? Or are there specific hardware things locked in that requires that you use that disk with that particular computer when you do an install ?

GU22

---

### Post by ubfan1 on 2015-06-22
Switching the disk to another machine will very likely have driver issues, which is probably what you are experiencing now.  Nvidia is causing all sorts of headachs these days, particularly on older machines.  Find out your graphics controller:
> lspci -v
and see what driver you are using.  If you are using the nouveau driver on an Nvidia chip, you might have performance issues, or overheating problems.  You usually install the Nvidia drivers through the "software and updates" program, under the "additional drivers" tab.  After a reboot, the nvidia driver should be in use (check with lsmod  |  sort  ) or the lspci command.  If you don't have the nvidia listed in lsmod, check to see if the  nvidia driver module had been built (its name is something like nvidia-xxx.ko where xxx is the driver number like 304, ...):
find /lib/modules -name "*nvidia*"
Each kernel will have a set of modules.  your running kernel is found from uname -r  If in paths starting with your kernel name, there are no .ko files or only an nvidiafb.ko, the kernel was not really build,  so try to rebuild it from a terminal:
sudo apt-get --reinstall install nvidia-current
(Assuming that's the additional driver you selected earlier).  You could use the specific driver number instead of current.  See that the terminal output claims to have build the driver module.  reboot, and check again what video is running.

---

### Post by mörgæs on 2015-06-22
If you are using only open source drivers there's nothing wrong with installing on one computer and moving the hard disk to another.

---

### Post by gu22 on 2015-06-22
> **ubfan1 said:**
> Switching the disk to another machine will very likely have driver issues, which is probably what you are experiencing now.  Nvidia is causing all sorts of headachs these days, particularly on older machines.  Find out your graphics controller:

and see what driver you are using.  If you are using the nouveau driver on an Nvidia chip, you might have performance issues, or overheating problems.  You usually install the Nvidia drivers through the "software and updates" program, under the "additional drivers" tab.  After a reboot, the nvidia driver should be in use (check with lsmod  |  sort  ) or the lspci command.  If you don't have the nvidia listed in lsmod, check to see if the  nvidia driver module had been built (its name is something like nvidia-xxx.ko where xxx is the driver number like 304, ...):
find /lib/modules -name "*nvidia*"
Each kernel will have a set of modules.  your running kernel is found from uname -r  If in paths starting with your kernel name, there are no .ko files or only an nvidiafb.ko, the kernel was not really build,  so try to rebuild it from a terminal:
sudo apt-get --reinstall install nvidia-current
(Assuming that's the additional driver you selected earlier).  You could use the specific driver number instead of current.  See that the terminal output claims to have build the driver module.  reboot, and check again what video is running.

Ok, I did find out that I have VGA compatible controller GeForce 7050, I then did the lscpi -v and it said that I was using the nouveau driver, I then installed the current nvidia driver. Ok, did a reboot, again did the lspci -v and this time it says I am using the nvidia one, did another reboot but the problem is now the dock on the left is non-functional, no mouse clicks on any of the icons there will do anything. Even though I the dock doesn't work I can still get into the terminal mode so if there are other things I need to check out please let me know. Hopefully I can solve this issue but it does feel like I am making some progress now.

Anyway, thanks to all who have offered info.

GU22

---

### Post by ubfan1 on 2015-06-22
Switching video does tend to confuse the desktop.  The problem is caused by some old configurations stored in your home directory, in files starting with a dot like .Xauthority.  Some of these are directories.  There might be a minimal set to delete, but since this is a new installation, with nothing really there to save, just delete the lot, and let them get rebuilt (the next time you login).

---

