---
title: "Problems after upgrading to Hardy"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by abenitoc on 2008-06-03
Hi, I have just updated yesterday to Hardy using the Update Manager and now I'm facing some problems. First I can't get my wireless to work properly, I have a Broadcom BCM4306 Adapter which I managed to get to work with the old 7.4 version I had. It seems that there is no visible problem, but the network manager doesn't show any networks in range although there are some and I can't connect even with manual connection. 
The second problem I have is that I can't configure any desktop visual effects. When I try to do so it just pops up a window saying "Desktop effects could not be enabled".
Any ideas?

---

### Post by dstew on 2008-06-03
Check in System --> Administration --> Hardware Drivers for restricted drivers. Hopefully you can get a wired internet connection to do this.

---

### Post by abenitoc on 2008-06-03
> Check in System --> Administration --> Hardware Drivers for restricted drivers. Hopefully you can get a wired internet connection to do this. 

I've checked there and I don't have any proprietary drivers in this system. Do I have to download them? How can I install them? Sorry buy I'm new to the Linux way of doing things. Appreciate your help!

---

### Post by dstew on 2008-06-03
Usually, after you install or upgrade, you can get restricted drivers for most of your hardware. You have to be on-line to do this, so that is why I asked if you can get a wired internet connection. Ubuntu is not allowed to distribute the restricted drivers, you have to get them on-line.

Perhaps you only need to configure your wireless, that is, put in the encryption key.

---

### Post by abenitoc on 2008-06-04
I thougt that because ubuntu recognized the adapter I shouldn't need the extra driver, but do you have any ideas of where I can find or look for it? How can I install it? Can I "borrow" it from Windows?

Any solutions for the problems with desktop effects?

---

### Post by vamsibethapudy on 2008-06-04
I had the same problem with wireless.i had upgraded.
but i changed the repositories & there came a notification that hardware drivers are available.
so its working now.
so try changing repositories in software sources.
i tried mirror.optus.net in australia.
keep all checked in third-party software.
hope this helps.
I dont try desktop effects because my RAM is small.

---

### Post by abenitoc on 2008-06-05
Thanks for the advice. I tried to do so but I cannot insert the adress correctly so that the repository you mention is added. Can you get me a little help on that? I'm trying in System>Administration>Software Sources. Is that correct?

---

