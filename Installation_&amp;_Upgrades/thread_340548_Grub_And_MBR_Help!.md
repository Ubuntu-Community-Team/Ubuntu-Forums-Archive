---
title: "Grub And MBR Help!"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by StreetSmart on 2007-01-17
The problem is that when windows vista installs, it will overwrite the mbr and that will disable grub. How would I restore grub after windows vista has installed? My partition table looks like this.

Hard Drive 80gb (/dev/sda)

[50gb sda1 /home] 
[14gb sda2 Ubuntu Edgy] 
[14 gb sda3 (Windows vista will be installed here)]
[2gb  sda4 Swap]

Ill attach my menu.lst from grub as well just in case anybody needs it. 

[http://pastebin.ca/319626](http://pastebin.ca/319626)

Thanks.

---

### Post by Drate on 2007-01-17
Try this, I am about to, we can see if it works for either of us.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by N'Jal on 2007-01-17
I can confirm that it will work, so long as you ensure that you install grub to the MBR, as long as grub is installed into the mbr vista will play nice. I done it myself using vista.

---

### Post by allwin on 2007-01-17
I did something similar (Windows ME), and I had to use the setup(hd0) option to write GRUB to the MBR in order to get a bootable disk.  The link in the earlier post tells it with less than crystal clarity in step 6, and suggests using setup(hd0,x).  I tried that first and it wouldn't boot.

---

