---
title: "No kernel! (user error)"
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by MrMe01 on 2015-10-07
Hi folks,

TL;DR how do I install a kernel on an offline, broken, kernel-less install? Debian based rescue media on hand.

After getting fed up with multiple kernel listings in Grub after the recent kernel release, I seem to have broken things. I'm running Ubuntu with KDE and Gnome, as well as Windows 7 and 10. (3 OS's over 2 internal drives)

I (foolishly) decided to remove kernels, besides the latest with Synaptic. The only problem is I seem to have hosed my install. My Grub menu lists an old install of Porteus that is USB bootable (mechanical drive) that forgot about, as well as Windows 7 and 10. 

I've tried to use the grub rescue disk (also USB bootable) I think that ran update-grub and added the old install of Porteus to Grub (I have multiple USB drives plugged into my system most of the time). It appears to recognise that I have no kernel and tries to fix it, but it never does. I've left it running for about 2 hours now and nothing has changed. Rebooting the system gives me the 3 options, 7, 10 and Porteus (broken). I have a USB bootable version of Lubuntu / Debian (the Grub rescue image), how do I go about fixing this?

Thank you in advance :D

---

### Post by grahammechanical on 2015-10-07
I suppose the principles are the same to those we use to install an upstream kernel.

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

See the section Installing Upstream Kernels. For a 64 bit CPU and OS we need to download

1) linux-headers- .... _amd64.deb
2) linux-headers- .... _all.deb
3) linux-image- .... _amd64.deb

put them into a folder by themselves and run

[code]sudo dpkg -i *.deb

You will need a kernel suitable for your version of Ubuntu whatever version it happens to be.

You could do this from recovery mode>root. Or from a live session, remembering to download the files to a folder in the Ubuntu partition and then using the terminal and changing directory (cd) to that folder to run the dpkg command. If you do not want any USB based OS showing up in the Grub boot menu, then remove the USB stick before doing this.

Regards.

---

### Post by tgalati4 on 2015-10-07
There is a GRUB2 configuration setting for the number of backup kernels that are shown in the GRUB2 menu.  I believe the default value is 7 (which is way too much), It should be set to 2 or 3.  You want at least one backup kernel.  Don't delete your current kernel from a working system.

---

### Post by MrMe01 on 2015-10-07
Thank you for the reply. Is there any way I can do this with something like apt-get -f install? Possibly chroot into the install and install with apt from there?

---

### Post by MrMe01 on 2015-10-07
> **tgalati4 said:**
> There is a GRUB2 configuration setting for the number of backup kernels that are shown in the GRUB2 menu.  I believe the default value is 7 (which is way too much), It should be set to 2 or 3.  You want at least one backup kernel.  Don't delete your current kernel from a working system.

Hindsight is such a wonderful thing :P

I literally kicked myself when I rebooted and realised what I had done. This information would have been great a few hours ago :)

---

### Post by tgalati4 on 2015-10-07
If you do delete the current kernel, or everything in /usr/bin, then don't reboot.  Your system will continue to run as if nothing happened.  

Yes you can install using *apt*.  But you have to install all the pieces.

```
apt-cache search utopic
```

At a minimum:  linux-image-generic-lts-utopic - Generic Linux kernel image

This presumes 14.04.

Install each piece and inspect your /boot.  When you have all the files, you can try to reboot.

> tgalati4@Mint17 /boot $ ls -la
total 38908
drwxr-xr-x  3 root root     4096 Aug 12 08:57 .
drwxr-xr-x 23 root root     4096 Dec 19  2014 ..
-rw-r--r--  1 root root  1158016 May  2  2014 abi-3.13.0-24-generic
-rw-r--r--  1 root root   165510 May  2  2014 config-3.13.0-24-generic
drwxr-xr-x  5 root root     4096 Jul  3 07:15 grub
-rw-r--r--  1 root root 28803172 Aug 12 08:57 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3372643 May  2  2014 System.map-3.13.0-24-generic
-rw-------  1 root root  5776416 May  2  2014 vmlinuz-3.13.0-24-generic


---

