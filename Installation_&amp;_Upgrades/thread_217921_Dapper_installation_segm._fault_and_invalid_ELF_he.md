---
title: "Dapper installation: segm. fault and invalid ELF header after 1st reboot..."
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by dakabali on 2006-07-17
Dear all,

I need your help, 'cause I've got no idea what I do wrong... I've been trying to install Ubuntu 6.06 using the Live DVD on a Pentium D computer with an onboard ATI Rage XL card. I'd like to create a small boot, a swap and 2 bigger xfs partitions. I've experienced the followings:

1) If I install "normally", at the first reboot after finishing the installation Ubuntu can't enter the GUI, instead it gives back an error message that the X server couldn't start. I can log in using the command line interface but I can't start any program without getting back either a "segmentation fault" or an "error: unable to open shared file ... invalid ELF header" I receive the same error message(s) even for aptitude and apt-get so I basically can't install any additional package! :confused: 

2) I tried to conduct a step by step installation. I installed Ubuntu as server, afterwards 

"sudo aptitude install ubuntu-base"
"sudo aptitude install x-window-system core"
"sudo  dpkg-reconfigure xserver-xorg" 

Everything fine, driver is "ati" and startx brings me to a wonderful X session in 1024x768 - also after rebooting. Now I installed ubuntu desktop using 

"sudo aptitude install ubuntu-desktop"

"sudo gdm start" ...and it IT WORKED!... Until I rebooted and experienced the very same problems I described at #1 ](*,) 

I changed GRUB to LILO, the xfs partitions to ext3, tried to install the ATI driver (fglrx) - no effect...

...any idea?

cheers

---

### Post by dakabali on 2006-07-19
Now it works. Just to share the solution with all of you who might need it:

First of all I didn't manage to find the exact problem, but I didn't need it, either. I managed to figure out, that the problem was caused by installing the ubuntu-desktop package.

Therefore I conducted the installation of the sub-packages of the ubuntu-desktop manually:

1) 
server type install with live DVD amd64

2) 
sudo aptitude install x-window-system-core 
sudo dpkg-reconfigure xserver-xorg
sudo aptitude install gdm
sudo aptitude install ubuntu-artwork
sudo aptitude install gnome-app-install

this installs a working ubuntu desktop for me

3)
sudo aptitude install gnome-system-tools
sudo aptitude install gnome-session
sudo aptitude install gnome-control-center
sudo aptitude install gnome-common
sudo aptitude install gnome-volume-manager
sudo aptitude install language selector

These are some extensions and... voilá here it is a working ubuntu system! The only problem is, I don't know which subpackage in the ubuntu-desktop brought my server down, so I must be careful with future installation/upgrades.

hope it helps to someone
bye

---

