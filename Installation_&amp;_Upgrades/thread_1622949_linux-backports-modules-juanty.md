---
title: "linux-backports-modules-juanty"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by ubichinon on 2010-11-16
Hey all!

I managed to completely break my ubuntu jaunty install on a hp pavillion dv3. The problems I am having are of course down to bloody hardware drivers, a neverending story in ubuntu.

so I am stuck at the following point:

My laptop has a ATHEROS AR9285 802.11 b/g Wifi Adapter in place as well as a REALTEK  RTL 8102E/8103E Famiily PCI-E FASTETHERNET NIS card.  I am now trying for days to get this working but neither the drivers I find on the realtek webpage nor the compat-wireless download seem to do the trick, in fact the drivers supplied do not compile smoothly (regardless which version of driver I am using and trust me I have tried ALL driver I could find their webpage) but apparently I missed one bit. 

The bit: you are explicitly told to checkout  linux-backports-modules-jaunty to resolve these issues!! SO I tried to get hold of them to be able to install the manually because, heiho, my internet does not work! Can someone please give me a link for inux-backports-modules-jaunty as I am not able to find a single link on the entire forum that actually works and does not come up with:

two or more packages specified (linux-backports-modules-jaunty-generic jaunty)
two or more packages specified (linux-backports-modules-jaunty jaunty)

.......

Please help!

Thanks

Ubichinon

---

### Post by arubislander on 2010-11-16
Hi... Jaunty Jackalope has reached end-of-life on October 23rd 2010 and so it is no longer supported. I shudder to suggest it, but have you tried running Lucid or even Maverick on your machine? The wifi detection has really improved (at least on the machines I tried)

---

### Post by rondackcpu on 2010-11-16
ubichinon:

I am not familiar with the two cards you mention, but if they worked before in previous versions of Ubuntu, you might try installing "linux-firmware-nonfree" from the Maverick repository using either synaptic or apt-get.  These pieces of firmware were routinely distributed in the "iso" of previous versions, but not Maverick.  Installing that package brought my NICs to life with no further messing around.

CRS

---

### Post by ubichinon on 2010-11-17
> **arubislander said:**
> Hi... Jaunty Jackalope has reached end-of-life on October 23rd 2010 and so it is no longer supported. I shudder to suggest it, but have you tried running Lucid or even Maverick on your machine? The wifi detection has really improved (at least on the machines I tried)

Thanks for your answers guys! I have of course considered reinstalling the whole thing, as 
the netbook version of the new ubuntu lucid looks quite neat. However, to get my problems sorted I was doing some searching again and unfortunately came across this:

[http://dimitar.me/how-to-enable-the-ath9k-wireless-driver-on-ubuntu-lucid-10-04](http://dimitar.me/how-to-enable-the-ath9k-wireless-driver-on-ubuntu-lucid-10-04)

which means that there is a significant probability to have spot on the same issue I am having already. I therefore can't trust because I also assume it will be the same for all the other drivers i had to fix to get linux running on my laptop (i.e. the sound card drivers were a problem like almost worse than wireless altogether, so going through that again would defo bring me to the conclusion to give up on linux and just go for a mac, which is the worst solution I want to think of).

Ubichinon

---

### Post by ubichinon on 2010-11-17
This does not work as it would remove linux-firmware that is required by the kernel I am running.

Selecting previously deselected package linux-firmware-nonfree.
dpkg: considering removing linux-firmware in favour of linux-firmware-nonfree ...
dpkg: no, cannot proceed with removal of linux-firmware (--auto-deconfigure will help):
 linux-image-generic depends on linux-firmware
  linux-firmware is to be removed.
dpkg: regarding linux-firmware-nonfree_1.9_all.deb containing linux-firmware-nonfree:
 linux-firmware-nonfree conflicts with linux-firmware (<< 1.17)
  linux-firmware (version 1.11) is present and installed.
dpkg: error processing linux-firmware-nonfree_1.9_all.deb (--install):
 conflicting packages - not installing linux-firmware-nonfree
Errors were encountered while processing:
 linux-firmware-nonfree_1.9_all.deb

---

### Post by dino99 on 2010-11-17
you'd better to install the latest kernel, 2.6.37-4 for natty work fine (temporary change your sources.list to natty to install that kernel, then change back and update again)

---

### Post by coffeecat on 2010-11-17
As far as the linux-firmware-nonfree package is concerned, linux-firmware was only split up into the  separate packages linux-firmware-nonfree and linux-firmware-free for Karmic (9.10) onward. And I doubt that the nonfree firmware modules are going to help here anyway.

I concur with what's being said about using a later version of Ubuntu. The Atheros 9285 adapter is supported in later versions, but I have come across sporadic threads about difficulties with it. Whether these problems were specific to the 9285 chipset or the particular computer the poster was using is difficult to tell. And as far as the dimitar.me link is concerned, I haven't looked at it closely, but I generally take howtos about Ubuntu on personal blogs with a very large pinch of salt. Sometimes as much as is contained in the Cheshire salt mines. :wink:

There's an easy way of finding out how well Ubuntu 10.04 and 10.10 will behave out of the box on your machine with that wireless chipset and without installing. Download the ISOs for 10.04 and 10.10, burn them to CD and run both live. If you can connect OK you will probably be OK with a permanent installation. If not, then you will probably have problems.

---

### Post by ubichinon on 2010-11-19
Hi!

Unfortunately 10.04 and 10.10 are of no help either. creating the custom kernel according to dimitar's blog however managed to get my laptop to connect to wired, wireless when using wep as well as my o2 dongle (not even hardy did that for me:) so can only speak best about this page. Connections to wpa are still not possible as the 4-WAY-HANDSHAKE of wpa_supplicant constantly fails. I don't need to go into details I guess because this issue has already been posted on the forum thousands of times and never seems to end really. I am now reading about how to debug wpa_supplicant. hopefully I will be done in a few years time and then even I will hopefullly be able to connect or I just switch to a macbook and get work done instead of getting constantly lost in useless ubuntu details.   

Ubichinon

---

