---
title: "Unbuntu 9.10 not installing. CD mounting issue?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by u_knew on 2009-11-25
Hello,
I downloaded and burned an Ubuntu 9.10 cdrom and attempted to install on an HP Media Center PC m7067. The initial menu to choose between running as live CD, installing, checking memory, etc. comes up, but hangs with a pulsing logo in the center of the screen when I try either running as live CD or installing.

Hitting Ctrl-C gets rid of the logo and shows the system messages. With the messages displayed I can see that the system is repeatedly trying to access the cdrom to mount it. The messages say:
```
mount: mounting /dev/sr0 on /cdrom failed: Invalid argument
init: line 1: can't open /dev/sr1: No medium found
init: line 1: can't open /dev/sr1: No medium found
mount: mounting /dev/sda1 on /cdrom failed: Invalid argument
init: line 1: can't open /dev/sdb: No medium found
init: line 1: can't open /dev/sdb: No medium found
init: line 1: can't open /dev/sdc: No medium found
init: line 1: can't open /dev/sdc: No medium found
init: line 1: can't open /dev/sdd: No medium found
init: line 1: can't open /dev/sdd: No medium found
init: line 1: can't open /dev/sde: No medium found
init: line 1: can't open /dev/sde: No medium found

```This repeats until the system finally gives up and ends with:
```
(initramfs) Unable to find a medium containing a live file system
```It then drops me into a Busybox shell.
From there I tried mounting manually with the command:
```
mount -t iso9660 /dev/sr0 /cdrom
```but it just returns:
```
mount: mounting /dev/sr0 on /cdrom failed: Invalid argument
```The computer has two dvd drives:
ASUS DVD-E616P3H
HP DVD Writer 640B
I tried both and get the same result.

I tried the same cd on another computer and it works fine there

Any suggestions on what to try next?

---

### Post by u_knew on 2009-11-27
Turns out problem is with video card.
I tried running Knoppix live CD and found udev was causing it to hang as well. This made me think that there might be some hardware that was causing udev problems. So I tried removing IDE expansion cards one at a time. Removing the video card and hooking the monitor to the onboard video port on the motherboard fixed all of the problems.
I guess in Ubuntu, once udev got messed up trying to handle the video card, it also messed up the /dev files for the DVD drives.
The video card is an ATI R9250. I do not know if the problem is a conflict between the onboard video and the expansion card or a Linux driver problem with the expansion card itself. Unfortunately I have not found a way to disable the onboard video. HP's online documentation show no motherboard jumpers to disable the onboard video. Setting the BIOS configuration for primary video source to PCI instead of onboard did not seem to disable the onboard video or fix the problems I was having.

---

### Post by mmmmhack on 2009-12-15
Hey, thanks for this followup. Your information helped me to solve a similar problem and put a computer under the Christmas tree for our son! 

My mom's year-old computer became damaged a few months back - the video was corrupted with lines in the display and her Windows Vista 64 was toasted (it was an HP system from Costco). I replaced the video card with an old one that I put in a PCI slot and the video was fixed but I couldn't install Ubuntu. Got an error message similar to what you had. It never would have occurred to me to plug in the bad video card again, but after reading your post I tried that (keeping the PCI card too) and then I was able to install Ubuntu!

thanks again,

William

---

### Post by MeNtuxRoKinU on 2010-02-08
Hey there, I have the same issue. My question is, did you get the good video cards back into the machines after the install, and if so, did you have any other issues? Drivers or configuration problems. I really don't need the graphics card, but I do like eye candy. Let me know, thanks!

---

### Post by siyisoy on 2010-04-13
I have the same problem. I dont have a video card on main board. It just have one video card which is Geforce 8900 gt.

---

### Post by siyisoy on 2010-04-19
Any help with this problem. I have a brand new machine with a Gigabyte 790fxta-ud5 board and cant install actually any linux on it.

---

### Post by siyisoy on 2010-04-19
I have tried 10.04 Beta2 and failed with the error message:
"Unable to find a medium containing a live file system" which foreshows that even 10.04 will not fix the problem I guess.

---

### Post by xd20 on 2010-10-06
> **MeNtuxRoKinU said:**
> Hey there, I have the same issue. My question is, did you get the good video cards back into the machines after the install, and if so, did you have any other issues? Drivers or configuration problems. I really don't need the graphics card, but I do like eye candy. Let me know, thanks!

this is what i'd like to know as well

---

