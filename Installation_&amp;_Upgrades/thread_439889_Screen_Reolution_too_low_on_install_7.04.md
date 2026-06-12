---
title: "Screen Reolution too low on install 7.04"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by seoras on 2007-05-11
Has anyone else experienced screen resolution problems with installing Ubuntu 7.04?

I recently upgraded a version 6.10 system on line to version 7.04, it all went well until l re-booted the system, only to find I was restricted to 800 x 600 or 640 x 400 resolutions whereas before I had the full range. I solved this one by removing the nVidia drivers from the system and the full screen resolution options were restored.

Then this morning I booted from from the 7.04 install CD on a Dell Dimension 5150 dual core with an ATI Radeon X600 video card with screen resolutions up to 1280 x 1024 only to find that Ubuntu  live CD only offered 640 x 400 resolution, which is very weird on a 21" monitor. needless to say I did not install Ubuntu on this system in case this was the only resolution I'd get.

I just wondered if any one else had experienced this behaviour.
Cheers

---

### Post by heimo on 2007-05-11
> **seoras said:**
> Has anyone else experienced screen resolution problems with installing Ubuntu 7.04?

...

I just wondered if any one else had experienced this behaviour.

Yes, many have. By searching these forums, you should be able to find threads with similar topics. Also very common in earlier releases of Ubuntu - I think it's less so in 7.04.

---

### Post by seoras on 2007-05-11
Yes, I had found other threads about the same problem but very few solutions or explanations why it happens. I have yet to try some of the proposed solutions but most are post installation and I have not found any explanations or solutions to this issue when running the live CD.

---

### Post by ianw1974 on 2007-05-11
I've just found a similar problem on a HP laptop with an Intel card.  It wouldn't go further than 1280x1024.  But I've subsequently fixed it.  Two things.  First:

```
dpkg-reconfigure xserver-xorg -phigh
```

select the resolutions you want.  Then you'll just need to restart X with CTRL-ALT-BACKSPACE for these to be enabled.

Sometimes this works for most people.  However, on my Intel chipset it was using the xserver-xorg-video-i810 by default.  This didn't have the latest driver available for the 945 chipset, and so I had to do:

```
aptitude install xserver-xorg-video-intel
```

to get it working properly.  Again, CTRL-ALT-BACKSPACE to restart X.  You could apply this process for your card and see what happens.

---

### Post by heimo on 2007-05-11
> **seoras said:**
>  and I have not found any explanations or solutions to this issue when running the live CD.

One way is to use alternate install CD, and install ubuntu-desktop or kubuntu-desktop package afterwards and fix any driver/resolution/refresh rate issues then, if neccessary. It's command line install as far as I know (haven't used it).

---

### Post by egoldtech on 2007-05-12
> **ianw1974 said:**
> I've just found a similar problem on a HP laptop with an Intel card.  It wouldn't go further than 1280x1024.  But I've subsequently fixed it.  Two things.  First:

```
dpkg-reconfigure xserver-xorg -phigh
```

select the resolutions you want.  Then you'll just need to restart X with CTRL-ALT-BACKSPACE for these to be enabled.

Sometimes this works for most people.  However, on my Intel chipset it was using the xserver-xorg-video-i810 by default.  This didn't have the latest driver available for the 945 chipset, and so I had to do:

```
aptitude install xserver-xorg-video-intel
```

to get it working properly.  Again, CTRL-ALT-BACKSPACE to restart X.  You could apply this process for your card and see what happens.

Hi, I installl ubuntu 7.10 on a Desktop Netvista with Video card Intel 82845 brookdale,  and after installation only was having 640x480 resolution, I have tried EVERYTHING, but this line solved my problem:
aptitude install xserver-xorg-video-intel
thank you very much

---

### Post by fo0b4er on 2007-05-12
Here's a strange coincidence, I also just installed ubuntu on a Netvista with an Intel 845, and I can't change the resolution from 640x480.  I have also tried EVERYTHING, including 915resolution and manually editing xorg.conf, but either it wont change or the xserver crashes.  I know my monitor can support higher resolutions because I also have Windows XP on the computer, and it can run properly at 1024x768.  I just tried installing xserver-xorg-video-intel, and it looked good in gdm, but the xserver crashes when I log in.  Any help would be appreciated! :)

---

### Post by jrcortez on 2007-05-13
> **fo0b4er said:**
> Here's a strange coincidence, I also just installed ubuntu on a Netvista with an Intel 845, and I can't change the resolution from 640x480.  I have also tried EVERYTHING, including 915resolution and manually editing xorg.conf, but either it wont change or the xserver crashes.  I know my monitor can support higher resolutions because I also have Windows XP on the computer, and it can run properly at 1024x768.  I just tried installing xserver-xorg-video-intel, and it looked good in gdm, but the xserver crashes when I log in.  Any help would be appreciated! :)

Same problem here except I just installed UbuntuStudio 7.04 on my Pentium III Sony Vaio.

---

### Post by fo0b4er on 2007-05-13
I don't know if this helps but here is the actual error message i got from the X server by booting into recovery mode and typing "startx":

```
(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112
(EE) intel(0): Unable to read from DVOI2C_E Slave 236
(EE) intel(0): No valid modes.
(EE) Screens(s) found, but none have a usable configuration.

Fatal server error:
no screens fount
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
     after 0 requests (0 known processed) with 0 events remaining.
```

I then typed "dpkg-reconfigure xserver-xorg", and ran through the configuration (and changing the driver from i810 to intel).  After another "startx" everything was perfect, so I rebooted and tried to log in, but the same thing happens!  The xserver crashes just like before!

---

### Post by fo0b4er on 2007-05-13
I found a solution!  Its surprisingly easy!  All I had to do was go back to the old i810 driver, then reboot and go into the BIOS settings (in my case press enter then  F1) and change the amount of shared video memory from 1MB to 8MB!  I got the solution here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel).  All I had to do after that was go to system -> preferences -> screen resolution and set it to my desired resolution (1024x768 ).  Very simple, and no need for 915resolution or experimental drivers! :)

---

### Post by heimo on 2007-05-13
Thank you very much for sharing that solution! And great that you got it working!     :D

---

### Post by jrcortez on 2007-05-14
I tried everything in the thread and nothing worked so I added a basic video card and it fixed the problem. Something was weird about the integrated video card on it. But thanks for all the help. Its appreciated!

---

