---
title: "Ocelot Upgrade Issues"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by thelowerrhythm on 2011-10-26
During the "Installing" portion of the upgrade I lost power at about 70% completion. Now when I boot the machine, I get a stripped-down version of the login screen with a frozen mouse cursor and a black background. The clock at the top ticks, however everything else appears to be hung.

I'm relatively new to Linux and so I'm not sure how to get the installer going again so that it can right this issue.:confused:

Any and all help is greatly appreciated, although if you know of a fix, I'd recommend giving me the idiot's guide. :)

---

### Post by collisionystm on 2011-10-26
> **thelowerrhythm said:**
> During the "Installing" portion of the upgrade I lost power at about 70% completion. Now when I boot the machine, I get a stripped-down version of the login screen with a frozen mouse cursor and a black background. The clock at the top ticks, however everything else appears to be hung.

I'm relatively new to Linux and so I'm not sure how to get the installer going again so that it can right this issue.:confused:

Any and all help is greatly appreciated, although if you know of a fix, I'd recommend giving me the idiot's guide. :)

It seems like a lot of people are loosing power during these upgrades!! :p

Plug your computer into the internet using a wire, NOT WIRELESS.

Reboot your computer.. immediately after the BIOS screen ( the one that says DELL or HP or ACER ...etc. ) hold the SHIFT KEY. You should be at a grub menu.

Choose system rescue. 

At this next screen, choose fix broken packages.

---

### Post by thelowerrhythm on 2011-10-26
Tried it just now, but there's no rescue option. GRUB only offers:

Ubuntu, with Linux 2.6.38-11-generic
(and also that with recovery mode),

then Previous Linux versions and two Memory tests.

---

### Post by thelowerrhythm on 2011-10-26
I should note that I am considerably more concerned with recovering data on the drive than anything else. Worse case scenario I can always just do a fresh install.

---

### Post by collisionystm on 2011-10-26
> **thelowerrhythm said:**
> I should note that I am considerably more concerned with recovering data on the drive than anything else. Worse case scenario I can always just do a fresh install.

Recovery mode is the one you want.

If you want to just get your data, boot with a live-cd

grab an external usb hard drive

copy your /home folder from your drive onto the usb.

---

### Post by thelowerrhythm on 2011-10-26
Indeed. I can't get a live CD made until I get back home tomorrow evening, so I guess in the meantime I will just try to get the rescue going.

Once I choose recovery mode it asks for my password and then drops me at a command line. Is it a specific command from here that will tell it to attempt to fix the broken packages? I tried looking at the list of commands and nothing seems to fit the bill.

---

### Post by collisionystm on 2011-10-26
> **thelowerrhythm said:**
> Indeed. I can't get a live CD made until I get back home tomorrow evening, so I guess in the meantime I will just try to get the rescue going.

Once I choose recovery mode it asks for my password and then drops me at a command line. Is it a specific command from here that will tell it to attempt to fix the broken packages? I tried looking at the list of commands and nothing seems to fit the bill.

You make it to a command line? Excellent. Plug yourself into the internet. 

Type

```
sudo dpkg --configure -a
```

---

### Post by collisionystm on 2011-10-26
Also try

sudo apt-get install -f

---

### Post by thelowerrhythm on 2011-10-26
Haha, wow... the last few hours... what an adventure.

Long story very short, I have access to my drive again thanks to the fantastic Ocelot CD I was able to get my hands on.

The bad news is that I can't seem to copy anything off the drive because I don't have read permissions for any of the folders I need to snag.

I really am annoyed at myself for being so clueless, but I must ask for further assistance in getting read permissions.... or just whatever will work to let me copy this stuff.

---

### Post by thelowerrhythm on 2011-10-27
Problem solved.

Installed 11.10 side by side with the old installations, reset folder permissions on old home directory to Access for everyone.

whee. thanks!

---

