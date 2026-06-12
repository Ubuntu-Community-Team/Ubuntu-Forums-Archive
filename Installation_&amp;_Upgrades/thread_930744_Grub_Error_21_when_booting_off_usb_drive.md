---
title: "Grub Error 21 when booting off usb drive"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by West Suhanic on 2008-09-26
Hello All:

I am installing hardy herron from a usb key built to allow installing from the network. This key does exactly what it is supposed to do. I am also installing ubuntu 8.04 from the net onto a usb key. The install works flawlessly. The problem comes when I boot into the newly created usb drive. I get the dreaded grub error 21. In order to get the machine to boot I have to hit ctrl-alt-del and everything works nicely after that. I have been struggling to resolve this problem for over a year. Here is my system information:

fdisk -l yields the following information which I have edited for clarity:

/dev/sda1 boot=yes type=jfs
/dev/sda5          type=swap

The drive /dev/sda1 is mounted on /


The file /boot/grub/device.map contains:

(hd0) /dev/sda


The /boot/grub/menu.lst contains:

## ## End Default Options ##

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=33ca655f-d7d2-4134-8ff7-03eab1d40bec ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=33ca655f-d7d2-4134-8ff7-03eab1d40bec ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Using the blkid command yields:

/dev/sda1: UUID="33ca655f-d7d2-4134-8ff7-03eab1d40bec" TYPE="jfs"
/dev/sda5: TYPE="swap" UUID="c1deef77-1f47-44a5-b263-42366588a508"

Also when I do a dmesg, the usb drive is seen by the OS as /dev/sda .

My machine is a Asus p5GC-MX with an Intel Core duo, e2160.
The bios sees the usb drive. 

Any suggestions? All help is appreciated.

regards,

West Suhanic
Any suggestions?

---

### Post by caljohnsmith on 2008-09-26
> **West Suhanic said:**
>  The install works flawlessly. The problem comes when I boot into the newly created usb drive. I get the dreaded grub error 21. In order to get the machine to boot I have to hit ctrl-alt-del and everything works nicely after that.
So to clarify, you install to your USB drive, you restart, you get a Grub error 21, you hit Ctrl-Alt-Delete, and then it boots OK after that? You don't then have to do another Ctrl-Alt-Delete on a cold start up? If you only once have to do the Ctrl-Alt-Delete but never after that, then it doesn't seem like too big a deal, but is this what you are concerned about?

---

### Post by West Suhanic on 2008-09-26
Hello Sir:

I just want to solve the problem. By solve I mean I do not want to see grub error 21. I want to power on and not see the grub error 21 message. Any suggestions?

thanks for the help.

West Suhanic

---

### Post by Pumalite on 2008-09-26
Check these two links:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

