---
title: "New but with BIG problem!"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by Kingdavid216 on 2007-08-11
Hello, I am new to this forum, just put Ubunutu on today and have run into several problems. I installed it, using the Alt CD, the newest verison of Ubuntu, and it installed and when I re-booted, I got a black screen. I then went into recovery and did startx and i heard the Ubuntu starting up sounds in the background but no image. So I know its something with my graphics card. I then tried to go back into my Vista and I can't even do that! All I see is my booting up image, then , in less than a second a blue screen comes up and then restarts my computer. I can't read what the blue image is cause it goes up so fast. I then went back into Ubuntu, in recovery mode and did "sudo dpkg-reconfigure xserver-xorg" then I did the questions and when it came time for the display config, I Xed what my TV (also my display) can put out and then when i clicked out, it said that,
"xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20070811174535"
then it gives back,
"root@ubuntuDUMA :~#"

I tried using the Vesa hardware option, but the same thing came up. I can't even log-in so I can't instal any program to help with the Nvidia recongition.

What should I do, I'm stuck, and my vista isn't working, and I am on my laptop for now. PLEASE HELP!!!:confused::confused:

Thank you for your help and patience!

---

### Post by Pumalite on 2007-08-11
Let's start from the beginning. Did you do md5sum on iso? Did you check for CD corruption before install? Did you burn at 4x? Also with Vista, you have to partition with Vista partitioner. If all that is OK; then  when you reconfigure xserver, choose most defaults and 'vesa as your driver. That should get you in. Posting your specs would help us help you.

---

### Post by Kingdavid216 on 2007-08-11
I don't know what the md5sum is on the iso. I checked for the defects before installation and it is on a CD not DVD. I burned it at 16x on the cd, when it can go up to about 52x. I didn't use the Vista partioner, it's okay if I loose Vista, yeah I'll be really pissed, but I can always re-install everything. I did the Vesa, and I did the defaults, I am using a 32' Inch Samsung TV as my monitor. I used it for Vista with no problem. I can still use the resolution sizes Ubuntu gave me. I did all of that and I still get the postnit warning sign.

My specs are:

CPU- Intel E6600 
Motherboard- EVGA nforce 680i Sli 
Memory- 4GB (4 sticks) OCZ SLI Ready  
Graphics Card- EVGA 8800 GTS OC'd 
Hard Drive- Samsung 250GB  
Power Supply- 700W OCZ 

Thanks for helping!

---

### Post by Pumalite on 2007-08-11
There are two things that can be a problem: your 32 inch TV as monitor and your 8800 card. Try alternate CD, but even then monitor might continue to be a problem. Do a forum Search on your card.

---

### Post by Kingdavid216 on 2007-08-11
I tried the Alt. CD, because I couldn't even start to install it with the LiveCD.

---

### Post by Kingdavid216 on 2007-08-11
w00! It works!! Thank you so much!!! Oh thankyou!!

---

### Post by ruibernardo on 2007-08-11
Just as a workaround for your graphic driver problem and to be able to run xorg, in the rescue mode do this:

```
 sudo dpkg-reconfigure xserver-xorg 
```and select "**vesa**" as the wanted driver. If it doesn't asks for a driver, try

```
 sudo dpkg-reconfigure xserver-xorg -phigh
```and accept the default even if it is an empty answer, except for the driver one.

Then you can use Xorg/Gnome/Ubuntu to search what causes the problem.

Edit: glad you have solved your problem.

---

