---
title: "error: no video mode activated"
date: 2012-01-02
forum: Installation &amp; Upgrades
---

### Post by jlparsons on 2012-01-02
Hi folks,

Installed ubuntu 11.10 on a lenovo T410.  Everything works perfectly out of the box, no configuration required whatever.  I installed on an encrypted partition via the alternate x64 image from a usb stick.  When I boot, the following text line displays on an otherwise empty screen:

error: no video mode activated

I assume this is from grub?  The machine displays this for a few seconds then boots normally, so I must admit this is purely a cosmetic issue.  However as I will be starting my machine in front of clients (no suspend or hibernate on an encrypted partition thankyou!) I'd rather get rid of it.  I've found similar issues on other posts/forums but no solutions.

Any ideas?

---

### Post by searchfgold6789 on 2012-01-02
Try adding nomodeset, try temporarily then if it works you can do it permanently: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bitinerant on 2012-05-10
This seems to be a known bug.  The issue and work-arounds are listed in:

    [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802)

---

### Post by hskhakh on 2013-01-13
Commenting out **GRUB_HIDDEN_TIMEOUT **and **GRUB_HIDDEN_TIMEOUT_QUIET **in **/etc/default/grub** works for me.

GRUB_DEFAULT=GRUB_SAVED_DEFAULT
*#GRUB_HIDDEN_TIMEOUT=10  *               
*#GRUB_HIDDEN_TIMEOUT_QUIET=*          
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Note: Please remember to run 'sudo update-grub' after above changes to /etc/default/grub.

HK

---

### Post by Evan I S on 2013-03-09
> **hskhakh said:**
> Commenting out **GRUB_HIDDEN_TIMEOUT **and **GRUB_HIDDEN_TIMEOUT_QUIET **in **/etc/default/grub** works for me.

GRUB_DEFAULT=GRUB_SAVED_DEFAULT
*#GRUB_HIDDEN_TIMEOUT=10  *               
*#GRUB_HIDDEN_TIMEOUT_QUIET=*          
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Note: Please remember to run 'sudo update-grub' after above changes to /etc/default/grub.

HK


Like what commented I changed GRUB_TIMOUT=?? to 3 from 2.  It resolved!  Thanks! :-)

---

