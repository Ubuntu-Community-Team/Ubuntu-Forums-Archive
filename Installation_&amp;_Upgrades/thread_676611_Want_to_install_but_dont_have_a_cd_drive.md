---
title: "Want to install but dont have a cd drive"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Aaronought on 2008-01-23
Ok so i acquired a Craptop off a friend, yes it has windows ME on it so its old but for what i want it for its perfect. General web browsing.

Now i would like to install Ubuntu onto it but there are a couple of pretty major problems and im not quite sure its possible.

It has no CD drive. 
No Floppy drive.

its suposed to have a bay thingy but i didnt get it so i havnt got that either.

now ive tried partitioning the HDD on my desktop and putting the contents of the live CD on it and tried to boot from that partition but the laptop just tells me to remove media and restart.

Dose anybody have any suggestion on how i might get it onto it.

From what i know you cant boot from USB.

can i install ubuntu onto the HDD using my PC then just put the HDD back in the laptop or will that cause hardware problems?

im just stuck and really dont know what else to do lol

any suggestions?

Thanks in advance

~A~

---

### Post by stevescripts on 2008-01-23
external cdrom drive?

---

### Post by Rhubarb on 2008-01-23
> can i install ubuntu onto the HDD using my PC then just put the HDD back in the laptop or will that cause hardware problems?
This should work mostly ok for you.
It may have problems starting up Gnome, because the video card is different (this can be easily fixed).

If the laptop has less than 512MB of ram, it may have problems running ubuntu - consider using xubuntu or fluxbuntu.

I have successfully installed ubuntu onto a laptop hard drive in a different computer for several cd-rom-less laptops, all laptops are running ubuntu fine now :D

---

### Post by jfinkels on 2008-01-24
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)

---

### Post by Aaronought on 2008-01-24
> **Rhubarb said:**
> This should work mostly ok for you.
It may have problems starting up Gnome, because the video card is different (this can be easily fixed).

If the laptop has less than 512MB of ram, it may have problems running ubuntu - consider using xubuntu or fluxbuntu.

I have successfully installed ubuntu onto a laptop hard drive in a different computer for several cd-rom-less laptops, all laptops are running ubuntu fine now :D

lol, Oh...

i dont think it has no where near 512mb of ram. Im at college atm so ill have a look when i get home.

xubuntu runs better on lower memory? 

and ill have a quick readup on fluxbuntu 

The laptop did have windows ME on it but it was running like crap but also saying that there was a ton of junk on it.

thanks for all your comments

~A~

---

### Post by Rhubarb on 2008-01-24
You can grab fluxbuntu here:
[http://www.fluxbuntu.org/](http://www.fluxbuntu.org/)

---

### Post by Aaronought on 2008-01-24
Right, 

I've installed Fluxbuntu onto the HDD and once the installation finished i placed it back into my craptop.

I get to what looks like the boot screen (The little stop watch) and the finger get just about half way and it freezes.

it has 64mb of memory =/. is that enough for flux? 

lol what have i done wrong, i installed it onto a 28GB partition of the HDD and gave it 2gb of SWAP because i wernt sure how much to give it, i remember somebody saying that if i give it to much it just dosnt use it.

any suggestions?

---

### Post by Aaronought on 2008-01-25
bump

---

### Post by jfinkels on 2008-01-26
64MB RAM? You'd be best trying out Puppy Linux or Damn Small Linux, perhaps.

[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by ebiladdress on 2008-01-26
> **Rhubarb said:**
> This should work mostly ok for you.
It may have problems starting up Gnome, because the video card is different (this can be easily fixed).

If the laptop has less than 512MB of ram, it may have problems running ubuntu - consider using xubuntu or fluxbuntu.

I have successfully installed ubuntu onto a laptop hard drive in a different computer for several cd-rom-less laptops, all laptops are running ubuntu fine now :D

Is there a link on that video card issue? I'm getting video display issue menu's at the start of the UI install which hault the install.

---

### Post by Rhubarb on 2008-01-28
If you know what video card is in your laptop, then run:
```
sudo dpkg-reconfigure xserver-xorg
```
At the command line (start ubuntu up in recovery mode).
Then just select what **video driver** you want to use, keyboard language, mouse, etc.

---

### Post by Aaronought on 2008-01-28
that is going to be fun as i cant boot into recovery either

---

