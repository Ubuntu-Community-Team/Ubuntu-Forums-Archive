---
title: "cant boot from cd"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by dzza on 2010-02-28
Hi, tried searching for a solution to my problem but couldn't find one so here goes-

I have ubuntu installed, made a second partition for windows and installed it.  Now I am trying to boot from the live cd so that I can rewrite grub and get a boot menu instead of having it just load windows.

I put the boot cd into the computer, restart, and it says 'press any key to boot from cd.'  I press any key.  It loads windows... 

I disconnected the hard drive to see if the problem was the boot cd.  It was a little slow loading but it booted successfully from the cd with the hd disconnected.

Any suggestions for how to get it to boot from cd with the hd connected?  BIOS options are set to boot from cd first so that's not the issue.

Thanks

---

### Post by sgosnell on 2010-02-28
Try pressing Esc as soon as the BIOS splash comes up.  You should be presented with a choice of which drive to boot from.  Choose the CD.  If that doesn't work, you need to take another look at your BIOS settings.  Some have two choices, one to select the available drives, and another to set the first boot device.  You need to make sure the CD drive is selected as available, and the first device, on the first screen, as well as on the second.  This may not apply to your particular BIOS, but that's the way it is on all my computers.

---

### Post by dzza on 2010-02-28
Thank you, selecting the device from the ESC menu solved the problem.  

Apparently the BIOS did not recognize my cd drive as a cd drive but as some other component, so simply having it boot from the 'cd drive' first didn't work.  

Thanks again.

---

