---
title: "Dell WILL NOT install Ubuntu"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by savaan on 2010-07-11
I've been trying for days now to install Ubuntu on a Dell Dimension 5100 desktop. It's got a 2ghz processor, ATI graphics card and 512 ram. It has a DVD drive that it boots from. Here's the problem.

I have Ubuntu 10 burned on a regular CD and I have Ubuntu 9.1 burned on a DVD. I can boot this Dell up using the CD. It goes through the regular install, gets to 23% then tells me that it can't recognize the CD/DVD device or the hard drive. I've re-seated cables, I know the hardware is all good, this is my media computer that Ive had attached to my TV now for a year. It was running fine 3 days ago before I got the great idea to convert it to Linux.
Now...once that fails I try to put in the burned DVD of version 9. Again the computer boots, I tell it to boot from the DVD...but this time the computer acts as if that drive doesn't even exist. It simply can't find the DVD drive anymore once I put a DVD into it. Is this a problem with the basic reading?? It'll read a CD but not a DVD. If I let it boot all the way to the live Ubuntu CD, the DVD drive is recognized just fine, reads DVDs, etc. 

Is there another solution, something I should be trying? I need this comp on Ubuntu. I've already converted all other systems in my house and this POS is the only abomination still using windows :/

---

### Post by breek on 2010-07-11
if you have an adsl router connected via ethernet you can try [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD"), maybe it works

---

### Post by savaan on 2010-07-11
I'd have to have drivers in place to work the ethernet card in the computer :( This has NO OS in it at the moment

---

### Post by efflandt on 2010-07-11
You say the CD boots to a live system.  Have you tried installing from there instead of during boot?  Some people have trouble installing from the boot menu, but if the live system works from CD try installing it with the desktop icon from there.

---

### Post by savaan on 2010-07-11
Yes, I've tried installing from the live CD desktop. It'll get to about 23% then say that it can't read from the drive/drive is bad/CD is scratched or bad. The drive is good, I'm sure of that. This computer was running Windows just fine 3 days ago and all hardware checked out.

---

### Post by wookieshaver on 2010-07-11
Just as a sidenote, a lot of lazy computer manufacturers placed IDE drives and CD/DVD drives in machine using "cable select" or "cs" as the option for the jumper on the back of the physical drive itself. I would check this option first on the drive and save youself some hairpulling assuming the drive is IDE and not sata of course.

---

### Post by RJARRRPCGP on 2010-07-11
> **savaan said:**
>  It goes through the regular install, gets to 23% then tells me that it can't recognize the CD/DVD device or the hard drive. I've re-seated cables, I know the hardware is all good, this is my media computer that Ive had attached to my TV now for a year. It was running fine 3 days ago before I got the great idea to convert it to Linux.
Now...once that fails I try to put in the burned DVD of version 9. Again the computer boots, I tell it to boot from the DVD...but this time the computer acts as if that drive doesn't even exist. 

Sounds like you need to chuck the optical drive and get another one. Sorry. :(

---

### Post by confused57 on 2010-07-11
It may be that your cd/dvd drive is having problems reading the Ubuntu install disk, I have a friend with a Dell Inspiron 1705, which refused to read any Ubuntu install cd's.  The same computer had no problem booting an Ubuntu installation usb.  You might want to try making one from another computer and set your Dimension 5100 to boot first from usb.  Make a plop boot manager cd, if it's unable to boot first from usb:
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by wilee-nilee on 2010-07-11
> **confused57 said:**
> It may be that your cd/dvd drive is having problems reading the Ubuntu install disk, I have a friend with a Dell Inspiron 1705, which refused to read any Ubuntu install cd's.  The same computer had no problem booting an Ubuntu installation usb.  You might want to try making one from another computer and set your Dimension 5100 to boot first from usb.  Make a plop boot manager cd, if it's unable to boot first from usb:
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Personally I haven't been able to install in this manner the usb install wanted the information from the cd not the usb.

---

### Post by savaan on 2010-07-16
> **wookieshaver said:**
> Just as a sidenote, a lot of lazy computer manufacturers placed IDE drives and CD/DVD drives in machine using "cable select" or "cs" as the option for the jumper on the back of the physical drive itself. I would check this option first on the drive and save youself some hairpulling assuming the drive is IDE and not sata of course.

unfortunately the hard drive is SATA. the dvd and cd drives are both ide

---

### Post by llawwehttam on 2010-07-16
Are you sure the disk isn't a bad download or a bad burn. Try downloading the iso again and burn to disk on a slow setting, I recommend no more than 4x.

If that doesn't work then I would put it down to a hardware issue.

---

### Post by oldfred on 2010-07-16
I would also check BIOS settings. Sometimes they interfere.

---

### Post by mörgæs on 2010-07-16
Try to feed it something else than Ubuntu, for example Slitaz:

[http://www.slitaz.org/](http://www.slitaz.org/)

---

### Post by Pumalite on 2010-07-16
Better yet; try a Knoppix

---

