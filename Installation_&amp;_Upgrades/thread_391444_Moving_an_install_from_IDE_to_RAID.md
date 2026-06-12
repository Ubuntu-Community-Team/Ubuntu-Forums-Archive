---
title: "Moving an install from IDE to RAID"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by DJMatty on 2007-03-23
Hi

I am still trying to get Ubuntu installed on my Striker Extreme system on the raided drives.

I have had success in getting feisty installed on my SATA drive, I have got the nvidia drivers installed and the network is now working (after using the msi msix options), and I have dmraid installed and can see my raid drive partitions. I also modified the initrd to include udevsettle to allow dmraid to load properly before it boots to it.

I was reading a How-to on installing to the raid drives using an already installed system on and IDE or USB drive, by copying the root and boot from the IDE to the raid partitions.

I thought I'd give this a try as all the other ways of installing it I have tried have not worked.

So I mounted the partitions, copied the files (using 'cp -r') and then modified the fstab file to use the raid partitions rather than the SATA ones, and then modified menu.lst to give me an option to boot into that partition too.

This booted up and started to load, but then it started saying that some of the files that it was using did not have the correct owner and this stopped the boot into gnome, and left me at a login prompt. However, none of the users that were in the SATA system would work in the RAID system.

Is this a valid way to move a working install from one machine to another? Should I use the '-a' switch of cp to do the copy? Should I chroot to the destination system and create the users again after the copy?

I think I am really close to getting everything working now, just need to get over this final hurdle...

Thanks

Matt

---

### Post by sdumper on 2007-04-06
matt how did you get your network to work im stuck...

---

### Post by DJMatty on 2007-04-06
Hi

I edited /etc/modprobe.d/options and added the line 

```
options forcedeth msi=0 msix=0
```

then you can do:

```
modprobe -r forcedeth
modprobe forcedeth
/etc/init.d/networking restart
```

and that resets the network and it all started working for me on my striker extreme.

Matt

---

### Post by sdumper on 2007-04-06
Matt ill try this when i get home thanks!!!

---

### Post by sdumper on 2007-04-07
Matt I followed your instructions and I get an msi not recognized or found error...do I need to set something up so that msi is recognized?

---

### Post by sdumper on 2007-04-07
Also did you disable one of your lan ports in the bios?
Last which lan port did you plug your cat5 cable into?

---

