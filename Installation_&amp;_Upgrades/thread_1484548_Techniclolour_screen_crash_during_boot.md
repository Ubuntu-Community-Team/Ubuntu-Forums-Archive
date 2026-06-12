---
title: "Techniclolour screen crash during boot"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by lurgee on 2010-05-15
Last night I switched from Lucid Ubuntu to Lucid Xubuntu.  Whenever I  switch on, I get a flash of several error messages on the boot screen;  then few seconds when the screen turns all the colours of the rainbow,  as if the display was damaged.  Then it loads normally and seems fine.

This happened occasionally under Lucid Ubuntu, but  don't recall it  happening when I was using Karmic Ubuntu.

It doesn't exactly fill me with confidence, and might even goad me to  dig out my old Karmic boot disc.  Say it ain't so!

My laptop is an eMachines (acer) E625.  But I doubt it is related to the  hardware.

Suggestions / instructions in the most simple language, please. Thanks  from a newbie.

---

### Post by lurgee on 2010-05-17
I've had a look around and noticed there are some similarities between what is happening on my laptop and the bootup/plymouth issues relating to nVidia graphics ... but my eMachines E625 uses a ATI Raedeon Xpress  1200 graphics card.  But I am getting the black screen with a flashing cursor, then the momentary techniclour screen crash described above, before the log in screen and pretty backdrop appears as normal.  

Has anyone else experienced this with non-nVidia graphics and is it likely the fix suggested for the nVidia issue will work?

---

### Post by lurgee on 2010-05-17
Looks like I've managed to solve this after bumbling about on the forums and reading stuff.  Amazing what you find when you google "plymnouth raedeon."  In this case, I found this thread on the forum: [http://ubuntuforums.org/showthread.php?t=1448346](http://ubuntuforums.org/showthread.php?t=1448346)

And it suggested I do this:
> 
sudo apt-get install plymouth-theme*
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u 

And it seems to have worked.

---

### Post by glitch323 on 2010-09-15
> **lurgee said:**
> Looks like I've managed to solve this after bumbling about on the forums and reading stuff.  Amazing what you find when you google "plymnouth raedeon."  In this case, I found this thread on the forum: [http://ubuntuforums.org/showthread.php?t=1448346](http://ubuntuforums.org/showthread.php?t=1448346)

And it suggested I do this:

And it seems to have worked.
I know this thread is a few months old, but I wanted to thank you Lurgee for posting this.  I have been going crazy trying to figure out why I had a large rainbow across my screen, but mine would freeze that way on every boot.  I found a quick way around it by changing the /etc/default/grub file to have "nomodeset" after the "quiet splash", but when I would shut down, I would see that rainbow again.  I am running 10.04 on a Dell Latitude 131L, which has an AMD Sempron processor and an ATI Xpress 1150 video card.  Anyways, thanks again! :D

---

