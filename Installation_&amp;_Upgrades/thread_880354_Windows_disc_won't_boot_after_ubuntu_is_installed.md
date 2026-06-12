---
title: "Windows disc won't boot after ubuntu is installed"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by dan245dl on 2008-08-04
I removed windows xp to install ubuntu, and all was well until i realized i needed windows. I want to install windows 2000, but whenever i put the disc in, the computer seems to ignore it and go straight to grub. The bios is set to where CD boots in priority to HDD, but even so, it goes straight to ubuntu.

I desperately need windows back for a job i'm doing. If anyone has had this problem and knows of a solution, please please reply.

Thanks again everyone,

Dan

---

### Post by darco on 2008-08-05
Windows needs to be installed  first (windows boot manger preference) then you could install another OS. Your scenario wont work....
Why dont you install  virtualization software,either Virtual Box or VMWare then you can load Windows w/o having to create a partition. Way easier

good luck
dacro

---

### Post by jualin on 2008-08-05
> **dan245dl said:**
> I removed windows xp to install ubuntu, and all was well until i realized i needed windows. I want to install windows 2000, but whenever i put the disc in, the computer seems to ignore it and go straight to grub. The bios is set to where CD boots in priority to HDD, but even so, it goes straight to ubuntu.

I desperately need windows back for a job i'm doing. If anyone has had this problem and knows of a solution, please please reply.

Thanks again everyone,

Dan

Ubuntu doesn't change the BIOS options so your problem is not related with Ubuntu, it's more likely a problem with the BIOS configurations, your Cdrom, or your Windows CD. The person above me suggested Virtualization which works great on Ubuntu. Pretty much it will let you run Windows within Linux. You can install the package "virtualbox-ose" using Synaptic or via terminal > sudo apt-get install virtualbox-ose

---

### Post by jualin on 2008-08-05
> **darco said:**
> Windows needs to be installed  first (windows boot manger preference) then you could install another OS. Your scenario wont work....

good luck
dacro

:KS Windows doesn't need to be installed to install another Operating System. Maybe what you meant was that it's easier to Dual Boot if you have Windows install first instead of installing Windows after Ubuntu is installed.

---

### Post by SkonesMickLoud on 2008-08-05
> **darco said:**
> Windows needs to be installed first

No it doesn't.

Dan:

Can your Windows needs be satisfied by using Wine?

```
sudo aptitude install wine
```

---

### Post by jualin on 2008-08-05
> **SkonesMickLoud said:**
> No it doesn't.

Dan:

Can your Windows needs be satisfied by using Wine?

```
sudo aptitude install wine
```

Check if the application that you want to use can be run by WINE, [here is the website]("http://appdb.winehq.com/"). Wine makes running a Windows Application run almost natively in Linux.

---

### Post by dan245dl on 2008-08-05
Well, the piece of software that i use crashes consistently under wine and has many unusable features.

If my scenario is impossible, does that mean that my computer is pretty much locked into Ubuntu forever?

thanks for all the replies!

---

### Post by coffeecat on 2008-08-05
Let's go back to your first post. You said that the BIOS was set to boot from the CD first, but that the Windows CD won't boot up. Have you tried any other bootable CD, such as the Ubuntu live CD to ensure that the BIOS is working correctly?

If the Ubuntu live CD boots up and the Windows one doesn't, then perhaps the Windows CD is faulty. Have you tried booting the Windows CD in another machine to check whether this is so or not? You don't have to install - just try to boot up.

Or another possibilty if no bootable CD boots up is that the optical drive is failing.

---

### Post by dan245dl on 2008-08-05
The Ubuntu Disc boots, but the windows disc will not. the windows disc boots happily in any other PC. The optical drive functions properly because after it ignores my cd and goes to Ubuntu, the Windows 2000 disc shows up on the desktop.

---

### Post by jualin on 2008-08-06
Can you try another Windows 2000 cd? If everything else fails you can uninstall Ubuntu by using the Ubuntu LiveCD to format the partitions to NTFS (Windows File System) and then trying to install Windows 2000, since Ubuntu wouldn't be there. However I doubt that Ubuntu is causing this, since Ubuntu cannot "choose" what disc you boot from. Good luck!

---

