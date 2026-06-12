---
title: "address already in use error on installation"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by KeeperGooble on 2011-07-07
Hi,

I have Windows 7 64 bit currently installed. I tried installing Ubuntu 11, first with wubi, and then dual booting with the image burned to a dvd. However, each time, I got the same error. It got to the purple ubuntu screen and then it said "address already in use 0x??????" (the ? marks are some numbers I don't remember). I've tried looking this up but haven't found anything like it around. Any help would be appreciated.

Thanks.

---

### Post by Rubi1200 on 2011-07-08
Hi and welcome to the forums :-)

This could be caused by a corrupted image, bad burn, faulty CD drive etc.

Try these steps to resolve the problem:

1. post the specifications for the computer

2. check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3. burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

4. if available on your computer, boot with a USB stick after burning to USB with UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Let us know what works or if you need more help.

---

### Post by KeeperGooble on 2011-07-08
Hi, thanks for the response.

1. Specifications:
Windows 7 home premium 64 bit (6.1 build 7601)
Processor : AMD Phenom II X6 1100T Processor, 3.3ghz
8GB Ram
AMD Radeon HD 6950 1.5 GB
Dual asus monitors, one 23" , one 19"

2. Upon checking the md5sum, the ISO I have used has the correct value. ( I used ubuntu-11.04-desktop-amd64.iso )

3. The DVD I burned was at lowest speed.

4. I tried that just now and got the same error:

Address 0xb8fe00 already in use

---

### Post by Rubi1200 on 2011-07-08
Hi,

> The [COLOR=Red]DVD[/COLOR] I burned was at lowest speed.

Perhaps the DVD is the problem. I suggest using a CD.

On the other hand, the fact that you got the same error with the USB stick suggests something else is going on.

Do you have any external devices plugged in such as an iPod, card reader etc.?

Try removing them and then start again to see if the problem persists.

Perhaps a faulty cable somewhere? 

It is worthwhile looking at all the angles.

---

### Post by KeeperGooble on 2011-07-08
I had a few USB devices plugged in : mouse, a Wacom intuos 4 tablet, a printer (Lexmark e232, if it makes a difference). Also had a headset plugged in. I tried unplugging the tablet and the headset but I got the same error.

---

### Post by Rubi1200 on 2011-07-10
I am not sure what to tell you about this.

Two more options to check/consider:

1. faulty memory (perhaps swap the sticks out, clean any dust away etc.)

2. use the Alternate CD and try booting with that instead

Sorry I can't be more specific, but as you pointed out this error does not seem to have a specific cause that we can easily track down.

Hopefully others will contribute with solutions.

Good luck!

---

### Post by KeeperGooble on 2011-07-11
Thank you for your help. I will look into hardware problems, as it seems like the only likely cause at this point.

---

### Post by Rubi1200 on 2011-07-11
You might also want to check that the CD-DVD drive is in good order.

Anyway, hopefully you can find a solution soon.

---

