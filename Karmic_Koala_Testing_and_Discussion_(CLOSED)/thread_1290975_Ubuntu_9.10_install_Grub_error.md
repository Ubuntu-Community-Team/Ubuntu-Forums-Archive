---
title: "Ubuntu 9.10 install Grub error"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by su-37 on 2009-10-14
We were installing the beta of Ubuntu 9.10 on one of our computers and when it reached the end of the install the following message came up.
"Grub installation failed. The grub package failed to install into /target/. without the grub the installed system will not boot."
If anyone can provide assistance, much appreciated.

---

### Post by dstew on 2009-10-14
Do you know if it tried to install grub 2, or grub 0.97 (also called grub legacy)? It seems that 9.10 will be using the newly-minted grub 2 program. The manual for grub 2 is [here]("http://grub.enbug.org/Manual"). I was looking it over, and came across this cryptic statement:> Also, when using GRUB 2 after booting from a live CD, notice that /boot may not be especially writable. You must adjust.I don't know what that means exactly. Anyway, it seems that this new grub has the potential to install itself, create its own menu (now in /boot/grub/grub/conf instead of menu.lst). It is clearly a work-in-progress.

If your new installation has the kernel and initrd images in its /boot directory, you might be able to get it going by installing grub legacy from an older Live CD.

---

### Post by su-37 on 2009-10-15
As for what kind of grub it installed im not sure. The error message did just say grub. Keep in mind this is ubuntu 9.10 beta so it could be grub 2 and just not telling me. As far as the directories, the error message said it wont boot. ergo im not sure how i can get to the directory.
Thanks for the reply.

---

### Post by dstew on 2009-10-15
Can you boot a Live CD? Use that to examine the file system on your hard disk.

---

### Post by Niko Johnson on 2009-10-15
you can always install grub from the command line pretty easy.. i dont know how well its going to work with the new ubuntu beta but try this out and see if it does ```
 sudo grub-install 
```
i hope that helps even just a little

---

