---
title: "problems with CD install"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by Christopher Newtoit on 2012-01-13
Hello all,

I am having trouble installing ubuntu into a 64 e machine tower I just got.  The tower is running Windows 7 no problem.  However when I burned the ISO image (and checked it, disc is good) and re started to boot from CD I get the Ubuntu logo with the Dots changing from red to white as it loads and then I get this strange screen that looks like a giant pixelated staircase.  It freezes here and I can't get past it.  This happens trying to install with both 64 bit and 32 bit discs.


I am running the monitor off of a graphic card if that helps. 

Thanks in advance.

---

### Post by Christopher Newtoit on 2012-01-14
alright my new approach is try a text install, and I am thinking of checking out Kubuntu this time-I think it might be my graphics card.  Any help still much appreciated.

---

### Post by Christopher Newtoit on 2012-01-14
OK.....got a little bit further with the text install attempt.  I got as far as setting up the internet connection and then.....nothing, nothing at all. An empty blue screen that I could type into with no response.

Also I feel it is worth mentioning-  I have am EVGA GEFORCE GT240 graphics card running the monitor through the VGA out (it also has HDMI out I think).   I feel like this has something to with it all. 

Help me out!  AHHHHHH windows.  I haven't used it in years. Now I've got this new tower....

---

### Post by mikewhatever on 2012-01-14
Try the 'nomodeset' parameter from advanced options. To get to them, hit any key as soon as you see the purple background after the BIOS screen. That should interrupt the boot process and present a menu. Hitting f6 should bring up the advanced options.

---

### Post by Christopher Newtoit on 2012-01-14
I'll give it a shot, thanks.

---

### Post by Christopher Newtoit on 2012-01-14
MikeWhatever,

Thanks, that got me a bit further. However after the install now and attempt to boot up into Kubuntu I have gotten to a blank screen.   Any other ideas? I seem to remember reading something about the noacpi option, maybe I'll try that also.

---

### Post by mikewhatever on 2012-01-14
You can apply the same workaround on an installed system, though it's a bit harder, but doable.

Hold a shift key right after the BIOS screen. You should see the bootloader screen with several lines, find the kernel line that looks something like this:

> linux   /boot/vmlinuz-XXXX-generic root=UUID=XXXXXX ro   quiet splash

press 'e' to edit, and append 'nomodeset=1' without the quotes to it. Press 'ctrl+b' to boot. If that works, you should probably install the proprietary Nvidia driver right away.

---

### Post by Christopher Newtoit on 2012-01-14
hey thanks, I was able to get into ubuntu 10.04 finally.....now I can get on so far so good, but if you have any ideas about directing me towards activating/finding drivers for a Nvidia graphics card....The system fails to retrieve the packages every time.

---

### Post by mikewhatever on 2012-01-15
Make sure it's connected to the internet.

---

### Post by Christopher Newtoit on 2012-01-15
it is defnetly connected. I'll mark this thread solved, tho, and begin a new one for new issues. Thanks very much for your help.

---

