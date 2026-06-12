---
title: "Switching from Debian to Ubuntu"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by john8547 on 2013-03-24
I burned the Ubuntu .iso file to a blank DVD and rebooted my computer, my boot order has CD/DVD/etc. drive listed to run first. When it boots with the disk in I see my Dell screen then it goes to a black screen with a blinking _ and just stays there.

---

### Post by Bucky Ball on 2013-03-24
*Thread moved to **Installation & Upgrades***

Did you check to make sure disk has no defects? The most reliable way to get the ISO is via torrent. Which release number are you using?

---

### Post by Synoc on 2013-03-24
first thing I need to ask. are you running a 32 bit system and did you download a 64 bit iso? next question is, did you check the md5sum on the iso?

---

### Post by john8547 on 2013-03-24
I went to see if it had no defects and it said there was no partition to perform that operation. Downloaded the 32-bit version of Ubuntu 12.10

---

### Post by oldfred on 2013-03-25
If a really old computer before Pentium or if Pentium M, you can have issues with PAE. Then you need Lubuntu 12.04.

If a newer computer with at least 2+GB of RAM you will do better with the 64bit version.

Often black screen is a video issue. What video card or chip does system have?
Many then work with nomodeset, but some may also need other settings 

       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)


 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by john8547 on 2013-03-26
I had bought this computer from a teacher who refurbrishes them. I think it's an older one, but it has 2 gig ram and Pentium M.
Since I figured it was an older one, I tried Lubuntu 32-bit (downloaded via torrent)  and it was installing but then failed. I checked for errors and there was 1 general error. How do I fix it, or should I go ahead and try 64-bit?

---

### Post by oldfred on 2013-03-26
You need to get a good download. 

With Pentium M you may have PAE issues or no support. 
You have to use Lubuntu or Xubuntu and possibly 12.04 32 bit only. Most newer only work with processors that support PAE.

 PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)


 [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---

### Post by john8547 on 2013-03-27
Now whe I try to install Lubuntu 32-bit 12.04, it freezes in the middle of the installation

I think I'm cursed Dx

---

### Post by oldfred on 2013-03-27
Does it boot in live mode?

---

### Post by john8547 on 2013-03-27
like the 'try libuntu without making changes to your computer'?
I tried that too and it also froze
I also checked for defect and there were none

---

### Post by oldfred on 2013-03-27
Are you installing 12.04 not 12.10?

[http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html)
> Further more, with 12.10, Xubuntu and Lubuntu no longer come with a  non-PAE Linux Kernel, so by default, you can't install any Ubuntu 12.10  flavour on computers using CPUs that lack PAE support (such as Intel  Pentium M).

---

### Post by john8547 on 2013-03-28
bump

---

### Post by oldfred on 2013-03-28
Cannot help with it just froze.

What hardware, perhaps a video issue or other boot parameters?

       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by john8547 on 2013-03-29
See attachment.

---

### Post by oldfred on 2013-03-29
As in post #5, have you tried nomodeset. You add it with f6 on screen you just posted.

---

### Post by Bucky Ball on 2013-03-29
@ john8547: I have deleted the image from your post (#14) and attached it instead. Please refrain from posting large images in the body of the post. Attach them instead by clicking 'Go Advanced' and using the icon there. Thanks. ;)

---

### Post by john8547 on 2013-03-29
I tried nomodeset and it went further but still froze

---

