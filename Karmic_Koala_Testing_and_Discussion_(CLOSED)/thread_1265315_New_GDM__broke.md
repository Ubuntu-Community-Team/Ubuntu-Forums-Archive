---
title: "New GDM  broke ?"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2009-09-13
Just did dist-upgrade and the Sep 12 GDM crashes.
Anybody else have this problem ? How can I fix it ?

---

### Post by Funnnny on 2009-09-13
lol, just crashed and I thought about asking it here :D
How about reinstall gdm, I've just boot to my windows box and doing my works here before playing around with the problem

---

### Post by cecilpierce on 2009-09-13
Well Funnnny I guess we are the only ones with this problem. I tried everything I know (which is not much) and still back screen, no mouse, no keyboard.

---

### Post by VMC on 2009-09-13
> **cecilpierce said:**
> Just did dist-upgrade and the Sep 12 GDM crashes.
Anybody else have this problem ? How can I fix it ?

When you say crashed, what happens afterwards. What are you left with. Does it reboot or are you put into a busybox?

---

### Post by orlox on 2009-09-13
I can't get to GDM either with the recent updates, though, I can't see xsplash either. Switching the video driver to nv instead of nvidia allows me to use my computer though...

---

### Post by cecilpierce on 2009-09-13
VMC it boots and I get the usplash then black screen then dead,no mouse, no keyboard and if I hit the start button it shuts the computer off. I do have karmic on another partiton that has not been updated yet and it works fine. 
Thanks, Cec

---

### Post by alligoodw on 2009-09-13
After updating this morning, I get up to the Nvidia splash screen.  After that, there are a couple of flashes and then nothing.  I have a cursor at the top left corner of the screen with no GUI.  It just stays there until I reboot the system. After rebooting I get the same problem over and over again.

---

### Post by kansasnoob on 2009-09-13
I had problems too, so I installed kdm which also pulls in some dependencies:

> exiv2 (0.18.2-1)
kde-icons-oxygen (4:4.3.1-0ubuntu1)
kdebase-runtime (4:4.3.1-0ubuntu1)
kdebase-runtime-bin-kde4 (4:4.3.1-0ubuntu1)
kdebase-runtime-data (4:4.3.1-0ubuntu1)
kdebase-runtime-data-common (4:4.3.1-0ubuntu1)
kdebase-workspace-kgreet-plugins (4:4.3.1-0ubuntu3)
kdebase-workspace-libs4+5 (4:4.3.1-0ubuntu3)
kdelibs-bin (4:4.3.1-0ubuntu2)
kdelibs5 (4:4.3.1-0ubuntu2)
kdelibs5-data (4:4.3.1-0ubuntu2)
kdm (4:4.3.1-0ubuntu3)
khelpcenter4 (4:4.3.1-0ubuntu1)
libclucene0ldbl (0.9.20-3)
libexiv2-5 (0.18.2-1)

And the installation does NOT complete normally with the question asking whether you want to use gdm or kdm, the terminal just sits forever saying that it's running some post-installation trigger or some such, but it did work for me and kdm allows to select different session whereas that option hasn't been present in gdm.

I also can't pull up a gui for kdm, but it doesn't really matter to me at this point.

Oh, and I'd also swear that boot time is somewhat better using kdm. Don't know why though.

---

