---
title: "grub ignores kbd input"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2006-10-09
I just test installed Ubuntu 6.06 LTS on a Dell Inspiron 8100 using the alternate install.  
I use XOSL as the boot loader, and installed Grub to the partition with Ubuntu installed - /dev/hda2.
W2000 is in /dev/hda1.

I should say first that it works really really nicely - very impressive.  

One item that doesn't work as it should is that the Grub bootloader does not recognize kbd input.  The Grub screen comes up, gives me a number of choices, and says use up or down arrow to select among the choices.  However it ignores the kbd input and just gives me the default (first) option.   Up arrow, down arrow, 'c', 'e' are all ignored.  Not a critical problem for the moment as mostly the default option is what I want, but no doubt one day I will need to be able to select a nondefault.  

It is not a kbd problem:  XOSL, which loads before Grub, recognizes kbd input before it passes control to Grub.  Once I am in Ubuntu, also no problem recognizing the kbd.

I have no external devices attached.  Though I have the same problem if I attach a PS2 mouse.

It is not a random event:  it happened on my 1st test install 2 days ago (for this install I had both the std kbd and a usb kbd attached - grub ignored them both), I then cleared the partitions and reinstalled.

My kbd at install time was set to std US kbd.  

Forum search on "grub keyboard input" gave no hits, even on 'search entire posts'.
The GNU Grub Manual (0.97) gave no hints of relevant config items. 
Google search was similarly unhelpful, though I have to admit I did not read all 27,000 hits.

Any ideas on how to solve this?

thanks

---

