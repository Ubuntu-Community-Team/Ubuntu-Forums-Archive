---
title: "bootable usb install files"
date: 2019-05-08
forum: Installation &amp; Upgrades
---

### Post by acefromspace on 2019-05-08
I have a bootable usb with ubuntu 18.04 on it. I would like to use this. but change it to ubuntu 16.04 (for my own reasons) What files do I need to change? I have a screenshot of files on the usb. How is this different from bootable dvd install files? I also have these files (16.04 ) Mostly I want to learn how this works. I have always used dvd for install, but my drive is shot.

---

### Post by Rubi1200 on 2019-05-08
Why not just download the image for 16.04 and write it to the USB, surely that would be the easiest way?

---

### Post by Forecaster on 2019-05-08
Hi!
Wow, how did you make it - a bootable USB for 16.04 ?
Where to read an instruction about it?

---

### Post by acefromspace on 2019-05-08
I didn't make the bootable usb... my son did. Can't post screenshot (until I upload to photobucket?) I just want to learn how this works. I have the ubuntu install image. Do I just add the autorun files to make it boot from usb?

---

### Post by Rubi1200 on 2019-05-08
Are you currently using Windows as your main operating system?

If yes, go here and download Rufus [https://portableapps.com/apps/utilities/rufus-portable](https://portableapps.com/apps/utilities/rufus-portable)

Double click the file and follow instructions to install.

Once done, open the application and put the USB stick you want to use in the computer (Rufus will detect it automatically).

Then click Select and browse to where you saved the ISO image of 16.04 and add.

Click start.

There might be a warning about syslinux files just click yes and yes to ISO Image (Recommended) and yes to you know it will overwrite any data on the stick.

Then just wait until finished.

Once done you can close Rufus, take out the stick and then you have a bootable Ubuntu to try out.

Depending on whether you have legacy BIOS or UEFI you may need to figure out how to enter and select the option to boot the stick but let's first get you a bootable Ubuntu stick before we take the next steps.

---

### Post by acefromspace on 2019-05-10
I'm using ubuntu 14.04 That's why I need to do fresh install (14 no longer supported) I was going to install 18, but my son is using it and not happy... recommended 16 for now (I don't like upgrades... always do fresh install) I seem to have confused everyone. I just want to know the difference between bootable dvd install and bootable usb install. Seems like a simple question.

---

### Post by Impavidus on 2019-05-10
Not much difference really...

Any dvd burning software makes it easy to burn a .iso file as an image to a dvd, but to burn one to a usb you need the right tool. Those tools have been linked above. When using a usb, there's an option to add persistency. This means that you can save files on the live disk, so that not everything is reset when you reboot. It's somewhat less reliable and I never use it. Usb may boot a bit faster and is not supported on really old computers and the usb can be reused for the next live disk you want to try. Other than that, no differences. Once you booted the live system, installation works exactly the same.

BTW, converting a 18.04 live usb to a 16.04 live usb means replacing nearly all files. Considering that it may (depending on how the live disk was created) have an iso file system, which is read-only, that's no option.

---

### Post by acefromspace on 2019-05-10
OK, I get it. Used ubuntu to create usb startup disc. No problem. I panned on doing dual boot with windows xp (need it to run a canon scanner... it will never see the internet) Used windows xp install and it said I have no hard drive, so I didn't really care and went ahead to install ubuntu 16. Used dvd install (my drive seems to be working now... have had issues before, that's why I needed usb install) It didn't work... just showed text and numbers. Then tried usb and same thing happened. Never had this before on this computer. At this point I'm considering just doing an upgrade... how do I it?

---

### Post by acefromspace on 2019-05-10
I used disk utility (included with ubuntu) and did self-test. It shows OK... 233 bad sectors, but it has always showed that. Forgot to do checksum on downloaded ubuntu install image, but have never had issues before. Will do that anyway. I still don't like upgrades, so insist on fresh install. Why would windows xp install say I have no harddrive?

---

### Post by mailc on 2019-05-12
> **acefromspace said:**
> ........... Why would windows xp install say I have no harddrive?

I don't know about xp.  Actually I don't know about Win 10 either but it usually takes up the entire disk. You have to "shrink" it to free part of the disk . Win 10 will tell you how much you can shrink it. xp may not do that.

---

