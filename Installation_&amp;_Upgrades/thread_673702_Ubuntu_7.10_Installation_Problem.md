---
title: "Ubuntu 7.10 Installation Problem"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by sudeep on 2008-01-20
Hi Frnds,

I am trying to install Ubuntu 7.10 on One computer, but once i start booting from CD for starting installation the**[COLOR="Red"] installation hangs with screen showing only colored pixels.[/COLOR]** What can be problem? If problem with graphics card, what is minimum graphics and other hardware requirements for installation??



Regards,
Sudeep
Hare Krishna

---

### Post by Partyboi2 on 2008-01-21
You could try adding a boot option.
at the main screen press F6 and at the end of the line add ```
fb=false
``` and press enter.
If that does not work you can try adding ```
video=vga16:off
``` as  well.

---

### Post by BujarM on 2008-01-21
I want to install Ubuntu as a second OS 
in my Dell Laptop( Vista) which has 65 GB free left.

In the installing process, the partitioning part
Ubuntu 7.10 requires 60 BG for itself.
It is too much!!!

I dont want to give more than 20 GB!!!
How do i solve this problem?

---

### Post by Partyboi2 on 2008-01-21
> **BujarM said:**
> I want to install Ubuntu as a second OS 
in my Dell Laptop( Vista) which has 65 GB free left.

In the installing process, the partitioning part
Ubuntu 7.10 requires 60 BG for itself.
It is too much!!!

I dont want to give more than 20 GB!!!
How do i solve this problem?
Ubuntu does not require 60 gig you can run the desktop version on about 2 gig min, so I would suggest if you have not done so already resize your vista partition with the tool that comes with vista. Then run the ubuntu install and at the partitioning part select manual and create a /swap partition about 2 times the size of the amount of ram you have in your system. So fi you had 1 gig ram you would create a 2gig /swap partition. Then create a /(root) partition  as ext  and mount it as /  with the remaining 20  gig.
So something like this:
Assuming you have 1 gig ram.
/swap 2gig
/(root) 18
 If you are up for alittle more adventure then you could create a /home ext partition as well from the 20 gig. So it would look something like this:
/home 13gig
/swap 2gig
/(root) 5 gig
The advantage of creating a separate home is that if you need to reinstall for any reason you have all your important stuff on another partition meaning you won't lose it all if you were to reinstall.

---

### Post by sudeep on 2008-01-21
Hi PartyBoi2,


I did what u said.But after doing vedio=vga16:off. I got blank screen now instead of colored one...

How to resolve sir?


Regards,
Sudeep

---

### Post by Partyboi2 on 2008-01-22
>  did what u said.But after doing vedio=vga16:eek:ff. I got blank screen now instead of colored one...

How to resolve sir?


Regards,
Sudeep     when you see the coloured pixels are you able to get to a working terminal (Ctrl+Alt+F1-F6) If you can try running 
```
sudo dpkg-reconfigure xserver-xorg
``` Answer all the questions if you are unsure just choose the one that is displayed. When it comes to selecting the video driver choose vesa. Hopefully this will get you to a working desktop where you can install. You may need to do the same thing again after you have installed if it works.
If not try using the alternate cd to install which is a text base installer. You can get it from [here]("http://releases.ubuntu.com/releases/7.10/")
what is your system specs?

---

### Post by sudeep on 2008-01-23
System specs:


Pentium 4, 2.8 GHz, 120 MB RAM

---

### Post by Partyboi2 on 2008-01-23
with only having 128 ram I suggest using the alternate cd and maybe look at installing a light weight desktop like xfce

---

