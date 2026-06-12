---
title: "USB won't boot to installation. (White blinking dash)"
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by DarkSapphire on 2015-03-06
So currently I have bodhi 3.0 installed, but I wanted to try out Utopic Unicorn.  I use unetbootin on my mac to install on my hp mini compaq.  I made sure to download the 32-bit version (1gb RAM).  I also checked the md5, and have used the same usb for 14.04.  The usb is in fat 32.  I made sure to boot to the usb as well.  When I boot, I either get a white blinking dash mark, or it says "Non-system disk, Press any key to reboot."  I'm very puzzled as I have followed everything.  Does anyone have any ideas?

---

### Post by yancek on 2015-03-06
>  "Non-system disk, Press any key to reboot."  

If you have the usb set to first boot priority, the first thing I would check is to see if it boots in another computer to eliminate the possibility that creating a bootable flash failed.  If it doeesn't boot on another computer, then something probably went wrong in the unetbootin creation.

---

### Post by DarkSapphire on 2015-03-06
I know it's not that.  I have tried multiple times, and even re-installed unetbootin.

---

### Post by sudodus on 2015-03-07
Have you tested that the pendrive is good, that it can boot other computers?

What flavour of Utopic are you trying? Standard Ubuntu needs more than 1 GB RAM. I would suggest that you try Lubuntu 14.04.2 LTS (or Utopic). Lubuntu 14.04 has long time support until April 2017, while Utopic is supported for 9 months with end of life in July this year (October + 9 months, 10 + 9 - 12 = 7 --> July)

There is a bug that affects Unetbootin for Utopic depending on the version of the system from where you create the pendrive and the version of Unetbootin.

It might work better to flash the iso file to the pendrive with [mkusb]("https://help.ubuntu.com/community/mkusb") in linux or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows.

If you still have problems, I suspect that it is a driver issue. Then try some [boot options]("https://help.ubuntu.com/community/BootOptions"). You can start with **nomodeset**.

Please specify your computer

- Brand name and model (we know 'HP mini compaq', but not the model 'name and number')
- CPU
- RAM (we know already: 1 GB)
- graphics chip/card
- wifi chip/card

It makes it easier to give relevant advice.

---

### Post by DarkSapphire on 2015-03-17
Sorry I didn't reply fast.  I actually got it installed perfectly.  Just needed to do it one more time.  Thanks anyway.  Sorry I didn't give all the needed info.

---

