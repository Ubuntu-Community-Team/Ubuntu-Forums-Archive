---
title: "rpm to debian on ubuntu 8"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by lilmale1 on 2008-09-08
im using some two files in rpm neither of them work with alien
i've install it. and redhat to somehow get these files in deb

i use the following. and, also the following shows

oh, yeah im trying to install the latest linux drivers for this 
card. but im sure they both will work on this card conexsat cx88
by making my alien work i will gladly appreciate it and making things simplier on me wouldn't be better. help please

root@xbatis-desktop:/home/xbatis# sudo alien cx88-0.0.4-9.1.rh7.3.at.i386.rpm
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
mkdir: cannot create directory `cx88-0.0.4': File exists
unable to mkdir cx88-0.0.4:  at /usr/share/perl5/Alien/Package.pm line 257.
root@xbatis-desktop:/home/xbatis#

---

### Post by ronnielsen1 on 2008-09-08
It appears to be a tv card? If correct try this. If not post the output of lspci -v 

> Basically I did this:
-open terminal, use "sudo -s" to get a root shell
-cd /etc/modprobe.d"
-echo "options cx88xx card=5" > cx88xx
-modprobe -r cx8800
-modprobe cx8800
-"dmesg" to check if it worked
[http://www.linuxquestions.org/questions/linux-hardware-18/help-me-configure-a-asus-tv-tuner-in-ubuntu-344884/](http://www.linuxquestions.org/questions/linux-hardware-18/help-me-configure-a-asus-tv-tuner-in-ubuntu-344884/)

---

### Post by lilmale1 on 2008-09-08
still getting this after trying to make a deb card
does it look like anything looks wrong on there

i put the file home xbatis and typed
sudo alien cx88-0.0.4-9.1.rh7.3.at.i386.rpm



:confused::confused::confused::confused::confused::confused::confused:



root@xbatis-desktop:/home/xbatis#  
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
warning: cx88-0.0.4-9.1.rh7.3.at.i386.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
mkdir: cannot create directory `cx88-0.0.4': File exists
unable to mkdir cx88-0.0.4: at /usr/share/perl5/Alien/Package.pm line 257.
root@xbatis-desktop:/home/xbatis#

---

### Post by lilmale1 on 2008-09-08
i notices i don't have update my kernel. but when i try updating trough ubuntu it say kernel updated

---

### Post by lilmale1 on 2008-09-08
[http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html)


does anyone know how to follow this

---

### Post by ronnielsen1 on 2008-09-09
You might not need to do that but you're not giving enough information
It's possible you just need to load a module


> [SIZE=4]It appears to be a tv card? If correct try this. [/SIZE][SIZE=4][COLOR=Red]If not post the output of lspci -v [/COLOR][/SIZE]

Open console and type in[COLOR=Red] lspci -v[/COLOR] and copy and paste the contents.

I see you have more than one post open on this
According to this website 

> Note that the cx88 driver also is included in the 2.6.x kernels. 

which means the driver is already in the kernel if this is your card.
[http://gentoo-wiki.com/Hauppauge_WinTV_HVR-1100#What_you_need_to_make_it_work](http://gentoo-wiki.com/Hauppauge_WinTV_HVR-1100#What_you_need_to_make_it_work)

---

### Post by Endolith on 2009-01-06
Does the missing key warning actually have any bad effect, or is it just for checking the authenticity of the package?  I've got an RPM package and I've got the key, but I don't know how to feed the key to alien, if it even matters.

---

