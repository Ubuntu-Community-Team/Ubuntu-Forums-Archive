---
title: "which version for Dell inspiron 15R?"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by loucat on 2012-06-16
[FONT=arial][SIZE=2]****Hi guys!

I've tried installing ubuntu 10 in a partition of my new laptop, then I upgraded it (I thought it was the last version but maybe it selected the 11th?), but I've always had sound problems and trying to fix them I got now the impossibility to access my linux o.s. otherwise than in recovery mode.

So I thought that maybe starting from scratch would have been better!
Could you please suggest to me a version which is compatible with my laptop: 

Inspiron N5110 (FCG84) - i5-2450 (2.50GHz, 3MB cache, Dual Core),and the video card is [/SIZE][/FONT][FONT=arial][SIZE=1]
[/SIZE][/FONT]                                               [FONT=arial][SIZE=1]**1 GB nVidia GeForce GT 525M, **[SIZE=2]I believe it has the sound card too.

Thanks!
[/SIZE][/SIZE][/FONT]

---

### Post by codemaniac on 2012-06-16
Ubuntu Desktop 12.04 LTS .

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by kc1di on 2012-06-16
Ubuntu 12.04 should run fine on that machine.
only reservation is that their has been some problems with some Nvidia card drivers you may need to install the latest driver from here after the install. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by loucat on 2012-08-06
Hey thank you very much guys!
I'm replying a bit late 'cause I didn't have the time to solve this... 
these days i'll try that version and the nvidia driver.

just a doubt: 
at the moment I still have the old grub, which should go to linux as default but it stops there until I select windows because of my messed-up linux installation.

I'd like to install the new linux version on the same partition it has before, but what do I have to do with the grub? is it going to be messed-up at startup?

thanks!!

---

### Post by mörgæs on 2012-08-06
When booting in live mode you can delete the old Ubuntu partitions, creating space for the new install. 

After this, during install Ubuntu will offer you to overwrite the old Grub, so it should all work automatically.

---

### Post by loucat on 2012-08-12
thank you guys!
it was even easier, ubuntu 12 found ubuntu 11, erased it and install itself instead :D

and my sound problems seem to be disappeared!!!

now if I also manage to customize the themes and stuff I'll be even happier :)

thanks thanks thanks

---

