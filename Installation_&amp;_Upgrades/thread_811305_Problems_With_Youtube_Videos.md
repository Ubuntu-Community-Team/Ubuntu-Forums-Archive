---
title: "Problems With Youtube Videos"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by elmaster84 on 2008-05-29
I've been experiencing problems with the videos on youtube. It seems that the videos start running but after just 5 seconds they start having problems and the images get stuck. Any help on what could the problems be??...If I need to download any lib or something... please help.

---

### Post by krlhc8 on 2008-05-29
Try this:


"I fixed this problem by removing ia32-libs, flashplugin-nonfree and nspluginwrapper, then installing ia32-libs_2.1ubuntu3_amd64.deb from [http://us.archive.ubuntu.com/ubuntu/...e/i/ia32-libs/](http://us.archive.ubuntu.com/ubuntu/...e/i/ia32-libs/) (It is an older version than what installs in apt-get), then installing flashplugin-nonfree. Thanks." 

--Carseneau
[http://ubuntuforums.org/showthread.php?t=659169&page=2](http://ubuntuforums.org/showthread.php?t=659169&page=2)

---

### Post by elmaster84 on 2008-05-31
Thanx for the reply but I actually need detailed instructions step by step on how to perform this changes...thanx again!!:)

---

### Post by krlhc8 on 2008-06-02
Try this URL:
[http://www.dipconsultants.com/debian/](http://www.dipconsultants.com/debian/)

---

### Post by elmaster84 on 2008-06-15
Thanx for the link, I tried using it, but kept saying something like "unable to find the lib", Is there another way you may possibly know???
THANX again....

---

### Post by PmDematagoda on 2008-06-15
Are you using Ubuntu 64-bit?

---

### Post by elmaster84 on 2008-06-15
Nope....Im running Hardy Heron 32-bit. Although I have a Turion 64X2 procesor.

---

### Post by krlhc8 on 2008-06-15
God why?!  That sounds like a waste of a good processor! :)  Did you do that on purpose so you could have less of a headache or what?

---

### Post by elmaster84 on 2008-06-15
As a matter of fact, the 32 bit version was the first one I could download. I installed it and got it to work perfectly. Later on I downloaded the 64 bit version and tried it but I couldnt get anything to work. No wireless, no effects no nothing. So I reinstalled the 32 bit. If its not to much to ask. What adavantages do I gain by using the 64 bit version? And if there is a way I can get it to work easily. I dont have any driver for the 64 bit version.

---

### Post by PmDematagoda on 2008-06-15
Did you install Flash first by executing:-
```
sudo apt-get install flashplugin-nonfree
```
?

---

### Post by elmaster84 on 2008-06-15
yes. I used that code. I also installed some plugins on firefox. Something about flash plugin.

---

