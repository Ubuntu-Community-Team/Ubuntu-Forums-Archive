---
title: "[SOLVED] Boot failure: missing boot record"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2007-08-31
At the moment I have FC4 on my 'master' hard disk and I have some windows components on my second hard disk. 
I also have a correct CDROM with an ubuntu iso-image (7.04 desktop).

I unplugged my FC4 hard disk and when I boot from the cdrom I get a message that there is a boot failure cause the computer cannot find the boot record on the cdrom. 
I checked the iso with md5sum and it is correct so why can't I boot?

---

### Post by merlinus on 2007-08-31
Almost certainly a problem with the cd.  Did you burn it as a disk image, at no more than 4x? 

Can you check it on a different computer or cd drive?

-merlin

---

### Post by Ampi on 2007-09-01
I burned it at 8x and I burned it using simply my nautilus browser (I tried different burn programs but I couldn't get them working). So I don't know if I have to do something special with the .iso....
I'll try burning it at lower speed, hopefully then the .iso will be ok....

---

### Post by Pumalite on 2007-09-01
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Ampi on 2007-09-01
Thanks you, but I use fedora so that link doesn't help me.
Anyway I've tried to burn the .iso at spped 2x and still I get a missing boot record. I have not been able to use, K3b, Nero, cdroast and another program that I already forgot the name of. So what I will do is try to burn this .iso with anther computer...
Thanks for the help anyway...

---

### Post by MrUmunhum on 2007-09-01
I see these possible problems with your set up.
  1) You have the boot manager on you master drive which is unplugged?
  2) Does your PC allow booting from a CD?
  3) Does your PC allow booting from the secondary drive?

:)

---

### Post by Ampi on 2007-09-02
That sounds all very plausible. 
In my BIOS I have booting from a CD allowable. But how do I check the other stuff (Q1 and Q3) ??

---

### Post by MrUmunhum on 2007-09-02
A few questions. 
1) In your FC4 system, did you install Grub?  You could then add the Windoze to the boot list. You can not add a CD to the Grub boot list.
2) With the master drive connected, can you boot from a CD? Try another CD that you know   is good.
3) Get into you BIOS and check which drives are supported for booting.

I had the same problem with bootable Ubuntu CD and I had to rebuild the CD. It worked with the second CD.  Try booting you FC4 disk 1 ( Install disk ).  If that works, you have a bad Ubuntu CD.

---

### Post by Ampi on 2007-09-03
I tried another CD which works. So it was a mistake in my CD not in the hard disks. Thanks anyway!

---

