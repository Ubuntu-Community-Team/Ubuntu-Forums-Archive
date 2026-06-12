---
title: "server dosen't boot,"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by tesuki on 2007-02-18
hello everyone!
I installed the server version on a laptop, and now it wont boot, it just reboot after grub.

I should tryout ubuntu and since I have a very old laptop (Toshiba, AMD K6 475MHz, 160MB RAM, AMD ATI 3D rage LT Pro), probebly from 1998. I thought it would be best installing the server version. Kubuntu/ubuntu is too heavy for it, xubuntu runs nice but still to slow, and I wont consider using fluxbuntu. I'm a vtwm user, so the best bet was to install the server edition, recompile the kernel and apt-get necessary programs. (the laptop had gentoo linux before and after waited 12 hours to get [moc]("http://moc.daper.net/") I decided stop using it).

I can't see the /boot/grub/menu.lst but i can show you the options in grub:
```

Ubuntu, kernel 2.6.17-10-server
  root (hd0,0)
  kernel /vmlinuz-2.6.17-10-server root=/dev/hda3 ro quiet splash
  initrd /initrd.img-2.6.17-10-server
  quiet
  savedefault
  boot 

Ubuntu, kernel 2.6.17-10-server (recovery mode)
  root (hd0,0)
  kernel /vmlinuz-2.6.17-10-server root=/dev/hda3 ro single
  initrd /initrd.img-2.6.17-10-server
  boot 

Ubuntu, memtest86+
  root (hd0,0)
  kernel /memtest86+.bin
  quiet
  boot 

```

it strange that it dosen't boot correctly since it should it did in xubuntu. and gentoo.
it maybe can have somthing to do with the partitionlayout i used:
```

/dev/hda:
 /dev/hda1: /boot (boot enable) ext2
 /dev/hda2: swap - (swap)
 /dev/hda3: /  - (ext3)

```

I have tested the same thing on another harddrive. then I choosed ubuntu to erase the entire disk. and the problem was the same.
i have no idea whats wrong
Maybe I should say that memtest86+ boots as it should (and reports no RAM failrus).

---

### Post by MrStonedOne on 2007-02-19
same here

using amd 400mhz processer with 93 mbs of ram,

---

### Post by confused57 on 2007-02-19
See this thread, you'll need to use the alternate cd to install a server on older hardware:
[http://www.ubuntuforums.org/showthread.php?t=290903&page=2](http://www.ubuntuforums.org/showthread.php?t=290903&page=2)

---

### Post by tesuki on 2007-02-19
many thanks for the answer confused57. I didn't know the server just used the i686. thought it was i386 and everything above. hopefully they will rename it to the right name... and thanks again.

---

