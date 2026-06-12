---
title: "Boots to White Screen (NO GDM, No Plymouth/Splash)"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by insaini on 2010-05-03
So this is the third ubuntu upgrade ive performed.. and the third time it has messed up during that process.. will it ever be a fully smooth upgrade for me.. who knows.. in any case... 

Ive upgrade to 10.04 x86 .. upon reboot.. no kernel for 10.04 has been added.. so i go into recovery mode of 9.10 .. manually add 10.04 kernel entries.. and then attempt to boot into 10.04 .. all I get is a white screen (on the left screen of my dual mon setup) .. 

next i try and go into recovery mode.. well this takes me to a terminal login point.. i enter my user.. pass.. and type startx at the prompt.. which takes me into gnome and my desktop.. at this point everything seems ok.. i do some reconfiguring.. reinstalling kernels.. etc..etc..  then reboot..  and once again nothing.. but white screen..  i have to go into recovery mode and manually enter gnome.. 

is anyone else having this issue.. has anyone been able to solve this.. 

cheers

J

---

### Post by insaini on 2010-05-03
Ok so here are some interesting things happening..

sudo dpkg-reconfigure xserver-xorg   .. does nothing.. runs and comes back to the prompt without asking questions

sudo dpkg-reconfigure -a .. asks a question about home directories.. and then exits back to the prompt..  

i definitely dont think this is expected behaviour.. something is definitely wrong.. anyone know what could cause this?

---

### Post by P4man on 2010-05-03
Couple of threads with near identical problems. Have a look here:
[http://ubuntuforums.org/showthread.php?t=1466818&page=5](http://ubuntuforums.org/showthread.php?t=1466818&page=5)

its a long thread, as we tried everything, in the last post you will find what solved it for him

---

### Post by dino99 on 2010-05-03
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure jockey

sudo apt-get update
sudo apt-get install -f

need to check: system admin hardware driver

reboot

---

### Post by insaini on 2010-05-03
> **dino99 said:**
> sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure jockey

sudo apt-get update
sudo apt-get install -f

need to check: system admin hardware driver

reboot

this is standard.. done and done many times over.. thanks for the suggestion though.. as for that other thread.. that user had a failure during the upgrade.. while mine completed successfully and all packages were setup and installed.. recovery mode only helps by taking me to the console so I can 'startx' manually .. which is how im typing this message right now.. 

.. however i have a temporary fix for my predicament anyways..  I dropped to the terminal from recovery mode.. and did a 'sudo gdm' .. that took me to the login screen and .. once i got into gnome.. i ran gdmsetup.. and basically set it up to log me in automatically..  i then editted the grub menu.lst and removed 'splash' from the main kernel boot.. (so it was 'ro quiet splash' and i changed it to 'ro quiet')

now i do have some crazy artifacts showing up when starting up.. but it eventually does take me into the desktop..

albeit without GDM or Plymouth.. WTF

---

