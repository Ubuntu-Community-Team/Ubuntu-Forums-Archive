---
title: "Telling Ubuntu not to install GRUB on the MBR"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by drexlar on 2006-09-04
Hi
I like Ubuntu very much especially because it uses the GNOME Display Manager. The problem I had is Ubuntu installation does not ask anything about the preferred location of the GRUB (boot manager) and installs it on the Master Boot Record. I do want to install the MBR on the boot sector of the /boot partition. Is there any way to tell the Ubuntu installation where to install GRUB?

Thanks in advance

---

### Post by coffeecat on 2006-09-04
I believe you have to use the alternate install CD to be able to install Grub to a location other than the mbr. The live CD gives you no choice. The alternate CD is a text-based installer.

---

### Post by alecjw on 2006-09-04
Haven't a clue what you guys are talking about but you might want to make it a feature request for the edgy live cd/dvd.

---

### Post by drexlar on 2006-09-04
Thank you **coffeecat**. You are very right. In the page [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/) one can download the version you mentioned, the **alternate install CD**.

By the way, **alecjw** I have heard about the version you mentioned but I could not find it in the Ubuntu web site. 

Thank you guys for your answers
Regards

---

### Post by RKelly5327 on 2006-09-04
Might be one thing I know... go to the Ubuntu home page, click on download, then United States if that's where you are. Way down the page you'll find a heading of Alternate... you can choose the text based on there, the one for PCs.
rk

---

### Post by mattsites on 2006-09-14
With the alternate CD install, will it still install GNOME by default still?

---

### Post by kauf on 2006-09-15
If I am not mistaken Ubuntu uses GNOME while kbuntu uses KDE... so my uneducated answer is yes, the ubuntu alternate cd will install GNOME.

On another note: my main HDD with windows (I have another HDD which I am attemting to install linux on) is f'd... I get some grub error when I try to boot windows.  If I don't get linux running I'll have to repair my windows installation, until then I'm stuck using the dapper live CD.

GOOD TIMES

---

### Post by mattsites on 2006-09-15
So the only difference between the dapper cd and the live cd is the graphical installation?

---

### Post by wkulecz on 2006-09-15
The live CD is different because it boots into a linux system running Gnome with a useful number of applications running from a special CD loopback mount and a RAM disk for storage.  Its useful to have as an emergency repair bootup later.  One of its main apps is the graphical installer.

I prefer Knoppix DVD as an emergency boot disk, but the live CD can be very helpful as it also lets you test your hardware before  the install, with the alternate install you may not find out that a driver is broken for your hardware until after you've installed.

--wally.

---

