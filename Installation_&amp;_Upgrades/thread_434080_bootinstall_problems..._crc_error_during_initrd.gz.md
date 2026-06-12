---
title: "boot/install problems... crc error during initrd.gz"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by nonlinear on 2007-05-05
can anyone help with a boot problem on a toshiba satelite M50-YK4 (pentium M, 1.75 ghz; 1.5 gb ram, 915gm/gml/910gm express graphix, trying for xp dual boot)? 

Whem i try to boot from the live CD using dedault settings, I get a CRC error/system halt when initrd.gz is loading...  I have spent manyhours testing the iso, cd, and memory and these are all OK.  if I add vga=771, I don't get the error but I hang on a black screen after about the same time period...  and BTW, I can't load the cd check option either (halt at same point), but i did verify M5 checksums and burned several times down to 4x).

However, I am able to use the WUBI installer.  when using this, things proceed OK until the first boot, when I get an error "[xx.xxxxxx] ata1.00: SET of native returned 0, expected xxxxxxxxxx."  If i wait on this error for about 5 miunutes, the installation proceeds and I am able to boot into the desktop and things seem to work.  

I don't even know if these things are related to eachother?

I am hoping that this WUBI install might help me do a real install, but not sure where to begin or what causes the CRC error i'm getting.  can anyone help?

---

### Post by nonlinear on 2007-05-05
OK bit of an update...

i logged back into the WUBI installation and started poking around in the system logs.  it seems that most of my hardwares was properly detected, including my soundcard, intel 915 graphics, etc.

But, there were some notes about my PCI stuff (I saved it all to a file but I can't access it in XP with that WUBI install, i thinik it's stored in an image file).  Anyhow, it said that there was an Intel bridge something or other, and that it was using a workaround or something.  I think it identified the intel as 82801.  But, it didn't seem to really cause any problems in that install.

could this be the problem that is preventing loading of initrd?  any ideas on how to fix this?

thanks

---

