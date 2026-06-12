---
title: "Dual boot issues"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Colo2 on 2011-04-29
I have no idea whats going on. I've managed to dual boot in the past just fine. 

So we install Windows 7 home premium. Then in goes the Ubuntu Disk. Ubuntu seems to think that the windows 7 partition is one big lump of unallocated space. Tried multiple re-installs of Windows 7, all concluding the same.

A bit of googling told me that it has something to do with partition tables or something. I even tried to use Gdisk to delete Gpt from the windows disk, which - as I have absolutely no idea what any of it means, - resulted in me screwing up the entire Win7 partition hence win7 not being able to boot anymore. 

All explinations and help i've seen on the internet include a lot of technical garble which I don't understand. I've been using Linux for a while, but as far as partitioning and dual booting is concerned, it's always gone smoothly for me up until now

Thanks for any ideas

Tom

---

### Post by srs5694 on 2011-04-29
Post the output of:

```

sudo gdisk -l /dev/sda

```

Please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

