---
title: "Intel Atom installation issues."
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by sourcenz on 2013-05-05
Hey guys! Im really really hoping someone can help me with this before i throw this laptop so far it will destroy the moon!

Ive been trying now for MONTHS to try and install ubuntu on my Acer Aspire ONE netbook, Intel Atom processor. Ive tried multiple versions, 12.04, WUBI all to no avail! Ive recently tried to install Back Track 5 R3 with GNOME and have had no luck, however was the closest to running.

With 12.04 LTS, i get a black screen and a blinking cursor after install which hangs at

"CPU interrupts balancing daemon" and a blinking cursor. It goes no further and i need to force a power cycle.

With Back Track, the install completes fine and on boot, i am receiving the 10.04 splash screen then the screen just goes completely black and i need to force a power cycle.

One thing i did notice was that when copying the ISO for 12.04 with both unetbootin and Linux Live USB creator, the copy happened very fast as where with Back Track, the process took quite a bit longer with unetbootin. I checked the ISO MD5 hashes and they were correct.

Right now im stuck! This netbook (which i really like, its a great machine) just really wont take any version of ubuntu. I have very little ubuntu knowledge and thus the reason i would like to install ubuntu and also for a nice lightweight OS.

Does anybody have any ideas? Please help me out i would really appreciate it1

Thanks

---

### Post by fantab on 2013-05-05
Give more details of your Netbook internals and also the exact model... we can't help you without you helping us with that info.

---

### Post by P-I H on 2013-05-05
I installed Ubuntu 13.04 32 bit on an Asus 1000HE and there were no problems.
This computer has 2x Intel Atom CPU N280 @ 1.66 GHz
The graphics is Intel 945GME x86/MMX/SSE2

---

### Post by sourcenz on 2013-05-05
> **fantab said:**
> Give more details of your Netbook internals and also the exact model... we can't help you without you helping us with that info.

Sorry guys!

Model is Acer Aspire One D270 - 26Dkk
1gb RAM
Intel Atom N2600 @ 1.6Ghz

Thanks for the reply

---

### Post by SecretImbecile on 2013-05-05
do the screen issues happen during installation? if so have you tried installing via the alternate install image?

---

### Post by sourcenz on 2013-05-05
> **SecretImbecile said:**
> do the screen issues happen during installation? if so have you tried installing via the alternate install image?

Ive tried everything except CD or DVD. The netbook has no CD/DVD player.

So ive tried USB and WUBI installs, both to no avail. Different versions and even different laptops.

I managed to install on another laptop no probem.

Thanks

---

### Post by AssureTech on 2013-05-05
> **sourcenz said:**
> 
With 12.04 LTS, i get a black screen and a blinking cursor after install which hangs at

"CPU interrupts balancing daemon" and a blinking cursor. It goes no further and i need to force a power cycle.

The only way I was able to get an Intel Atom board to work with Ubuntu 12.04 LTS is with the following:

sudo vi /etc/default/grub
then add mem=4G to the end of the GRUB_CMDLINE_LINUX_DEFAULT variable.

e.g., GRUB_CMDLINE_LINUX_DEFAULT="mem=4G"

---

### Post by fantab on 2013-05-06
> **sourcenz said:**
> Sorry guys!

Model is Acer Aspire One D270 - 26Dkk
1gb RAM
Intel Atom N2600 @ 1.6Ghz

Thanks for the reply

This NETBOOK has Atom **CEDARVIEW chipset** with **PowerVR Graphics**. (Search www for more info). The Graphics are poorly supported in Linux. The normal Ubuntu/*buntu install wont work. It didn't for me. I have ASUS 1015CX with almost same specs...

Here are some useful links:
[http://askubuntu.com/questions/168986/cedar-view-drivers-arent-working](http://askubuntu.com/questions/168986/cedar-view-drivers-arent-working)
[http://linuxeeepc.blogspot.in/2012/08/lubuntu-on-eeepc-1025c-with-correct.html](http://linuxeeepc.blogspot.in/2012/08/lubuntu-on-eeepc-1025c-with-correct.html)
[http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/](http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/)
[http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/](http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/)

I have tried lots of other distros and after a lot of head banging, I have found that **[BodhiLinux]("http://www.bodhilinux.com/about_bodhi.php")** (based on Ubuntu LTS) works out of the box with fbdev driver. You will not be able play HD graphics or watch HD videos on Web but most of the things work. 
I installed **[Fedora]("https://fedoraproject.org/en/get-fedora-options")**_xfce on my netbook which has 2GB RAM and things work and you can watch HD videos on youtube upto 720px. But watching HD movies on your desktop player may or may not work. Touchpad needs to be reconfigured/tweaked but that is simple. 
In your case I suggest you opt for **Fedora_LXDE-32bit** (only 32 bit version work with this Netbook).

Good Luck...

---

### Post by sourcenz on 2013-05-06
Thanks for all the replies guys. Loving the support here!!

So, i just installed 13.04 and the install went flawlessly and i was this morning able to boot into linux sucessfuly. It looks like its working maybe some fixes in the 13.04 release. I did however do a upgrade from the previous 10.04 Back Track install.

Anyway, my next question now is, am i able to run backtrack on 13.04 somehow? Some pen testing to do

Thanks guys!!

---

### Post by sourcenz on 2013-05-07
Now the windows install is gone and i really dont know how or why but no matter what i cant repair the windows boot record.

Tried to reinstall and chose the option to "remove everything and reinstall" and now, NO windows install.

---

### Post by fantab on 2013-05-07
I hope there is no hardware failure. Anyways...

Boot with ubuntu. use Gparted to delete ALL partitions on HDD. Create new partition table (will be listed under 'device') choose 'msdos'. Don't create partitions. Reinstall Windows and use its utility to create and format partition.

Then download either BODHILinux or Fedora_xfce and install. I suggest you try BodhiLinux... it is based on ubuntu and most of the commands are same as Ubuntu.

---

