---
title: "Install from Hard Drive or other source?"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by Gentist on 2006-12-08
I'm trying to install Ubuntu on one of my desktops. However, it's not working very well. The LiveCD boots without problems, and the installer sort of works. However, I think I might have a semi-faulty CD-ROM drive. The installer freezes at random places when copying files. It's not the install disc, because I've used different ones each time, and they've all been MD5 verified.

Since it does boot the system, and that appears to work long enough to actually get the install process running, is there a way to have the installer copy files from an alternative source, such as the Hard Drive? The idea is that I would copy the iso, or required directories, to the Hard Drive, and have it read the files from there. If my problem indeed lies with the CD-ROM drive, that would fix it.

Also, why isn't the old install method (text-based install) available as an option on the LiveCD? It would probably fix my problem as well, as I recall that one actually gave me a CLI prompt when it failed to do something.

---

### Post by wpshooter on 2006-12-08
You say you did MD5 check.

Did you check the integrity of the CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you run the memtest program ?

Clean your CD drive.

Make sure that your CD drive has the latest & greatest firmware installed.

Are you burning the CDs at 4X or slower ?

Are you going to have any other O/S on this computer other than Ubuntu ?

If not, consider getting the **KILLDISK** program and **WIPE** your hard drive completely clean and then retry the installation.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by K.Mandla on 2006-12-09
> **Gentist said:**
> Also, why isn't the old install method (text-based install) available as an option on the LiveCD? 
I don't know why they're not both on the CD; it's probably a space issue. Have you tried installing from the [alternate CD]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso")? It's the text-based version, and much more reliable than the live CD's installer.

---

### Post by Gentist on 2006-12-09
> **wpshooter said:**
> You say you did MD5 check.

Did you check the integrity of the CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Yes.

> **wpshooter said:**
> 
Have you run the memtest program ?

No, but the CD-ROM drive is the only thing acting up, and Windows XP works 100% fine as far as RAM issues are concerned.

> **wpshooter said:**
> 
Clean your CD drive.

Done that. My guess is that for some reason or another, the installer fails to read files temporarily, and just chokes, instead of actually trying to read it again.

> **wpshooter said:**
> 
Make sure that your CD drive has the latest & greatest firmware installed.

The firmware should be fine as the only time it actually behaves like this is when installing.

> **wpshooter said:**
> 
Are you burning the CDs at 4X or slower ?

Burned several CDs, at various speeds with different burners (4x being one of them). All of the discs are perfectly fine.

> **wpshooter said:**
> 
Are you going to have any other O/S on this computer other than Ubuntu ?

Yes; Windows XP. It's already installed. Need it for the programs that can't run via Wine.

> **wpshooter said:**
> 
If not, consider getting the **KILLDISK** program and **WIPE** your hard drive completely clean and then retry the installation.

If that would actually work, then it's clearly a problem with Ubuntu, seeing as I actually did manage to complete the install once (though I had to wipe it for a few reasons).

I'm going to try the text-based install, as that might actually give me some feedback as to what could be wrong. I understand why the graphical installer suppresses information (most users would find such information confusing), but not having a "debug"/verbose mode is kind of stupid unless the installer is flawless (which it isn't).

---

### Post by Gentist on 2006-12-09
Found this one: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It's exactly what I've been looking for. It can easily be converted for use on a system with no CD-ROM drive, but with USB boot support. Or used to install Ubuntu on a system where the CD-ROM drive is faulty or doesn't work properly (as appears to be the case with my system). It's a shame that it's hidden deep within the help section of the site.

---

