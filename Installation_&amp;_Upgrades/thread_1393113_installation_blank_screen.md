---
title: "installation blank screen"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by virkar on 2010-01-28
I'm currently trying to install ubuntu 9.1 on my gateway nv79. I have windows 7 on the machine already and trying to install a dual boot ubuntu. After booting from cd and getting the language screen I entered install ubuntu then the screen goes black. I waited 10 min and the display is still black and doesn't show anything except i can see my hard drive is being read and the cd is also being read. I can't seem to be able to see anything. I decided to download ubuntu 9.0.4 and it works and I can install it correctly but for some reason I can't seem to install 9.1 version. 

Is it something to do with my display? or do i have a bad version of 9.1? I would really like to not use windows if i can get the newest version of ubuntu to work correctly.

---

### Post by SusieSA on 2010-01-29
Hi Virkar

I'm experiencing a similar problem to you and I haven't resolved it... yet.  I did find many other posts with similar problems but haven't found the solutioin yet.

Can you have a look at my post:
[http://ubuntuforums.org/showthread.php?t=1392813](http://ubuntuforums.org/showthread.php?t=1392813)

Even though I haven't found a problem, I've ran a couple of commands, that I found on other postings, which help other readers understand what's happening on boot etc.  Perhaps if you run these commands and post the output, helpers may have more information and be able to understand your problem

---

### Post by presence1960 on 2010-01-29
> **virkar said:**
> I'm currently trying to install ubuntu 9.1 on my gateway nv79. I have windows 7 on the machine already and trying to install a dual boot ubuntu. After booting from cd and getting the language screen I entered install ubuntu then the screen goes black. I waited 10 min and the display is still black and doesn't show anything except i can see my hard drive is being read and the cd is also being read. I can't seem to be able to see anything. I decided to download ubuntu 9.0.4 and it works and I can install it correctly but for some reason I can't seem to install 9.1 version. 

Is it something to do with my display? or do i have a bad version of 9.1? I would really like to not use windows if i can get the newest version of ubuntu to work correctly.

Let's revisit back to the beginning. Did you [MD5SUM ]("https://help.ubuntu.com/community/HowToMD5SUM")the iso you downloaded?
All characters must match exactly or the iso is corrupted.

If the MD5SUM checked out did you burn the iso as an image at a slow speed (4x-8x is perfect)?

When you boot the CD did you select "check disk for errors"? If even 1 file is found to have an error you cannot assume the disk will work as it should. Burn another disk.

You now have a good disk. At the boot menu hit F4 and choose safe graphics mode. For more info on this and other boot options see: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

As a last resort you may have to use the alternate text based installer. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by lpstevens on 2010-04-24
Thanks for the tip.  Ubuntu 9.10 is now installing on my new gateway nv79 laptop.

---

### Post by brucekev on 2010-05-04
The new 10.4 installation works great on the NV79. I'm glad they got it fixed! ;-)

---

