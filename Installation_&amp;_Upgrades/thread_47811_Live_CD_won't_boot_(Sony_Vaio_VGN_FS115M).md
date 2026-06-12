---
title: "Live CD won't boot (Sony Vaio VGN FS115M)"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by LeMarquis on 2005-07-10
I have a problem with booting Ubuntu from the Live-CD on my notebook (Sony Vaio VGN FS-115 M). I'm already overriding PC-Card Detection. 

Hardware detection etcetera is working. But then the screen turns black and the system hangs up (Ctr-Alt-F1 doesn't work), just at the moment the GUI should appear. 

Anybody who has the same problem, and knows what to do about it?

Marquis

---

### Post by boo.spacehamster on 2005-07-22
I have the same problem with my VGN FS115M.

 My system hangs at cardbus detection. It does this when I try to install it as well as with the live CD. I really wanted to install this distro, but toying around with the install options did not help. 

If anyone knows a solution please post it. I'm at a loss what to do, except reinstalling fedora. 

To the thread starter: did you update the firmware to your dvd-rewriter drive, because I read somewhere that their might be the problem. It was reported for some cd-roms and laptops.

---

### Post by matthew on 2005-07-22
Another thought...for my laptop I had to boot using the vga=771 option.

---

### Post by boo.spacehamster on 2005-08-06
the vga option does not work. It is not a display problem, but thanks for the suggestion.

---

### Post by Martin Witte on 2005-08-07
I had something similiar on a Sony Vaio, with a SiS video chipset. Initially I replaced  in /etc/X11/xorg.conf the value for entry "Driver"  in section "Device"  with vesa - this seems to be the most genereic video driver, working with most hardware. Then I downloaded the latest SiS driver from [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml), and installed it.  
Hope this gives you some clues.

---

