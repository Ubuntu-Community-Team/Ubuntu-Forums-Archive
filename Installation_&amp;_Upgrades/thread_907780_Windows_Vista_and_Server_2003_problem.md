---
title: "Windows Vista and Server 2003 problem"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by foodrules2me on 2008-09-01
Okay, I just got Server 2003, and was trying to install on a second hard drive, finally got it after unplugging the first hard drive. But afterwards, when I try to boot into Vista with grub, it just says Starting up... How do I fix Vista to boot. 
Also, if I try to go to my Server entry on grub it says the same thing, but if I start it from the bios hard drive selection it loads fine.

Any help on this would be greatly appreciated.:(

---

### Post by xen-uno on 2008-09-01
>> ... finally got it after unplugging the first hard drive

You've mentioned BIOS, so your aware of drive boot order and such. So you have Vista on 1st drive, Server on 2nd, and Ubuntu on some other drive ... correct? Look into burning a SuperGrub disk (Google for it). Sometimes it helps to understand grub better ...

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by manishtech on 2008-09-02
Plug in both the hard disk properly and post the output of the command

```
sudo fdisk -l
```

and the contents of the file **/boot/grub/menu.lst**

---

### Post by foodrules2me on 2008-09-02
Well, thank you for the replies, but I fixed it.
I had guessed it was the windows mbr, but didn't know how to take care of it but found something called VistaBootPro. Ha, actually kinda proud, set up Server's entry in grub all by myself:)

---

