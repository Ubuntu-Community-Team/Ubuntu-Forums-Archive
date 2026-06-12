---
title: "No display/video after Lucid install - nvidia"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by IMNOboist on 2010-05-10
Lucid installed without any errors that I can see of off the main i386 installation CD, but after booting I get no display. Even in recovery mode. The monitor doesn't go into sleep mode and I can tell that the OS is actually running the background because I can do a Ctrl-Alt-Del and do a proper shutdown.

I'm running an nvidia GT 9500.

Everything is working fine on Karmic.

---

### Post by oldfred on 2010-05-10
I had to do this:

boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot

After I installed nvidia driver (default from pop up) then it has worked without issue.

Similar threads with some more info:
[http://ubuntuforums.org/showthread.php?t=1467690](http://ubuntuforums.org/showthread.php?t=1467690)
[http://ubuntuforums.org/showthread.php?t=1471137](http://ubuntuforums.org/showthread.php?t=1471137)

---

### Post by IMNOboist on 2010-05-10
Thank you! That did it!

---

### Post by aceron on 2010-06-25
Hi-

Same issue though I do not get to see grub at all either so I cannot go in and change anything.  Does anyone have a fix in this situation? I have been searching and have not had any luck.

---

### Post by stumay on 2010-06-25
> **aceron said:**
> Hi-

Same issue though I do not get to see grub at all either so I cannot go in and change anything.  Does anyone have a fix in this situation? I have been searching and have not had any luck.


Trying pressing the ESC key right after your BIOS bootscreen prints all it's findings

That's what I had to do to get to GRUB  

the SHIFT Key did not work on my system.

---

