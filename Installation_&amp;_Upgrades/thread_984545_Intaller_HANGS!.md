---
title: "Intaller HANGS!"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by digitalice on 2008-11-16
Hello, im digitalice.
I own a AMD64 X2 4200+ and 1GB ram, 250 sata HD.
2 days ago, i downloaded intrepid ibex desktop CD to install ubuntu on my PC. When the installation was about to finish 79% (Creating user ...) i got an error MSJ saying that the installer crashed! 
I re burn the ISO at 8X, did the MD5 hash and check the CD integrity and all was fine. I submited the bug to launchpad.
Today, i gave up on trying to install desktop and i downloaded Alternative.
Burned a 8X etc ... i follow the steps on the installation, and at the very end ... while it was installing app and after selecting the package management system, the installation halted because an error.
i re tryed to install it ... but fails.

what im doing wrong?

Im trying to install this on a simple SATA hard drive ... no raid, no nothing.
:confused:

regards,

---

### Post by gilgongo on 2008-11-16
What's the error you getting? Could it be a hard drive fault? Is it a new machine?

---

### Post by wirechief on 2008-11-16
Since you are installing to a Hard drive I am assuming you had no trouble booting up the livecd and actually using it. Is this a "new" hard drive ? (correctly optioned) Have you tried earlier
release's of Ubuntu 8.04 ?

---

### Post by digitalice on 2008-11-16
> **gilgongo said:**
> What's the error you getting? Could it be a hard drive fault? Is it a new machine?


Does not say ... just "installation fail" ... and then, when i try to save the logs, same error!

HD its new!

Regards,

---

### Post by digitalice on 2008-11-16
> **wirechief said:**
> Since you are installing to a Hard drive I am assuming you had no trouble booting up the livecd and actually using it. Is this a "new" hard drive ? (correctly optioned) Have you tried earlier
release's of Ubuntu 8.04 ?

No prob on booting live cd (no extra parameters) ...
and yes, i use to have intalled ubuntu 8.04 64bit on this system.
But i cannot intall 8.04 ... same problem. installer hangs! :confused:

regards

---

### Post by wirechief on 2008-11-16
**
Well, if you have had success with 8.04 64bit on this hd that would eliminate the hd as a problem, I would verify the media again with   md5sum /dev/cdrom   (assuming cdrom is the device and not cdrom1) compare the md5sum with the correct md5 code of the Ubuntu from your download source. I have found that errors
such as what you describe are usually faulty media or just a bad burn, I always burn at 4x and DAO (disk at once) since you did not say what you used to burn the disk, I have used k3b in the past but have been using imgburn under wine  with much better success rate.

---

### Post by digitalice on 2008-11-17
> **wirechief said:**
> **
Well, if you have had success with 8.04 64bit on this hd that would eliminate the hd as a problem, I would verify the media again with   md5sum /dev/cdrom   (assuming cdrom is the device and not cdrom1) compare the md5sum with the correct md5 code of the Ubuntu from your download source. I have found that errors
such as what you describe are usually faulty media or just a bad burn, I always burn at 4x and DAO (disk at once) since you did not say what you used to burn the disk, I have used k3b in the past but have been using imgburn under wine  with much better success rate.

I did it, and CD was ok ...
I said i burned the CD at 8x in my first post of the topic.
MD5sum was also ok.

I used nero 6 to burn the image ... and worked fine! (i guess)

regards

---

