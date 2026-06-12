---
title: "Unable to recover Ubuntu after 12.04 to 12.10"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by Jaspermid on 2013-07-12
Hi Guys,

I'm having a real challenge with Ubuntu after updrading from 12.04 to 12. 10

What's happening:

1. Screen loads the ubuntu loader (although it turns black quite a bit) and than just goes black and I am unable to do anything.  

Problems

1. USB live boot does not work (do not get the boot menu) I have checked on different computers and USB bootable does work. 
2. I have no connecting to Wifi (and do not have an ethernet connection on my laptop). So I do not seem to be able to get new packages. 
3. Grub> root (hd1, 0) says root command not know. 

I have tried about everything I can and do not seem to be able to get anything to work. I have no problem with a clean new install or deleting everything so long as it works. I am quite a beginner but have tried every solution I can find and hope someone out there could help me out and get my laptop working again. Just getting a network connection from root shell command prompt/grub will also help out. Thank you! (Will try to send some good Karma your way :P) 

Cheers,

Jasper

---

### Post by howefield on 2013-07-12
Were you using proprietary video drivers with 12.04 ?

If it were mine, I'd go for a clean install with 13.04.

---

### Post by Jaspermid on 2013-07-12
Not Sure, Would love to get a clean install but how?

edit: as the usb doesnt boot

---

### Post by kc1di on 2013-07-12
there are a couple things you can try.  Do you have access to another desktop that is connected?
if so go to [this page]("https://help.ubuntu.com/community/Boot-Repair") and download boot-repair and burn it to a cd as instructed on the page.  run that on you Laptop.

do you get any splash screen when trying to run the live usb?

---

### Post by Jaspermid on 2013-07-12
I do not have a CD drive but tried it with USB with BootRepair. Unfortunately my Ubuntu laptop does not load the USB (it does recognize it as I can see a red light from the USB meaning it has power) so the exact same thing happens when just booting up normally. 

Running the live USB does not give anything different than just booted up. It just doesn't seem to load what's on there (used win32 imager to burn the iso's on the USB, USB works fine on other laptops) 

What could I do to get the USB loaded and just get everything off there? Thanks

---

### Post by Jaspermid on 2013-07-12
I;m running a Macbook Air by the way if that helps/

---

### Post by Jaspermid on 2013-07-12
Managed to fix it. My USB boot was not properly set although it worked on other laptops. used UnetBootin on the nw USB boot and managed to fix it. Thanks for the responses.

---

### Post by kc1di on 2013-07-13
> **Jaspermid said:**
> Managed to fix it. My USB boot was not properly set although it worked on other laptops. used UnetBootin on the nw USB boot and managed to fix it. Thanks for the responses.

Glad you got that fixed :)
Now have you got boot repair working and did you get the thing to boot?

---

