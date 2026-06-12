---
title: "gutsy live cd not booting correctly"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Bashed on 2007-11-04
I downloaded official 7.10 and burned the iso as usual. I boot it off the LIVE CD and later, tells me running its running in low graphics mode. I click continue [in low graphics mode], it goes to a blank screen which says "running boot scripts...." and never proceeds further. I tried this again with all usb unplugged from laptop, same problem. What could be the cause?

My video is Nvidia 8400M GT with 256MB 1280x800 widescreen, 4GB memory - Core 2 Duo.

Some illogically suggested running a sudo command off the live cd. I'm no linux expert, but just about 100% sure you cannot sudo anything on a live cd DURING boot process. Makes no sense.

---

### Post by alnhntr29 on 2007-11-04
had a similar problem with gutsy on an intel onboard video. Not sure if this helps you but what I did was to boot using a 6.06 live cd, then upgraded to gutsy through update manager. A long process but in the end it worked, where as the gutsy live cd didnt work at all.

---

### Post by Bashed on 2007-11-04
I tried the new linux distro called Vixta.  Its pretty neat. Curious, where is that scrolling start menu style from in Vixta distro? Is it a KDE or Fedora thing? Or is it a custom Vixta setup?  Anyone here that tried it know by any chance?

---

### Post by Bashed on 2007-11-04
I burned the 6x version of ubuntu and booted off that, SAME error message about my video card. Its a shame that Ubuntu does not support Nvidia 8400M GT video cards (and who knows what other nvidia cards it does not support). Fedora, Vixta, Linux Mint, Opensuse work fine.

---

### Post by saby4237 on 2007-11-04
Have Pentim D dual core processor, 1 GB RAM, NVIDIA Geforce 8400 GS video card... 
  Similar problem as above

---

### Post by Bashed on 2007-11-08
I guess there is no solution?

---

### Post by EspressoRulz on 2007-11-08
Have you tried the 'Alternate' CD image?

---

### Post by Bashed on 2007-11-08
i have, and it failed with an error about writing to grub hd,0 whatever.

---

### Post by perixx on 2007-11-14
Hi TalkJesus --

I've had (or rather still have) the same problem as you, with an ATI X1950GT (really annoying piece of hardware under Linux, that is).

I figured out that my Gutsy LiveCD will not boot at all when I manually choose 1280x1024 16/24k at the bootup. Only booting with 1024x768 will succeed - unless I let it boot itself, then I have a much higher resolution availible (1600x1200). Changing the language will cause the booting to interrupt, leaving me with some booting messages; when I do a manual 'startx' the X-server will start the desktop.

I've tried both Ubuntu 64AMD and Xubuntu 64AMD and it seems the Xfce version is more compatible and less troublesome in my system at the bootup...

Btw, I cannot get Mint 4.0 Live-CD to boot on my system, 3.1 (Celena?) will behave similar to Gutsy's Live-CD, but work so-so.

Maybe booting with 'noapic nolapic' switches will help -- switching off ACPI in the BIOS will not help much. 


perixx

---

### Post by perixx on 2007-12-08
Hello again...

I've stumbled upon some interesting info that might be of concern in regards to this topic:
[http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash+update]("http://ubuntuforums.org/showthread.php?t=581075&highlight=usplash+update")

There might also be a problem with your graphics card outputting the video signal on the wrong (secondary) out connector, like mine does:
[http://ubuntuforums.org/showthread.php?t=633073]("http://ubuntuforums.org/showthread.php?t=633073")

perixx

---

