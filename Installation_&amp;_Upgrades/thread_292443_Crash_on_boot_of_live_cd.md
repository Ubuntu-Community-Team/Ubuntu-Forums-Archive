---
title: "Crash on boot of live cd"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by ToastBusters on 2006-11-03
Hey guys,

I'm trying to install ubuntu on one of my machines here. I am using a cd that I have used to install on multiple machines already, so I know that the cd itself is good. Additionally, I have successfully run Knoppix and installed windows on the machine in question.

What's happening is when it tries to load the live cd environment, it starts to boot up, and when I get to that solid brown screen, just before the gnome desktop would normally appear, it freezes. I'm not getting an error message or anything, it just stops loading. I tried both the 32 bit and 64 bit versions.

My processor is an AMD Athlon64 3400 and my graphics card is geforce 5200. I'm hesitant to point the finger at the graphics card as it was pulled from a different machine that was running ubuntu, but this particular box hasn't ever had linux on it- so we'll see.

Any help would be appreciated. Could it be a driver issue?

Thanks.

[edit]btw, I am trying to install edgy on here, but dapper is having the same problem (except the screen it freezes on is black instead of brown as with dapper)

---

### Post by FewClues on 2006-11-03
> **ToastBusters said:**
> Hey guys,

I'm trying to install ubuntu on one of my machines here. I am using a cd that I have used to install on multiple machines already, so I know that the cd itself is good. Additionally, I have successfully run Knoppix and installed windows on the machine in question.

What's happening is when it tries to load the live cd environment, it starts to boot up, and when I get to that solid brown screen, just before the gnome desktop would normally appear, it freezes. I'm not getting an error message or anything, it just stops loading. I tried both the 32 bit and 64 bit versions.

My processor is an AMD Athlon64 3400 and my graphics card is geforce 5200. I'm hesitant to point the finger at the graphics card as it was pulled from a different machine that was running ubuntu, but this particular box hasn't ever had linux on it- so we'll see.

Any help would be appreciated. Could it be a driver issue?

Thanks.

[edit]btw, I am trying to install edgy on here, but dapper is having the same problem (except the screen it freezes on in black instead of brown with dapper)

I am having similar problems.  I have the same processor but using SIS graphics card. I moved from 5.10 to 6.06LTS using the upgrade command. Everything worked perfectly and I was happy.  I downloaded the ISO for Edgy Eft and my troubles began.  I finally threw up my hands and ordered a copy of the CD from On-Disk - and I have the same problem.

I cannot boot the Live CD for the 64 or 32 bit version.  The Splash screen is a dark black and gray affair.  I get a string of errors for bad pages and then a bunch of Authentication errors and it dies.  Both 32 and 64 bit Live CD's perform the same way.

However I had virtually no trouble installing the 32 bit version after running it live on a Toshiba Laptop.

What has changed in Edgy that I cannot use it on my AMD64 box?

---

### Post by ReaderRat on 2006-11-03
When you reach that point, do a -.CTRL+ALT+F1 to get into Terminal and run 
```
sudo dpkg-reconfigure xserver-xorg
```
You should then be able to configure video.

This is assuming you have at least 256M RAM. If not, try installing Xubuntu.

---

### Post by ToastBusters on 2006-11-03
When I get to that screen, the system is completely non-responsive. I hit that earlier, as soon as the ubuntu logo appears, and I got this error:

> buffer error I/O on device hda logical block 353612

I'm not sure if that error really means anything, but either way, it continued booting, and I hit CTRL+ALT+F1 again as soon as it continued. 

This machine has 2GB of ram, so that wasn't an issue ;). So here's where my results are... after hitting that key combination, it loaded up a terminal, and once again, froze. I am not getting any response from the keyboard whatsoever.

---

### Post by ToastBusters on 2006-11-04
Okay, I managed to get ubuntu installed using the alternate install cd. It still failed to boot up, so I ran sudo dpkg-reconfigure xserver-xorg. Now, when I boot up, I get a solid black screen with a curser in the upper left corner, with no activity, and of course, absolutely non-responsive.

Any further help would be appreciated.

---

### Post by ToastBusters on 2006-11-04
Since I'm not having much luck getting help, I tried installing the nvidia drivers, and now it's actually getting the login screen before crashing.

---

