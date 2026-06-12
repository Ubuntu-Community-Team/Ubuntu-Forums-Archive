---
title: "how to install brother HL-2070n usb/local"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by n00ti on 2010-04-01
I had to figure this out for linux mint.  posted for posterity.

how to install brother hl-2070n printer local w/usb port

download the lpr and cups drivers for the hl-2070n

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2070N](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2070N)

cd to folder where drivers downloaded.

Do these commands.

sudo apt-get install apparmor-utils
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
sudo dpkg  -i  --force-all brhl2070nlpr-2.0.1-1.i386.deb
sudo dpkg  -i  --force-all cupswrapperHL2070N-2.0.1-2.i386.deb

verify install:
sudo dpkg  -l  |  grep  Brother

open browser and verify usb connection:

[http://localhost:631/printers](http://localhost:631/printers)

click on launcher:

Applications>Printers set default

test print something.

adios.

---

