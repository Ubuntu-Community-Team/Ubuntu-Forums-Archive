---
title: "How to change bootloader"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by rozner on 2010-10-16
Hello,

I have two installs on the same drive but different partitions. First I installed XBMC live which is based on Ubuntu (I don't know the exact verion but I think it's in the 9.x). 

Then I installed full Ubuntu 10.04 on another partition. 

Now it uses grub2 off the second partition. I configured it to boot XBMC as default and I've had no issues with it. However in the end I rarely use Ubuntu since this is really HTPC. I thought maybe it would be cool to check emails and do some web browsing on my TV, but it turns out I prefer just using a regular computer for that. So I want to delete the partition, but I'm worried doing so will make the system not boot anymore unless if I reinstall XBMC live, I don't want to do that either since I've got it configured all properly and I don't want to mess that up. 

So I believe I have to change the MBR to point to the XBMC partition although I haven't quite figured out how to do that.

Thanks for any help with this.

---

### Post by VMC on 2010-10-16
Do you know the partition# of the XBMC? You can boot up then edit the grub menu of the XBMC to find it, then do the following from a livecd.

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

XY = partition# of XBMC

---

### Post by ronparent on 2010-10-16
You just need decide which grub you want to use and reinstall it to the partition you are retaining. If you want to retain grub 2 just load the live cd containing it and reinstall according to this (if grub 2): [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2
The reinstallation should find the XBMC partition automatically when the boot menu is generated. You will have to identify it fir the install.

---

