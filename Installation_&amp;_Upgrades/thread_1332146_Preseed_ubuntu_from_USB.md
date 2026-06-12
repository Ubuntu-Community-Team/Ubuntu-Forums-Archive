---
title: "Preseed ubuntu from USB"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Senathon on 2009-11-20
I have create a USB installation Disk of Ubuntu, it works fine.  Now I am setting up a preseed.cfg on the root.  I have edit the text.cfg with the following:

default live-install

label live-install
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append locale=en_US console-setup/layoutcode=us noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed.cfg boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --

I boot up and the installation does not fill the questions, it acts like there is no preseed.cfg.  I confirm the preseed.cfg is on the root of the usb.  

Any ideas?

---

