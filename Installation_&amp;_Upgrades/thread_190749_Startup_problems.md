---
title: "Startup problems"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by jonttix on 2006-06-06
I had installed both ubuntu and windows, but then I installed kubuntu insteadof ubuntu, and removed ubuntu. How do I change so it starts kubuntu instead of ubuntu in the where I choose what operatingsystem I want to start?

---

### Post by sdalley on 2006-06-06
Was the kubuntu install a clean reinstall on to the same disk partitions as the original ubuntu? That would have obliterated the old version. Even if not, if you went through the full process your grub boot menu should be up to date and bring up the new kubuntu. I have kubuntu too and although it says "Ubuntu" in the boot menu this is just a generic use of the name and the kubuntu variant is what actually come up.

If you do an online dist-upgrade from ubuntu to kubuntu, then there is still only one ubuntu-type system (updated) on your computer, and this is what starts up. Bear in mind that, with the dist-upgrade, unless you explicitly remove stuff, gnome will still be present and probably useable as well, and will even be still the default desktop unless you reconfigure the login screen settings. So just because you still find yourself staring at gnome after boot, it doesn't mean that you haven't got kubuntu now!

---

### Post by jonttix on 2006-06-07
But when I start now I don´t get to KDE or Gnome (I removed Gnome), I only get to the terminal and I don´t know how I manually start KDE, how do I do that?

---

### Post by sdalley on 2006-06-07
Ah, right, so you're already booted, but your graphics are gone. Have you checked whether your packages are in a sane state now, eg what does **sudo apt-get check** give you? Also, **sudo apt-get -f install** is worth a go.

It's possible that you removed too much. **sudo apt-get install kde-desktop** might pull in missing bits.

I experienced a competely blank screen at one point, becuase my nvidia driver had gone missing. Booting to recovery mode and doing sudo apt-get install nvidia-glx fixed things for me, however this may not be relevant for you.

---

### Post by jonttix on 2006-06-07
It is ok now. I had removed too much so I installed kubuntu-desktop and then it worked. Thanx

---

