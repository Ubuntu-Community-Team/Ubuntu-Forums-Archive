---
title: "install on compaq presario 1800T laptop"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by jrmink on 2007-09-19
Hi everyone

I have a compaq presario 1800T laptop and I have not been able to install ubuntu 7.0.4 fiesty fawn on it. I run the boot disc and get to the gui menu where I can click "start and install" "check cd" etc etc... but when I click start and install the gnome desktop never comes up. 

The screen goes completely white with a tannish outline. Is this a problem with the resolution? 

I have searched for a solution but all I have found is more posts asking this same question. So if someone could please help us out.

I guess the white tannish screen is called a garbaled display?

BTW I can install and run windows xp on it but the ubuntu 7.0.4 fiesty fawn install boot disc just does not work. (Again that damn white screen comes up when the gnome desktop is launched)

JrMINK
__________________

---

### Post by Pumalite on 2007-09-19
[http://tuxmobil.org/compaq.html](http://tuxmobil.org/compaq.html)

128MB of SDRAM, seems to be your problem
With that RAM I would stick to a small distro: Zenwalk, DSL, Puppy.
__________________

---

### Post by jrmink on 2007-09-23
I cant run xubuntu on 128 or 192 mbs of ram?

---

### Post by Pumalite on 2007-09-23
I think it would get installed and run, but if you want a fast system with your RAM install a smaller distro

---

### Post by jrmink on 2007-09-24
Does anyone know of any wireless usb network adapter that will work with the small distros so I can get online..?

---

### Post by Pumalite on 2007-09-24
[http://ubuntuforums.org/showthread.php?t=382214](http://ubuntuforums.org/showthread.php?t=382214)

[http://www.trap17.com/index.php/wireless-configuration-damn-small-linux_t33728.html](http://www.trap17.com/index.php/wireless-configuration-damn-small-linux_t33728.html)

[http://puppylinux.org/wikka/WifiAndPcmcia](http://puppylinux.org/wikka/WifiAndPcmcia)

[http://puppylinux.org/wikka/NdiswrapperPuppy](http://puppylinux.org/wikka/NdiswrapperPuppy)

---

### Post by jrmink on 2007-09-24
Thank you

---

### Post by Pumalite on 2007-09-24
You are welcome. Good luck.

---

### Post by jrmink on 2007-09-27
Ok well since my laptop only has 192 mb of ram I have failed to install ubuntu and fedora and slackware just is not for me.

My last hope was to try xubuntu.

With the text install cd I get to the base install part but it then stops at 77% of the base install and it just doesn't go any further.  The current process it says it's doing is preparing the install report or something along the lines of that.

Im wondering if anyone has a solution for this.  I tried the graphical install of xubuntu and it didn't even work at all.

If  I can't figure this out........I will have to do the unthinkable....and go back to windows for my laptop at least...like windows 98..

---

### Post by Officer Dibble on 2007-09-27
> **jrmink said:**
> 
If  I can't figure this out........I will have to do the unthinkable....and go back to windows for my laptop at least...like windows 98..

I've recently been playing around with a PC with similar specs to yours. Looking at the specs of your laptop I would suggest having a go at Xubuntu Alternate. I had it running on a 300Mhz PC with 128MB RAM and it did quite well. Check it out.... [Xubuntu Alternate]("http://ubuntu-cdimage.datahop.it/xubuntu/releases/7.04/release/")

Only because I am experimenting with different distro's I also received good advice regarding Puppy Linux... that's extremely  good for small systems.

Hope you don't have to go back to Windows. :)

---

### Post by jrmink on 2007-09-27
I know I'm trying my hardest to not go back to windows.  I have a friend that is going to burn another copy of xubuntu alternate.  

Btw I already tried xubuntu alternate and like I said it gets to 77% of the install progress and it just never continues.  Which is why I'm gonna have a friend burn another copy so I can give it another go.  There is also the fact I haven't waited for more than like 30 minutes for the 77% to change and since it says at 77 preparing installation report my only guess is that it is still going on 77 78 79% etc just its not showing it and that when its done it will automatically go to 100% if you know what I mean.

So hopefully I will be able to get xubuntu.

I managed to get slack 12 on it but it was much harder to install packages etc, and I need ndiswrapper to enable my wireless usb adapter so you see I couldnt use slack if I couldnt get my wireless going so I deleted slackware.

*Edit*

[COLOR="DarkRed"]Can someone guide me through partioning my hard drive with the xubuntu text install?

The primary partion can be ext2 right?  Because a friend told me ext2 is faster and more stable.

Also I make my primary partion just " / " right and then make a flag for bootable and thats it?

Plus my swap which is the easy part[/COLOR]

---

### Post by jrmink on 2007-09-27
Nevermind I figured out that the xubuntu alternate cd was corrupt.  

When I use the gui install for xubuntu it does not work on my laptop.

---

### Post by DwightDE on 2007-11-10
I just finished installing Xubuntu 7.10 on a Compaq Presario 1800T.  I used the "safe graphical install", and haven't had any problems.  I think the 1800T needs to run with the basic VESA driver, which must be what is used for the "safe graphical install".

I may have a bit more RAM, but I'm not sure.  Anyway, the basic hardware of the 1800T seems to be fine with it.

I've also installed Ubuntu on this computer, so that will work as well.  (I changed hard drives after installing Ubuntu, and used Xubuntu on the new drive.)

---

