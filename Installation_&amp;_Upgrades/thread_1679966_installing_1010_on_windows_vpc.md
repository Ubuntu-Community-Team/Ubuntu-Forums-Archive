---
title: "installing 1010 on windows vpc"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by millwab on 2011-02-01
I can install Ubuntu 9.04 on a virtual pc in windows 7 with no problem.
When I try to install version 1010 however, it starts to install and then bombs out without reaching the language selection screen.
Reading one of the forums, I tried the following:
Press escape and then F6
Delete 'quiet splash --' and replace with 'vga=788 noreplace-paravirt'
Try Ubuntu without installing
 
I then get the desktop environment
 
I select the option to install
 
It starts to install the software and I select keyboard layout etc but the installation then stops when about half way through (according to the progress bar)
 
Any help would be greatly appreciated
 
Thanks ..... Brian

---

### Post by razgueado on 2011-02-09
Same here - with this additional weirdness.  

My first attempt got to the language selection screen, I selected English and hit enter.  It then went to a black screen with a flashing underscore prompt and sat there for an hour.  I closed the VPC, choosing the option to "Turn off".

I then deleted the VMCX, the VMC, the VHD...everything I could find remotely related to the VM I'd created.

Created a new VM with the same name, new VHD, captured the ISO as a DVD in settings, started the VMCX.  This time went to a screen with icons at the bottom - a rectangle, equal-sign, and a figure in a circle, sat there for a moment or two, then powered down.  Restarted the VMCX, got to the Ubuntu 10.10 screen with four dots.  After the second dot changed color, powered down.  Restarted again, screen with icons, Ubuntu 10.10, powered down.

So I deleted everything again, made sure it was gone from recycle bin, rebooted computer, repeated the above - same results.  Never gets to the language screen again, just the cycle of attempt to boot and power down.

So I deleted everything and created a new VPC with a DIFFERENT name - same results.

Tried without first capturing the ISO, waited for it to prompt for boot media, then captured the iso.  Same deal.

Mounted the ISO on host with MagicDisk,set VMCX DVD option to access physical drive, selected drive letter for mounted ISO.  Same result.

What puzzles me is that I could never get back to the language screen, even if I delete all the VM files.  It's like something is getting cached in some hidden place.

BTW - all of these were done with dynamically expanding drives.

Next, going to try with a fixed-size VHD.  If that doesn't work, I'll go to 10.4 LTS and see if I have better luck.

Oh, and I'll continue to search the forum for pertinent info while it works...

-RAZ-

---

### Post by razgueado on 2011-02-09
Nevermiiiiiind.  I found the thread about installing 10.4 on VPC and am following that for 10.10.  Confidence is high.

-RAZ-

---

