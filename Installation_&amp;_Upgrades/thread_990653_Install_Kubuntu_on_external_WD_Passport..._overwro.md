---
title: "Install Kubuntu on external WD Passport... overwrote MBR?"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by sina94 on 2008-11-22
So. I got an Acer Aspire One netbook, and attempted to install Kubuntu to my WD Passport so that I could boot from it on my netbook. Unbeknownst to me, the install on the Kubuntu CD overwrote (or, at least appears to have overwritten) the MBR on my desktop in the process. Now my desktop will neither boot from my internal hard drive or the Passport (though, it will boot from the Kubuntu CD)... and the netbook won't boot from the Passport because GRUB apparently isn't set up on it correctly.

I've poked around with the Kubuntu CD and I've looked around on the internet, but I can't figure out how to restore the MBR on my desktop so that I can boot an OS... or how the get GRUB set up properly on the Passport so the the Aspire One can boot from it (if this is indeed the problem).

Have only been running Kubuntu on my desktop for about 6 months now, so not a lot of experience... and even less experience with dealing with the MBR and GRUB.

Thanks for any help you can provide.

(Also, GRUB returns error 21 without the external plugged in, and error 2 with it plugged in.)

---

### Post by confused57 on 2008-11-22
> **sina94 said:**
> So. I got an Acer Aspire One netbook, and attempted to install Kubuntu to my WD Passport so that I could boot from it on my netbook. Unbeknownst to me, the install on the Kubuntu CD overwrote (or, at least appears to have overwritten) the MBR on my desktop in the process. Now my desktop will neither boot from my internal hard drive or the Passport (though, it will boot from the Kubuntu CD)... and the netbook won't boot from the Passport because GRUB apparently isn't set up on it correctly.

I've poked around with the Kubuntu CD and I've looked around on the internet, but I can't figure out how to restore the MBR on my desktop so that I can boot an OS... or how the get GRUB set up properly on the Passport so the the Aspire One can boot from it (if this is indeed the problem).

Have only been running Kubuntu on my desktop for about 6 months now, so not a lot of experience... and even less experience with dealing with the MBR and GRUB.

Thanks for any help you can provide.

(Also, GRUB returns error 21 without the external plugged in, and error 2 with it plugged in.)

If you were using grub to boot Kubuntu & Windows on your internal desktop's drive, you can reinstall it with the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You can also use the live cd to install grub(actually grub's IPL, of Kubuntu installed on the external drive) to the mbr of the external hard drive.

---

### Post by caljohnsmith on 2008-11-23
How about from your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, to restore a Windows MBR to your internal drive, you can do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/[COLOR="Red"]sda[/COLOR]
```
The above command assumes your internal drive is "sda", so you can change that if you need to. Can you set your BIOS to boot the passport drive on start up? If so, you can install Grub to its MBR to make it bootable, and most likely you should be able to boot Kubuntu just fine; installing Grub to the MBR of the passport drive will keep your drives independent of each other so you can still boot your internal Windows drive regardless of whether the passport drive is connected or not. 

To install Grub to the MBR of your passport drive, you can use these steps:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Kubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And then if you set your BIOS to boot the passport drive, you should at least get a Grub menu on start up. Booting Kubuntu from the Grub menu might result in a Grub error, but most likely that will be easy to fix if it happens. Let me know how far you get or if you run into problems. :)

---

