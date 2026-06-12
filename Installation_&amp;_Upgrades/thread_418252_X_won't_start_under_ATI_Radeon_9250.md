---
title: "X won't start under ATI Radeon 9250"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by ~SkyBlue~ on 2007-04-22
I have ATI Radeon 9250 and tried various drivers. So far I only got away with vesa driver, but I don't like it since it doesn't have any hardware accel. support.

I have tried the normal xserver ATI driver, the screen goes pitch black right after ubuntu loading screen, and system freezes

Also tried fglx 8.28.8 from ati.com (this is the relevant version for Radeon 9250), reconfigured xserver, and this time after a little flickering, an error msg pop-up saying it can't start X.

Here is link to my lspci, dmesg and Xorg.0.log :
[http://www.cse.unsw.edu.au/~gtan/errmsg/lspci](http://www.cse.unsw.edu.au/~gtan/errmsg/lspci)
[http://www.cse.unsw.edu.au/~gtan/errmsg/dmesg](http://www.cse.unsw.edu.au/~gtan/errmsg/dmesg)
[http://www.cse.unsw.edu.au/~gtan/errmsg/Xorg.0.log](http://www.cse.unsw.edu.au/~gtan/errmsg/Xorg.0.log)

Any help will be greatly appreciated

---

### Post by ~SkyBlue~ on 2007-04-22
plz any1 :(

---

### Post by trailnut on 2007-04-22
Same problem on my end. Haven't found a solution yet.

---

### Post by Inspire1997 on 2007-04-22
Same here. Radeon x1600

---

### Post by jonnymccullagh on 2007-04-24
Same here with ATI Radeon x1600. I cannot get 7.04  running the LiveCD. Someone suggested using the Alternate CD so I am going to give that a try.

---

### Post by adi_8079 on 2007-04-24
Same thing here on Ati X600. However under Edgy the 8.28.8 driver works fine.

---

### Post by Unetwork on 2007-04-28
Its very annoying!
I also installed first time, first user the old Ubuntu and the radeon 9250 worked just fine!
Now with the 7.04 all is gone.
I am reading and reading and find thousands of pages all over with people having the same problem!
What ever I tried the only thing I got is a crash of the system.
The resolution is very low and I can't get any rate that I can work with.
read also this: [https://answers.launchpad.net/ubuntu/+question/5281](https://answers.launchpad.net/ubuntu/+question/5281)

I am really surprised that there is no one that can come with a work around after such a time.

---

### Post by dude051 on 2007-04-28
Looking at your logs I can't see any problems. Please post your xorg.conf for reference, it does not look like it is using the fglrx ati drivers. Try using this guide : [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") first using Method1, then Method2 (manual way). You might be forced to use the manual way because you need old drivers for the support, so just replace the install with the old drivers.

---

### Post by Unetwork on 2007-04-28
Hi well that is the problem as you might not know that there is a huge different between the 9250 and the 9500.
So even with all this the Ubuntu will crash doing the  method 1 or 2.
Also in 6.06 and 7.04 there is a different ati will work there but not in 7.04 so far.
[https://answers.launchpad.net/ubuntu/+question/5281](https://answers.launchpad.net/ubuntu/+question/5281)

---

### Post by dude051 on 2007-04-28
Actually support is working for the 9250 series in 7.04, but there are a few differences still. The Xorg ati drivers provide 3D acceleration and work, but fglrx provides direct rendering and no 3D acceleration. Also the new 8.28 drivers do not work in 7.04 because it uses the 2.6.20 kernel. I've found a few threads of the same stuff, try this one for some info,[http://ubuntuforums.org/showthread.php?t=415323&highlight=fglrx+9250]("http://ubuntuforums.org/showthread.php?t=415323&highlight=fglrx+9250")

---

### Post by Unetwork on 2007-04-29
Pity it won't work.
Is there a easy way to go back to to a older version and to un-install Ubuntu so I can have my dual screen again working?

---

### Post by Xera on 2007-08-22
Nevermind, sorry.

---

