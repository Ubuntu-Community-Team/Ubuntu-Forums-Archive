---
title: "Install of Ubuntu 10.04 LTS leads to grub prompt"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by joy_deep on 2013-01-19
Hello,

I just installed Ubuntu 10.04 from a Live CD. My laptop has WinXP installed. After installation when I restarted my laptop I ended up in GRUB prompt. I checked in this forum and found if I put below commands I can login to Ubuntu.
```

linux /vmlinuz root=/dev/sda8
initrd /initrd.img
boot

```
Here is my bootinfo :[http://paste.ubuntu.com/1548867]("http://paste.ubuntu.com/1548867")

But I cannot get Grub menu and boot WinXP. 
Please help.

Thanks!

---

### Post by mörgæs on 2013-01-19
First I wouldn't install 10.04, as it has only a few months left of support. 

If you do a fresh install of 12.04 / 12.10 and still have problems double booting, [Boot-repair]("https://help.ubuntu.com/community/Boot-Repair") is a good option.

---

### Post by joy_deep on 2013-01-19
My Laptop is Compaq Presario 2100 having 512MB RAM. I tried with Ubuntu (or other Ubuntu flavored distro like Mint) latest version. But could not install into my laptop. I am already having this CD. So I tried with that CD.

---

### Post by ibjsb4 on 2013-01-19
Did you use the option to try Ubuntu before installing just to make sure that old CD is still working?

And even with 10o4, half a gig of ram is pushing your luck.  I would go with Xubuntu 12o4, its an LTS (long term support) and uses less resources.

---

### Post by joy_deep on 2013-01-19
I tried with 10.04. Even I am replying with Ubuntu 10. If I could install it right then I shall upgrade it to 12.

---

### Post by YannBuntu on 2013-01-20
Hello

1) as morgaes said, better use 12.10 (or 12.04 for longer support but older software)
2) Boot-Repair indicates:
```
The boot files of [The OS now in use - Ubuntu 10.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

```

You can either create a /boot partition as indicated, or via Gparted reduce your sda8 partition from 57 to 25GB.

---

### Post by mörgæs on 2013-01-23
An updated BIOS might give you more freedom to partition as you please. Not a guarantee though.

---

