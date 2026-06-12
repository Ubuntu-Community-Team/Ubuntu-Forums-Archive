---
title: "Installation Problems"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by rhstott on 2008-02-11
I'm a Windows User new to Ubuntu. Ubuntu ran just fine from the CD. Installing on my hard drive appeared to be successful, but when I restarted there was a black screen and a message right after the boot loader that said unable to process analog input. My video card is an SIS 650_651_740 and my monitor a Dell1905 FP.

I tried the Alternate CD and got an error at about 6% in the installing software section.

I've tried all of the above several times with the same results.

I also have found that the boot loader doesn't respond to my USB keyboad. Had to plug in my old PS 2 keyboad to boot to Windows. Is there a boot loader that I can use with USB? And change the default to Windows?

Thanks for any help!

---

### Post by Partyboi2 on 2008-02-12
With the live cd when you are at the main menu press F4  and try changing the resolution and see if that helps.

---

### Post by rhstott on 2008-02-12
Thanks for the feedback. When I hit F4 nothing happens, so I'm guessing I don't understand when to do it. When running from the CD, the resolution is correct. When should I try the F4 key?

---

### Post by Partyboi2 on 2008-02-12
Sorry I misread what you had written, Try removing the splash and see if you get any further. At the grub menu hightlight the kernel you are booting into and press "e" then highlight the line starting with "Kernel" and press "e" again then change the word splash to nosplash and press "enter" then "b' to boot.
Or you could try using something like vga=791 as a boot option (add it to the line where splash is) more [here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers")

or if that does not work try booting into recovery mode and reconfiguring xserver 
```
sudo dpkg-reconfigure xserver-xorg
```

---

