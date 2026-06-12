---
title: "lynx won't run from live cd or installation"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by UphillSkier on 2010-05-06
Lucid Lynx won't boot my laptop. As it loads I get a message
"wbsd unable to assign resources".  Then the splash screen comes  up momentarily and the screen goes blank. This happens
a. when I did a cdromupgrade from the 10.4 alternate disk
b.  when I did a full install from the alternate disk
c.  when I tried the live cd ( the 10.4 desktop disk)

Koala (9.10) was running fine before I trashed it with (b) above.I am now running from the 8.04 LTS desktop disk, which also works fine. Can anyone suggest what might be going on?

This is an older laptop manufactured by MDG (Canada) with a Pentium (R) M processor and 486.4 MiB

I plan to get a 9.10 desktop disk and reinstall from that, but I'd sure like to know what is the problem with 10.4.

thanks for any help

---

### Post by Catharsis on 2010-05-07
What is the output of:
```
lspci | grep VGA
```?

---

### Post by UphillSkier on 2010-05-07
> **Catharsis said:**
> What is the output of:
```
lspci | grep VGA
```?

Thanks for ansering, Catharsis.

This is while running on8.10 LTS disk
```

ubuntu@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
ubuntu@ubuntu:~$ 
```

---

### Post by UphillSkier on 2010-05-07
Catharsis

I followed your advice in this thread  [http://ubuntuforums.org/showthread.php?t=1474464](http://ubuntuforums.org/showthread.php?t=1474464)


namely to insert i915.modeset=1 after quiet splash in the GRUB commands to load the kernel.

I still got the unable to assign resources message but the boot continued successfully through to login.

Thanks a million.:p

---

### Post by dino99 on 2010-05-07
i think your laptop have not enough ram, you should try with something like xfce or lxde

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

found this: 
*** wbsd is a ISA device so it might not be handled properly with modern 
dists (which assume everything is PCI or similar). Fedora was also 
broken until I pointed out the problem to them. ****

sudo update-pciids && update-usbids

---

### Post by Catharsis on 2010-05-07
> **UphillSkier said:**
> Catharsis

I followed your advice in this thread  [http://ubuntuforums.org/showthread.php?t=1474464](http://ubuntuforums.org/showthread.php?t=1474464)


namely to insert i915.modeset=1 after quiet splash in the GRUB commands to load the kernel.

I still got the unable to assign resources message but the boot continued successfully through to login.

Thanks a million.:p

Glad to hear it. You can make the change permanent with Workaround A here:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

