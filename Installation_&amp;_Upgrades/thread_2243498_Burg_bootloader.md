---
title: "Burg bootloader"
date: 2014-09-09
forum: Installation &amp; Upgrades
---

### Post by rainbatt on 2014-09-09
The issue is that when I choose the ubuntu option it works 1/3 of the  time without any trouble but sometimes the resolution when
I get to  ubuntu is weird and half the screen is not shown and sometimes it  doesn't start at all but freezes on a black screen.

Anyone?

---

### Post by rainbatt on 2014-09-09
Does Burg mess up resolution?

---

### Post by yancek on 2014-09-09
You should find some documentation at their web site.  Never used it myself but there are a lot of hits on google.

[http://code.google.com/p/burg/](http://code.google.com/p/burg/)

---

### Post by grahammechanical on 2014-09-09
Burg = Grub spelt backward. and like Grub it is Just a boot loader. It starts off the process of the kernel loading and it evaporates from system memory. The kernel and the Xserver then play a part in setting screen resolution with the video driver taking control long before we get to the login screen and the desktop.

Try using the open source video driver or experimenting with the available proprietary video drivers.

Do you have a computer monitor or a digital TV/monitor, or a digital TV being used as a monitor. There may be settings in the monitor that we need to adjust. It all depends on what you have.

Regards

Regards.

---

### Post by rainbatt on 2014-09-09
Was working well under Grub2 till I tried Burg.  Even thought I switch back to Grub2, the resolution problem still around.
How to totally remove Burg and install Grub2?

---

### Post by oldfred on 2014-09-09
The 'new' burg shows most recent files as 2010, so not current.

If you can boot, purge burg & grub and totally reinstall grub. Make sure Internet is working as once old versions of grub are purged you can not reboot until new grub2 installed. Best to make sure you have another current version live installer just in case.

Not sure if burg's package name is burg, but include whatever package name burg uses in the purge command.

       # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

---

