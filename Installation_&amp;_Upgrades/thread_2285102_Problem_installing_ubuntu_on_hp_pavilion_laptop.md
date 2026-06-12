---
title: "Problem installing ubuntu on hp pavilion laptop"
date: 2015-07-03
forum: Installation &amp; Upgrades
---

### Post by vik10 on 2015-07-03
Hopefully someone can help me?
I am trying to install ubuntu 15.04 32bit onto my hp pavilion dv6000 laptop. It appears to install OK but when I log in it works fine for about 1 minute if that and then freezes - no touch pad,  keyboard all frozen. Help!

Spec:
HP Pavilion dv600 entertainment pc
amd 64x2 turion tl-60 2.00GHz
nvidia graphics
2.00GB RAM
200GB hard drive

I deleted Windows Vista home premium SP2, 32 bit OS

---

### Post by Vladlenin5000 on 2015-07-03
Hi and welcome.

1. You can and probably should install a 64-bit version.
2. You need proprietary nvidia drivers for optimal performance. System Settings > Software & Updates >> Find the rightmost tab, Additional drivers, and select the recommended proprietary driver.

---

### Post by kerry_s on 2015-07-03
you need to go lighter, ubuntu-mate or xubuntu

2gb ram is your bottle neck, install zram-config to maximize your ram & run additional drivers for you nv card drivers.

---

### Post by vik10 on 2015-07-03
Thanks for the feedback. I have just tried ubuntu v14.04.02 lts and the same happens. Everything just freezes.
OK. I will try a lighter version next. See what happens.
Not sure how to install graphics drivers when the keypad does not work?

---

### Post by vik10 on 2015-07-03
xubuntu did not work. The screen did a lovely stripe effect all over while trying to do the install and i had to abort. As I did not take a copy of windows Vista (I know...) I need to see if I can download a copy.
Not giving up on ubuntu yet - I think I need to find and install the graphics drivers first, once I have vista back up and running. Unless anyone else has a better idea?

---

### Post by ubfan1 on 2015-07-03
Initially, you need to boot with the "nomodeset" option on the kernel line (you can edit it from the grub command line "c" at grub menu, put it next to the "quiet splash" words. Instructions are at the bottom of the grub page.)  Then run the software updater, select the additional drivers tab, and select the nvidia-current.  reboot, and you should have the nvidia driver instead of the nouveau or vga (check with the lsmod command to see if nvidia is present.)  Definitely avoid the standard Ubuntu with the unity desktop, that's too much for your machine.

---

### Post by kerry_s on 2015-07-03
just googled your model, yours requires some tinkering to get up & running.

[https://www.google.com/search?q=pavilion%20dv6000&gws_rd=ssl#safe=off&q=pavilion+dv6000+xubuntu](https://www.google.com/search?q=pavilion%20dv6000&gws_rd=ssl#safe=off&q=pavilion+dv6000+xubuntu)

just read up.

---

### Post by vik10 on 2015-07-05
OK. Latest update on this.
In desperation I loaded a very old copy of windows xp! Reformatted the whole hard drive. 
Then after installing this windows xp worked fine but it's xp!
So I reinstalled xubuntu planning on doing the changes that you have advised.
To my surprise everything now works... The graphics are fine. In fact I am very happy :). Just not sure what I have done to get it WORKING? 
In the additional drivers menu I noticed that it is using the nvidia x.org server-nouveau display driver.
Can anyone tell me why this now works as it did not before?

Thank you for all your help.
Vikki

---

