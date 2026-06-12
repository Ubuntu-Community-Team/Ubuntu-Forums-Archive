---
title: "[SOLVED] 3 Questions"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by Nissan_350Z on 2008-03-26
I have 3 questions :)

1. Ok. once its installed on a computer, can i install windows XP later?


2. How do i find drivers for Ubuntu, like modem and graphics card drivers.
3. Is there a thing i can install to make it compatible with windows things? just curious...

Thanks Sooo much! :) :KS

---

### Post by Rocket2DMn on 2008-03-26
> **Nissan_350Z said:**
> I have 3 questions :)

1. Ok. once its installed on a computer, can i install windows XP later?


2. How do i find drivers for Ubuntu, like modem and graphics card drivers.
3. Is there a thing i can install to make it compatible with windows things? just curious...

Thanks Sooo much! :) :KS

1.  Yes, but it is easier to install XP first so you don't have to reinstall GRUB, since windows will overwrite the MBR.  See [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Either way, you should lay out your partitions before you install either - this means you won't have to deal with resizing partitions when you decide to install the second OS.

2.  Most work out of the box, if you have specific problems with your video card or modem, you can post here on the forums and we will help you get them working.  Some video cards work best with restricted drivers, but these are usually available directly through Ubuntu, it should prompt you if you need them.  Some wireless cards also have trouble, but people around here know how to troubleshoot them.

3.  What do you mean windows things?  Some programs work under [WINE]("http://www.winehq.org/").  The advantage to a dual boot is you can use both systems to their full capacity.  VMs (virtual machines) are also an option using Virtual Box or VMware, though a dual-boot is recommended if you are just starting the plunge into linux/Ubuntu.  You can also mount your windows partition in linux using the ntfs-3g driver which comes built in to Gutsy Gibbon and newer.  You can also access your linux partition from windows using the driver from [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by scragar on 2008-03-26
> 1. Ok. once its installed on a computer, can i install windows XP later?
yes, but windows will assign itself a stupid drive letter in such cases(G drive anyone?)

> 2. How do i find drivers for Ubuntu, like modem and graphics card drivers.
your graphics card will proberly work by default, and if not there are a few other programs to lend a hand, including 1 that's built in.

> 3. Is there a thing i can install to make it compatible with windows things? just curious...wine is a compatabily layer that let's you run most windows applications on linux, although not all will work.

---

### Post by Nissan_350Z on 2008-03-26
> **Rocket2DMn said:**
> 1.  Yes, but it is easier to install XP first so you don't have to reinstall GRUB, since windows will overwrite the MBR.  See [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Either way, you should lay out your partitions before you install either - this means you won't have to deal with resizing partitions when you decide to install the second OS.

2.  Most work out of the box, if you have specific problems with your video card or modem, you can post here on the forums and we will help you get them working.  Some video cards work best with restricted drivers, but these are usually available directly through Ubuntu, it should prompt you if you need them.  Some wireless cards also have trouble, but people around here know how to troubleshoot them.

3.  What do you mean windows things?  Some programs work under [WINE]("http://www.winehq.org/").  The advantage to a dual boot is you can use both systems to their full capacity.  VMs (virtual machines) are also an option using Virtual Box or VMware, though a dual-boot is recommended if you are just starting the plunge into linux/Ubuntu.  You can also mount your windows partition in linux using the ntfs-3g driver which comes built in to Gutsy Gibbon and newer.  You can also access your linux partition from windows using the driver from [http://www.fs-driver.org/](http://www.fs-driver.org/)

I mean, like Windows Games and stuff. like if it will run with .exe programs are therre any addons? lol thanks soo much :D

---

### Post by Nissan_350Z on 2008-03-26
> **scragar said:**
> yes, but windows will assign itself a stupid drive letter in such cases(G drive anyone?)


your graphics card will proberly work by default, and if not there are a few other programs to lend a hand, including 1 that's built in.

wine is a compatabily layer that let's you run most windows applications on linux, although not all will work.

ahh okay, this graphics card is a PCI Video card, hehehe thanks :D

---

### Post by Rocket2DMn on 2008-03-26
> **Nissan_350Z said:**
> I mean, like Windows Games and stuff. like if it will run with .exe programs are therre any addons? lol thanks soo much :D

It just depends on the program.  Some programs work fully, some partially, some not at all.  For video games, you really are best playing them through windows, but some games work under WINE, esp. games that run under Steam (can't speak for all of them, but many popular ones do).
You can look up specific programs at [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by scragar on 2008-03-26
> I mean, like Windows Games and stuff. like if it will run with .exe programs are therre any addons? lol thanks soo much 
windows executables can be run in wine, although not all will run, and some require work arounds.

> ahh okay, this graphics card is a PCI Video card, hehehe thanks
do you happen to know the maker or model of your graphics card?

---

### Post by Nissan_350Z on 2008-03-26
> **scragar said:**
> windows executables can be run in wine, although not all will run, and some require work arounds.


do you happen to know the maker or model of your graphics card?

no, someone else is doing it for me,because they are putting an awesome graphics card in it but, i let them use my CD for it, they told me to ask... so idk, he just asked me to ask you guys if you know of any site with all of the Ubuntu Drivers...

---

### Post by Nissan_350Z on 2008-03-26
> **Rocket2DMn said:**
> It just depends on the program.  Some programs work fully, some partially, some not at all.  For video games, you really are best playing them through windows, but some games work under WINE, esp. games that run under Steam (can't speak for all of them, but many popular ones do).
You can look up specific programs at [http://appdb.winehq.org/](http://appdb.winehq.org/)

ahh okay, thanks soo much :D

---

### Post by scragar on 2008-03-26
depends on the card where it's drivers are installed from.

Envy tackles most peoples Nvidia or ATI cards([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)).

most other graphics cards(although there are few) work with generic drivers or can be installed using standard liunux drivers from the manufactures website.

---

### Post by Nissan_350Z on 2008-03-26
> **scragar said:**
> depends on the card where it's drivers are installed from.

Envy tackles most peoples Nvidia or ATI cards([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)).

most other graphics cards(although there are few) work with generic drivers or can be installed using standard liunux drivers from the manufactures website.

ok thanks :D

---

