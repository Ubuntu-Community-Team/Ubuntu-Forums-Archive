---
title: "Segmentation fault in boot after 2.6.24-22 (and-21) kernel updates"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by PetriSirk on 2008-11-29
Hi,

I am still running 2.4.24-19 kernel under Ubuntu 8.04 LTS because the latest two kernel updates fail to boot.

Unfortunately I am unable to capture the output in text format, but I have photos of the seg. fault. :)

The system is running on a Fujitsu Siemens Scaleo P, AMD Athlon 64 X2 2600. 

After the Segmentation fault [3_FirstSegF] the boot stays in loop reporting [4_ErrLoop] hung cpu (soft lockup) every 11 seconds.

Is anyone having similar problems?

Can anyone advice if it possible to debug the problem?

I am skilled in unix and software engineering. I can compile a kernel if neccessary, but I would rather keep up with updates and minimize the configuration.

-Pete

---

### Post by littlebat on 2008-12-11
Hi, it seems I have the same problem a month ago. See: Booting "Segmentation fault" after updating initrd.img-* files for Hardy [http://ubuntuforums.org/showthread.php?t=979639](http://ubuntuforums.org/showthread.php?t=979639) 

Backup your /boot/initrd.img-2.6.24-19-generic file (and, don't save this backup file with .bak suffix). Then, execute "sudo update-initramfs -u -v -k 2.6.24-19-generic" to update this file. Restart your system, if it can't boot from this udpated initrd.img-2.6.24-19-generic file, then, you have a same problem as mine.

I have reported this as a bug to Ubuntu, Booting "Segmentation fault" after updating initrd.img-* files for Hardy [https://bugs.launchpad.net/ubuntu/+bug/297546](https://bugs.launchpad.net/ubuntu/+bug/297546) , but has no response. You can report your problem too to make Ubuntu come into notice our problem.

---

