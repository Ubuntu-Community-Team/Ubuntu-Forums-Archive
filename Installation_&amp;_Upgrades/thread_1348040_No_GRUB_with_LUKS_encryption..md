---
title: "No GRUB with LUKS encryption."
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by kYd on 2009-12-06
Hi, 

I recently formatted and re-installed and added LUKS encryption all my drive partitions (apart from boot), however, I am now unable to boot to GRUB.

On reboot I am presented with a black screen and just a blinking cursor in the top left corner, I've had this error before which I could easily solve by re-installing the GRUB, but this is not working.

I am able to boot the computer by using a USB stick and editing the GRUB as such to boot off my HD.

**fstab**
```

Name	Flags	Part Type	FS Type	    Label      Size (MB)
  
sda1    Boot    Primary         Linux ext3  Boot       98.71         
sda2            Primary         Linux       Root       10240.48
sda3            Primary         Linux       NewOS      6144.29
sda5            Logical         Linux       NewOS2     6144.29
sda6            Logical         Linux       Var        8192.38
sda7            Logical         Linux       Temp       2048.10
sda8            Logical         Linux       Swap       2048.10
sda9            Logical         Linux       Home       6144.29
sda10           Logical         Linux       Music      66558.97
sda11           Logical         Linux       Pictures   3068.03
sda12           Logical         Linux       Videos     25597.08
sda13           Logical         Linux       Docuements 4096.19
sda14           Logical         Linux       Downloads  9212.32
sda15           Logical         Linux ext3  MiscNoEnc  10446.11


```
Thanks.

---

### Post by kYd on 2009-12-07
Any ideas with this, please?
It's been like it for over a week now.

---

### Post by kYd on 2009-12-07
No one please?

---

