---
title: "lilo slpash not working"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by keratos on 2008-03-15
I followed this guide [http://ubuntuforums.org/showthread.php?t=67673&highlight=lilo+howto+boot+splash](http://ubuntuforums.org/showthread.php?t=67673&highlight=lilo+howto+boot+splash)

The splash is not showing. I just get the normal text bootup.

My system appears to use an initrd.img but I am unable to upload this due to its 8MB size.

I managed to "unlock" the initrd.img and eventually got to see the directory layout in the image. There are quite a few dirs and scripts.

I am using xubuntu alternate amd64 ISO installed into an XFS partition.

Other than that, no changes to whatever gets installed from this CD.

A strange issue also, is that after Xorg starts and I log in to a GUI desktop, if I Ctrl-Alt-F1 or other Fs, the console is like 40 columns wide and aboout 20 rows high. The text is massive. I cant use them.

I tried putting vga=x where x was one of 771, 790, 794, 0x31A and so but I just got blank screens until Xorg started. Xorg is fine by the way.

vga=ask identified my settings as 0Fxx something and when I select one the screen switches into the selected mode, but after about one or two seconds, goes back to the "normal" 80x40 or whatever it is, and carries on as a text boot. I never got the splash either.

Wierd

Any ideas folk?

oh, and I did a "lilo -v" as root. No errors.

Help

---

