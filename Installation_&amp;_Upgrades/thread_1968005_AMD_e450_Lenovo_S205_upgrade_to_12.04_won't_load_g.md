---
title: "AMD e450 Lenovo S205 upgrade to 12.04 won't load gui"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by nitroguy on 2012-04-28
Hey there -

I just updated my Lenovo S205 with AMD e450 APU to 12.04 from 11.10. Upgrade went perfectly, but then on reboot I was greeted with a black screen. 

What I see on boot is "Ubuntu 12.04 LTS *compname* tty1" and it asks me to log in. I do, and I basically am left with a full screen terminal. 

How do I get into the gui? Sorry if it's an obvious answer, I'm a bit new to the Linux game. 

Thanks!!

---

### Post by nitroguy on 2012-04-28
No one?

---

### Post by cheesyking on 2012-04-29
did you have the proprietary ATI drivers installed?

I had this problem and fixed it by reinstalling the drivers from the command line.

If you want to use the latest drivers direct from ATI download them with:

wget [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)

and install with:
sudo sh amd-driver-installer-12-4-x86.x86_64.run

or you should be able to use the drivers that come with 12.04 which you can get through apt (though their exact package names escape me ATM)

BTW, for me the wireless sort of worked out of the box with 12.04 however the driver thought that hardware off switch was on even though it wasn't. The workaround that got me going was (bizarrely) to change the boot order so the "ubuntu" device wasn't at the top of the list.

---

### Post by nitroguy on 2012-04-29
So, it turns out that indeed, cheesyking you are right, in that there was a graphics driver issue. I attempted your method of fix, although it just led to more breakage. The solution I found was to strip out the AMD proprietary drivers, and just use the Ubuntu default (at least, that's what I think happened!). I used:```
aticonfig --uninstall
```

Also, thanks to cheesyking, my wireless works! (although, the speed is a bit spotty still). Simply on boot, press F2, and adjust the boot order to have "ubuntu" below the Hard Drive. Silly fix, but good! (Aren't those the best kind?!)

Thanks! Hope this can help someone in the future!

nitroguy

---

