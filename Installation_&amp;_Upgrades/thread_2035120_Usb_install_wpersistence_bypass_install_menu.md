---
title: "Usb install w/persistence bypass install menu"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by wheelspin on 2012-07-29
I have Ubuntu 12.04 installed to a usb drive with persistence, I want to bypass the keystroke required at the first purple loading screen that has a keyboard=human logo on it, if you don't perform a keystroke which then takes you to the menus it will still boot to the desktop then ask if I want to install or try out at that point but it takes much less time to boot if you select the option to try out during the menu loading screens, basically I want to boot straight to the desktop without any intervention by the user. Thanks

---

### Post by mindaa on 2012-07-29
I would recommend to either install it to a CD/DVD where you won;t have this problem or use a different program to create the live USB.  Such as LinuxLiveUSB at [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)  However if you are concerned about boot time the best option would be to install it to your HD.  Very simple and much much faster.

---

### Post by wheelspin on 2012-07-29
I had used this same process to run a live usb install under ubuntu 11.04 and everything worked great,

download the iso 
burn to cd
boot from cd
use the usb creator to create a persistent install
boot into the usb install
set the menu timeouts to 5 seconds
and then repeated boots goes pretty quickly to the desktop

12.04 seems to need a keystroke at the initial load screen or it will boot to a semi desktop then ask if you want to try or install

---

### Post by wheelspin on 2012-07-30
Ok I figured it out, in case anybody is wondering

go to the root /cdrom/syslinux/syslinux.cfg file

replace the contents with this

default live
label live
  say Booting Ubuntu Live session...
  kernel /casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash noprompt --

Boots straight to the desktop with no prompts needed and my drivers and files all still there and work.

---

