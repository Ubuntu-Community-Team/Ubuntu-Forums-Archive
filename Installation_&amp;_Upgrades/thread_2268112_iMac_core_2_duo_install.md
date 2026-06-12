---
title: "iMac core 2 duo install"
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by Francis_Dunnery on 2015-03-06
Image an old iMac core 2 duo and I am trying to install Ubuntu on it... Infact I'm trying to install any linux distro on it but I would prefer Ubuntu. It will not mount the ISO disk image. I have managed to get Ubuntu 11.4 installed but it's not supported any more. Since researching this issue I have found an underbelly of the same problem with these particular machines. It seems that the hardware cannot deal with an ISO disk image that is designed for dvd AND sub stick although I could be totally wrong. I have tried Lunbubtu, xubuntu and its all the same. 
My question is... Does anyone know a command I can type into the terminal that will download and install the latest version of Ubuntu? If I can get it to install as a duel boot machine I can bypass the ISO disk image and just download and install straight from the terminal using the 11.4 to type and install it. ( if you get my drift). 
I hope I have been clear enough. Thanks guys

---

### Post by grahammechanical on 2015-03-06
There is a way to upgrade 11.04 to 11.10 and then to 12.04 but it requires editing the URLs in the sources.list file to point to another repository/server.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

What you want to do is here

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

But it is not as easy as typing in a single command.

> [COLOR=#333333][FONT=Ubuntu]The disadvantage of this method is that you need to mess a little with a grub config file. You may also find that current Ubuntu versions provide a grub-2 config file, while your older Ubuntu installation may only have (legacy) grub-1 installed. But it takes only three lines of grub commands.[/FONT][/COLOR]

I have never tried this. Not even as an experiment. So, I can not offer any advice.

Regards.

---

### Post by Francis_Dunnery on 2015-03-07
Here is the answer to the question. 
[http://youtu.be/ld7UVefOvHo](http://youtu.be/ld7UVefOvHo)

---

### Post by Tablecrasher on 2015-03-08
I recently did just this on an aluminum imac.  I followed the directions in the last section of this site. [http://zo0ok.com/techfindings/archives/1796](http://zo0ok.com/techfindings/archives/1796)

I used it to install LinuxMint 17.1 64bit via a Usb drive.

---

