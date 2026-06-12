---
title: "Upgrade from fiesty to Ubuntu Studio"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Pocadotty on 2007-05-11
I was wondering if there is a way to upgrade my Ubuntu 7.04 to Ubuntu Studio without having to dump my current installation.

I have already added the Ubuntu studio repositories, and I am wondering if there is anything more that I can to then simply installing the Ubuntu Studio apps.

---

### Post by jondecker76 on 2007-05-11
wondering the same thing - though i have added their repos and installed all packages from them - seems to work just fine..

I was just wondering if there were any differences between the official release install and just upgrading feisty.

---

### Post by nevin on 2007-05-11
im thinking that upgrading to ubuntu studio would probably be only installing a new kernal and adding some software... i wouldn't think it would be too much of a problem.

---

### Post by Kobalt on 2007-05-12
You can install the additional packages that UbuntuStudio provides by adding its repos into your sources.list and then from Synaptic.
See this : [http://www.ubuntustudio.com/downlads](http://www.ubuntustudio.com/downlads)

PS: the site is curently down due to the overflow from yesterday's release

---

### Post by .t. on 2007-05-12
Install the ubuntustudio-desktop and the ubuntustudio-audio, ubuntustudio-graphics, ubuntustudio-video, ubuntustudio-audio-plugins packages to fit your needs. Note that ubuntustudio-desktop replaces ubuntu-desktop.

---

### Post by beatgroover on 2007-05-12
> **Kobalt said:**
> 
PS: the site is curently down due to the overflow from yesterday's release

Is there a mirror? I think there's lots of people who'll be wanting to download today. I thought the main site was hosted by Canonical?


.......................................

   [www.ubuntustudio.tv]("http://www.ubuntustudio.tv")

.......................................

---

### Post by Pocadotty on 2007-05-12
thank a bunch .t.!

---

### Post by Pocadotty on 2007-05-12
Everything works for me except the Low Latency kernel, which neads a kernel module for my nVidea card... how do I add that?

I also posted a thread asking that in Desktop Enviroments

---

### Post by jondecker76 on 2007-05-12
look in synaptic for linux-restricted-modules-lowlatency (its named something like that, may even include the kernel version number)
Worked for me

---

### Post by Pocadotty on 2007-05-12
thanks jondecker76... that did the trick

:)

---

### Post by pvcrisp on 2007-05-13
mirrors are at [http://www.ubustu.com/](http://www.ubustu.com/)

---

### Post by hrdriv on 2007-05-16
Ive been trying to upgrade using the advice on the ubuntu studio site, and its getting me nowhere, i can see the packages in synaptic package manager but any time i try to install anything i am informed that there are several dozen packages that are uninstallable.  Is there a way i can install the uninstallable?

---

### Post by Pocadotty on 2007-05-16
You should just be able to click ok on that.

ubuntustudio-desktop is uninstallable because it replaces ubuntu-desktop.  If for some weird reason you cant install the uninstallable, just add the other packages.  Although it is Ubuntustudio-desktop that really contains the system upgrade.

I got that dialog box when i upgraded and I was able to click ok with no problems.

---

### Post by mpgarate on 2007-05-16
same problem, flawless solution. thanks

---

### Post by hrdriv on 2007-05-17
Sorry, no such luck for my predicament.  Im just gonna buy pro-tools.  lol

---

### Post by GeordieDS on 2007-05-17
Does the low latency kernel arrive with the packages? That's the only thing holding me back from maybe starting from scratch with the dvd.

---

