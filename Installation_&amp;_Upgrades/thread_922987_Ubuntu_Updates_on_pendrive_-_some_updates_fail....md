---
title: "Ubuntu Updates on pendrive - some updates fail..."
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by steelxenon on 2008-09-17
Ok, I have ubuntu installed on my 8gig flash drive, works perfectly... except for some reason when I try to get the current updates some of the packages fail to install/configure: linux-image-2.6.24-19-generic, hal, linux-restricted-modules-2.6.24-19-generic, and update-notifier

```
steelxenon@ubuntu:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.24-19-generic (2.6.24-19.41) ...
Running depmod.
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.24-19-generic to initrd.img.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 17
Setting up hal (0.5.11~rc2-1ubuntu8.2) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Hardware abstraction layer hald                                     invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 hal
 linux-restricted-modules-2.6.24-19-generic
 update-notifier
```

any ideas? do you need those on a "live cd" or will it not affect anything? maybe there's already a fix for this issue? should I just ignore it?

---

### Post by soyfeo408 on 2008-09-18
Sadly, don't have a suggestion for a fix, but I'm having the exact same problem. (Fresh install of 8.04.1 on an 8GB Sandisk Cruzer Micro).

---

### Post by nowin4me on 2008-09-18
> **steelxenon said:**
> Ok, I have ubuntu installed on my 8gig flash drive, works perfectly... except for some reason when I try to get the current updates some of the packages fail to install/configure

any ideas? do you need those on a "live cd" or will it not affect anything? maybe there's already a fix for this issue? should I just ignore it?

It failed to do updates for me to at one point I order it to do the updates again.... And then it was successful maybe Ubuntu's site went down or something I advice you to try again.

Also please may you tell us what the make of your 8Gig flash drive is please.
Thank you

---

### Post by steelxenon on 2008-09-18
it's a PNY Attache 8gb from walmart for $70... the only thing that happened during the update was the screensaver activated because I left to wait for it to finish... also now when I try to install other programs with the package manager, it always shows an error at the end about those same packages... so they must still be marked to be configured... maybe there was an interruption during the download while I was gone... is there some way to make it re-download a fresh file and try again?

btw, I am using it right now, it still works, just those packages show errors when I use package manager because they try to configure again at the end... I can't try to do updates again at the moment because I'm adding some games ;) but I will try that in an hour...

Also, I used this guide:
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

---

### Post by soyfeo408 on 2008-09-18
I just tried another upgrade per nowin4me's suggestion, and still no luck. Incidentally, I followed the same tutorial as steelxenon to get my install set up.

---

### Post by steelxenon on 2008-09-19
I've seen some other guides out there that tell you to simply use the ubuntu installer and choose your flash drive from the list, then install grub on the flash on step 7... but that doesn't work for me... I just get an error trying to partition it and it stops.

---

