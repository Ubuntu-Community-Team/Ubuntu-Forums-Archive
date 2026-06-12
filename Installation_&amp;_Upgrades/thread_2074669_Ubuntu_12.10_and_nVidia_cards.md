---
title: "Ubuntu 12.10 and nVidia cards"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by alain.roger on 2012-10-22
Hi,
I've read several posts about issues installing Ubuntu 12.10 with computers having nVidia cards. But i didn't find any solution...so are we all nVidia owners in trouble ? That would be very bad.

Anyway, i tried with CTRL+ALT+F1 at boot to change settings:
- so i select a language
- changed MODE to OEM manufacturers
- and run ubuntu as a try only.

For now, it seems that monitor still receive signal from video card and i hope i will be able to get something to test.

I will let you know.

A.

---

### Post by alain.roger on 2012-10-22
Ok so nothing work anyway :(

---

### Post by darkod on 2012-10-22
Did you try using the nomodeset parameter?

Here you have details how to do it when trying live mode from the cd, or when booting your hdd installation, depending what you want to do.
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by canadianwriterman on 2012-10-22
Sadly, it's not just Nvidia cards that are a problem. I have Intel HD4000 graphics and am getting a black screen on boot and often a notification that it's going into low graphics mode. I tried purging and then reinstalling LightDM to no avail.

---

### Post by alain.roger on 2012-10-22
> **darkod said:**
> Did you try using the nomodeset parameter?

Here you have details how to do it when trying live mode from the cd, or when booting your hdd installation, depending what you want to do.
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)


thx a lot...it boot like that and i can run Ubuntu...

---

### Post by canadianwriterman on 2012-10-22
And, oddly, the problem does not occur when running the live CD or the installer. It's only after installation that the issue arises.

---

### Post by darkod on 2012-10-22
> **alain.roger said:**
> thx a lot...it boot like that and i can run Ubuntu...

If it boots like that in live mode, you can try installing. But don't forget that on the first boot after the install, you will have to do the procedure to add the nomodeset parameter to the grub options, so that it lets you boot once.
After that usually it's enough to activate the video driver in Additional Drivers.

---

