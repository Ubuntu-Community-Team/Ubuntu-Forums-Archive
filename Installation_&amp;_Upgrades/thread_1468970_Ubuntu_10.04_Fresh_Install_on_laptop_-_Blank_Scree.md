---
title: "Ubuntu 10.04 Fresh Install on laptop - Blank Screen"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by manilaph on 2010-05-01
My laptop:

MSI AMD Athlon 64x2 Nvidia GeForce GO 6100.

I've done a fresh install of Ubuntu 10.04 and I end-up with a blank screen. I've also tried a fresh install of Xubuntu 10.04 and Kubuntu 10.04 and I get the same blank screen.

Ubuntu 9.10 was working perfectly though. So what do you think happened?

I installed the Ubuntu 10.04 livecd on my desktop and it works perfectly so I think it is not a burning problem.

Any workarounds? I really like Ubuntu and will wait for a workaround to be available.

Thank you!

---

### Post by A.S. on 2010-05-08
Same problem here.

But no idea, sorry.

---

### Post by bodildane on 2010-05-08
Try to look at this link:   [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004) Almost at the end of the page the following is written:  
**Intel 8xx X freezes/crashes**

   
 The -intel driver fails with X  freezes or crashes on certain i8xx hardware. The issue is known upstream  but solutions are still under development. For now, to work around the  issue, boot with the -vesa video driver. See [http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](http://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)  for further details.

After a frustrating period with trying and trying I've reinstalled 9.10 and wait until the problem is solved. By the way does anyone know if they announce somewhere when that happens.

---

### Post by Catharsis on 2010-05-08
The OP has nVidia, not Intel, so the i8xx bug doesn't apply. However, this is also in the Release Notes:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

To boot with the "nomodeset" option:
1) Hold down Shift while booting to enter the GRUB menu.
2) Hit 'e' to edit.
3) Add "nomodeset" after "quiet splash".
4) Ctrl+x to boot.

If that fixes it, you can make the change permanent as detailed in the Release Notes.

---

### Post by j.long on 2010-06-20
> **Catharsis said:**
> The OP has nVidia, not Intel, so the i8xx bug doesn't apply. However, this is also in the Release Notes:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

To boot with the "nomodeset" option:
1) Hold down Shift while booting to enter the GRUB menu.
2) Hit 'e' to edit.
3) Add "nomodeset" after "quiet splash".
4) Ctrl+x to boot.

If that fixes it, you can make the change permanent as detailed in the Release Notes.
This worked perfectly for me, thanks (Asus UL50V).

---

### Post by hanciong on 2010-09-19
same for me. I use USB live installer. after I finish install, it tells me to restart. but it doesn't want to enter grub. I just get blank screen. I have to turn off by pushing power button a long time. after that, I turn on again, and everything works fine. what is the problem? my laptop is HP G62 with ATI graphic card.

---

