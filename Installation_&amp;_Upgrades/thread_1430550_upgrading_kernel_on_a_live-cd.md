---
title: "upgrading kernel on a live-cd"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by foosaa on 2010-03-15
Hi,

I am building a live-cd using live-helper on Karmic (9.10). The process executes fine and I am able to build a live cd of ~200MB in size with minimal and xfce. But things does not work if I try to upgrade the kernel with the one of them from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) site. Ubuntu kernel team publishes the kernel for testing and I would like to upgrade the kernel for testing. But when I upgrade the kernel from inside the live-helper's interactive shell, it upgrades fine and iso gets created. While booting, it loads the kernel and errors out with the following message:

```

(initramfs) mount: mounting aufs on /root failed: No such device.
aufs mount failed.

```

I am running initramfs after installing the new kernel (a .deb file) using dpkg.

What else should I need to do for getting this to work?

Thanks.

---

### Post by phillw on 2010-03-15
I can't help on the kernel update, but, have you considered either xubuntu (which uses xcfe), or an even more light-weight variant called lubuntu (which uses lxde). xubuntu is available in 9.10, lubuntu is only in 10.04 alpha. I'm running lubuntu alpha and it is certainly stable enough to run with, just not ready for release. All the *buntu family are in 10.04 alpha testing, with their release due at the end of April.

It may save you the work of creating your own CD if one of those two suit your needs. 

xubuntu --> [https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)
lubuntu --> [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Regards,

Phill.

---

### Post by foosaa on 2010-03-15
Thanks for the information though.

My primary aim is to reduce size as much as possible so that the cd/usb booting becomes faster. Currently my USB version boots under 30 seconds to a fully operational desktop with network support on most the systems!! (In a sample of 100+ different systems.)

I will not be achieving that speed in other distro. I don't want to discuss on that because my primary concern is to fix an issue with the libata, which looks like it has been addressed in the latest kernels. But I am unable to test it because of the aufs issue. Any suggestions on fixing this?

I found that the aufs kernel module is missing in the ppa mainline kernels. Would that be of any issue? Because the main repository contains the 2.6.31-x versions with aufs modules. I could not find a pre-compiled version of 2.6.33 with aufs support. If i try to compile the 2.6.33 version, the final kernel package (the .deb) file grows aroung 250 MB whereas the downloaded pre-compiled version is aroung 30 MB!!! I tried multiple options of importing the oldconfig / optimizing the config, but nothing helps. Either the compiled kernel give kernel-panic or does not work!!!

---

### Post by flambert on 2010-04-09
Hi,
 
Do you found any solution. I've the same problem. I make a live dvd from my ubuntu 9.10 system with remastersys and try to boot from the dvd. But I get exactly the same error message like you.
 
Regards,
     flambert

---

### Post by Johnnyent on 2010-04-09
Hi there!
 
I've the same problem!!!Someone?!!

---

### Post by llelectronics on 2010-05-29
As aufs is not included in the mainlinekernel it won't boot. 
You have to apply a aufs patch the kernel and rebuild it.

---

### Post by slickvguy on 2010-06-13
Just had the same problem, due to my using mainline kernel 2.6.34 (works better with my Core i3/H55 mobo).

Rather than starting over from scratch w/ remastersys and then running the Ubuntu USB Creator again, here is what I did to get my LiveUSB working quickly:

1) Booted into Ubuntu using the most recent Ubuntu "standard" kernel (you should see it your grub2 menu). For me, it was 2.6.32-22-generic.

2) Updated my initrd for that kernel version so that it included the casper stuff (because I installed remastersys and casper while using the mainline kernel, so the packages (and remastersys after I ran it) updated the mainline kernel's initrd only).

```
sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
```

3) Copy the kernel and initrd from the /boot directory to the usb stick's casper directory, changing the filenames to "vmlinuz" and "initrd.gz". Just use 'sudo cp...'

That's it, that's all.

---

