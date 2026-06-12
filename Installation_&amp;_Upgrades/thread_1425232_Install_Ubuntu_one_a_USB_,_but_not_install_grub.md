---
title: "Install Ubuntu one a USB , but not install grub?"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by Madmoose on 2010-03-08
Hey y'all, 

This is what I'm imagining, and I've tried to do this before. Yet, I kept having an issue I'll explain below. 

A while back I got the idea to install Ubuntu on a 16GB flash drive. I wanted a little computer I could carry around on my neck, and use on my schools PC's. Well, any PC really. I went out and got the USB flash drive, and got it all installed. What I didn't think about, or know, was that when I made the host computer boot from USB the USB installed grub. Then when I took out the usb, and restarted the computer grub was the MBR. I ended up needing to use supergrub to fix the windows MBR, and I didn't pursue it much more after that. 

Latly, the idea of something like that has been itching at me. I've looked around Google, the forums, and other search engines, but I've not found my answer. Maybe you all can tell me if I installed it wrong, or if there isn't a way to prevent the USB installation from installing Grub when the computer boots from it. 

Thanks all I eagerly await your answers! :P

---

### Post by psusi on 2010-03-08
Umm... unless you tell it to install ubuntu, just running the bootable cd or usb system does not touch the hard drive.

---

### Post by Madmoose on 2010-03-08
Yeah. That's what I thought too, but every computer I tested it on the USB installed GRUB and overwrote the window MBR.

---

### Post by psusi on 2010-03-09
How did you build the USB stick and what version of Ubuntu are you using?

---

### Post by kansasnoob on 2010-03-09
These guides are great:

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

And you do want a persistent "live" usb if you're going to use it on various different hardware!

---

### Post by psusi on 2010-03-09
Or you can just click the USB stick creator option in the menu of the Ubuntu livecd.

---

### Post by Madmoose on 2010-03-09
> **psusi said:**
> How did you build the USB stick and what version of Ubuntu are you using?

Hello again, 

I used a Cruzer Micro 8GB. (I know I said 16GB. My mistake) The guide I used was a guide from [http://www.pendrivelinux.com](http://www.pendrivelinux.com), but for an older disro as it was about two years ago I tried to do this. 

I don't think there was a USB Startup disk creator when I last tried to do this. I'm going to give that a try, and see if it fixes the issue I have. I can't have the USB disk install grub on every computer I use it on. 

Thanks for the info I'll give an update in a bit. :)

---

### Post by psusi on 2010-03-09
System -> Administration -> USB Startup Disk Creator.

---

