---
title: "Burg Grub2 not working"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by poision_heart on 2010-03-09
hi i ve some issue with burg on my inspiron14(core i3 ATI4330).
i ve installed burg but its not working.can anyone help me.

i ve followed tutorials which i m posting here too.pls tell me whats wrong with my system


1.Install BURG

Edit source.list file(Open terminal from Applications/Accessories/Terminal):

sudo gedit /etc/apt/sources.list

add following into the file and save it.

deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic mainAdd GPG key:

gpg --keyserver subkeys.pgp.net --recv 55708F1EE06803C5
gpg --export --armor 55708F1EE06803C5 | sudo apt-key add -

update and install:

sudo apt-get update
sudo apt-get install grub-pc

Then,write the new startup code into MBR:

sudo grub-install "(hd0)"


2.Download themes:

wget [http://grub4dos.sourceforge.net/themes.tar.bz2](http://grub4dos.sourceforge.net/themes.tar.bz2)
Extract it to /boot/grub/themes:

sudo tar -xjf themes.tar.bz2 -C /boot/grub/themes/
Then,edit /etc/default/grub:

sudo gedit /etc/default/grub
delete the “#”(without quotes) before this:

GRUB_TERMINAL=console3.Now,edit /etc/grub.d/40_custom:

sudo gedit /etc/grub.d/40_custom

copy and paste following into this file:
set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui
load_config /boot/grub/themes/proto/theme.txt


the last line will load the theme.You can change this line to :
ubuntu theme:
load_config /boot/grub/themes/ubuntu/theme.txt
winter theme:
load_config /boot/grub/themes/winter/theme.txt
proto theme:
load_config /boot/grub/themes/proto/theme.txt
Now,use this command to create grub.cfg file:

sudo update-grub

---

### Post by Locke_99GS on 2010-03-09
I'm afraid we need to know what is actually happening. "i ve installed burg but its not working.can anyone help me." is very general, and doesn't direct us to your issue. 

Does burg fail to load? Can you not boot your system? Cannot select proper OS or Kernel?

---

### Post by poision_heart on 2010-03-09
hi

actually its not failed to load.
when pc starts i found change in grub2 menu.Normally its like a simple page but now.every selected line (eg ubuntu.9.10)blinks and highlighted.means burg installed properly.

only thing is i m not getting any theme(eg ubuntu,winter or os logo sora)

---

