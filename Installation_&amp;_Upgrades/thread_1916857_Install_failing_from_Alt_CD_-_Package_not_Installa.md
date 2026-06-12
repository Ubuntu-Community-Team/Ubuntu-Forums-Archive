---
title: "Install failing from Alt CD - Package not Installable"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by Devo420 on 2012-01-28
I had to write it down, because it was during an install. I'm on the livecd now. 
  It says:


  Unmet Dependencies
  xserver-xorg-video-all: Depends on xserver-xorg-video-ati but not installable
  tasksel: aptitude failed (100)
  'pkgsel' failed error code 1


  Does anyone have any tips?


I need to use the alt cd for disk encryption. The normal install CD works fine.

---

### Post by mastablasta on 2012-01-29
are you using fglrx drivers?

---

### Post by grantscheffert on 2012-03-11
I'm getting the same error:
xserver-xorg-video-all: Depends on xserver-xorg-video-ati but not installable

Did you find any solution?

Thanks,
Grant

---

### Post by grantscheffert on 2012-03-11
I found a solution.  I am installing Unbuntu Studio and it turns out that the xserver-xorg-video-ati file was on the install media, but not named correctly.  If I look in the /pool/main/x/xserver-xorg-video-ati folder I saw two files named
    xserver-xorg-video-ati_6.14.99~git20110811.g93fc084-0ubuntu1_.deb

Every other folders had files with a "_i386" at the end of them.  So, I renamed the 2 files in this folder to
    xserver-xorg-video-ati_6.14.99~git20110811.g93fc084-0ubuntu1_i386.deb
and
    xserver-xorg-video-radeon_6.14.99~git20110811.g93fc084-0ubuntu1_i386.deb

After those 2 renames, everything installed without issue.  I am using a USB flash stick for installation, which allowed me to simply rename them.

---

