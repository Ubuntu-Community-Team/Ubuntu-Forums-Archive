---
title: "graphics card problem"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by siriusblack711 on 2007-10-24
just installed a new graphics card on my comp.geforce 8600 gt.works perfectly on windows.but ubuntu seems to show no screen output.i was using an ati onboard graphics card before.
also how do i get teh original windows mbr instead of grub?is there any way apart from a reinstall of ubuntu?

---

### Post by forestpixie on 2007-10-24
try booting to the recovery for Ubuntu and reconfiguring x

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

answer the questions and you should at least get in and be able to get the restricted driver, laternatively once you're back in try [envy]("http://albertomilone.com/nvidia_scripts1.html")


If you reinstall the win mbr you won't be able to boot ubuntu are you sure that's what you want ;) 

To do so use the win disc, boot with it and choose repair, then fixboot and fixmbr and reboot.

---

### Post by siriusblack711 on 2007-10-24
is there any way to do it without the windows cd?

---

### Post by forestpixie on 2007-10-24
found these two but there's more try searching google I did :)

[http://forums.techguy.org/windows-nt-2000-xp/470476-restore-windows-mbr-without-recovery.html](http://forums.techguy.org/windows-nt-2000-xp/470476-restore-windows-mbr-without-recovery.html)

[http://forums.techguy.org/windows-nt-2000-xp/620626-how-fixing-mbr-without-using.html](http://forums.techguy.org/windows-nt-2000-xp/620626-how-fixing-mbr-without-using.html)

---

### Post by PmDematagoda on 2007-10-24
Your issue concerning the VGA card does not necessitate a reinstall, and if even if you did want it, you can just reinstall Ubuntu on top of the old installation without problems.

---

### Post by siriusblack711 on 2007-10-24
when i tried the sudo command in recovery terminal it only asked which resolution i wanted the x server to be shown in?then a ok button.didn't work. also how do you restart or shut down once in the recovery terminal?tired of hard reboots(yeah i'm a noobie)

---

### Post by siriusblack711 on 2007-10-24
thanks guys for such prompt replies.really appreciate.maybe reinstall.

---

### Post by siriusblack711 on 2007-10-24
thanks guys for such prompt replies.really appreciate.maybe reinstall.

---

### Post by knitmom on 2007-10-24
I was able to do this (see code below) and fix my problem.  I did this from the prompt in linux once it tried to load and failed.  If you can't remember what your video card is, reboot and load windows and then check your video card properties.  Mine happened to be a VIA/S3G type of card.  It worked when I used VIA in ubuntu after using the code below. ....now to solve the networking problem.....

> **forestpixie said:**
> try booting to the recovery for Ubuntu and reconfiguring x

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

answer the questions and you should at least get in and be able to get the restricted driver, laternatively once you're back in try [envy]("http://albertomilone.com/nvidia_scripts1.html")


If you reinstall the win mbr you won't be able to boot ubuntu are you sure that's what you want ;) 

To do so use the win disc, boot with it and choose repair, then fixboot and fixmbr and reboot.

---

### Post by PmDematagoda on 2007-10-24
You will have to change settings in the x-server, do:-

```
sudo dpkg-reconfigure xserver-xorg
```

and select the driver as Nvidia, and just accept the other default choices and move on.

But before you do that, I believe you should install the driver for Nvidia. Go to the Nvidia website and download the Linux driver, the installation instructions are given in the web site.

After installing, then do the first instruction.

Then try "startx" and see if that succeeds.

If you wish to reboot, just type in "reboot".

---

### Post by knitmom on 2007-10-24
I got two screens, the first asked the video type, the second asked for the resolution. Could you have hit enter twice?

---

### Post by siriusblack711 on 2007-10-24
how do i install the linux driver in ubuntu when i can't even get into it?

---

### Post by PmDematagoda on 2007-10-24
Download it to the root Desktop, or you can navigate through the CLI to reach it. Do you have any working OS at all?

---

### Post by siriusblack711 on 2007-10-24
thanks everybody.PmDematagoda really saved my ***.the reconfigure command worked.pretty cool seeing the desktop effects on an nvidia card.(had ati earlier hence no desktop effects)

---

### Post by PmDematagoda on 2007-10-24
Nice to hear that you got it to work. Hope you are enjoying the desktop effects :).

---

