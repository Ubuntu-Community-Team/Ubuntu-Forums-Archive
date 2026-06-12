---
title: "Mapping grub devices to physical drives"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2008-06-06
I have two IDE drives (sda=primary master and sdb=secondary slave) and two SATA drives (sdc=slot 0, sdd=slot 1). 

I would like to install the bootloader on sdc and sdd so that I can boot off either by configuring the BIOS boot sequence (setting up RAID...). The system currently boots off a RAID array made up of sda1+sdb1. 

I've pored over the grub docs for ages but I just can't decide: what should I substitute for [COLOR="Red"]X[/COLOR] below ?

```
$ sudo grub 
grub> root (hd[COLOR="Red"]X[/COLOR],0)
grub> setup (hd[COLOR="Red"]X[/COLOR])
grub> quit
```

---

