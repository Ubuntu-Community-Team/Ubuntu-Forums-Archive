---
title: "Xubuntu on an old IBM Thinkpad 600E"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by spaceuser on 2006-11-26
I've seach this forum for help on installing Xubuntu (or on Ubuntu in general) for my old IBM Thinkpad 600E laptop.

I find several that had problem, but I didn't came that far that they did, so I wonder what need to do.

It has an recently updated harddrive, to an 80 GB Hitachi drive (40 GB is for Win 2000 that's already installed). It has only 192 Megs of ram, which is why I selected Xubuntu with Xfce desktop, instead of Gnome or KDE.

I have removed the "quick boot" in BIOS, but it didn't solve anything as expected. I set the keyboard to swedish and the VGA to 1024x768x16 when I pressed F4 and then continue booting the CD, but it just starts for a few second, and then the screen went black and nothing happends thereafter.

Would appreciate any comments on this!

TIA

---

### Post by king20878 on 2006-11-28
Hi spaceuser,

I had a similar problem with my 600e.  You need to use the alternative install CD in text mode.  Check out this post: 
[http://ubuntuforums.org/showthread.php?t=304203&highlight=600e](http://ubuntuforums.org/showthread.php?t=304203&highlight=600e)

Let us know how it goes.

---

### Post by spaceuser on 2006-11-29
Thanks for the suggestion!
The installation seems to have finshed almost well. It said something at last in the install process that it only could find one OS on the disk, Windows 2000, which is correct, and it said also that it should be safe to add GRUB to the hda(0), so I let it. Then the CD went out and the reboot started...

After boot I now receive:
"GRUB Loading stage1.5.

GRUB loading, please wait...
Error 18"

So here I am, late in the evening hoping for a good night sleep, but instead this happends. Any suggestions would be appreciated.

TIA.

---

### Post by spaceuser on 2006-11-30
Solved!!!

I updated the BIOS to 1.16 and now I could boot Xubuntu or Win 2000 if I'd like to.

Next step would be to get the sound to work.

Thanks!

---

### Post by grumpymole on 2006-11-30
spaceuser,

Fixing the sound is not too difficult.  If you search, you will find lots of different sites to help.  You can look [here]("http://grumpymole.blogspot.com/2006/10/thinkpad-600e-sound-problem-still-not.html") or [here]("http://www.mueller.ch.vu/misc/tp600e_en.html").

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by spaceuser on 2006-12-01
Many thanks grumpymole,

I would look into it later today.

---

### Post by king20878 on 2006-12-01
I've also found this post to be very helpful, and it addresses edgy specifically: 

[http://ubuntuforums.org/showthread.php?t=282624&highlight=600e](http://ubuntuforums.org/showthread.php?t=282624&highlight=600e)

---

