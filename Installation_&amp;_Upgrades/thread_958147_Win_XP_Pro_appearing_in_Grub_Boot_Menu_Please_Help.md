---
title: "Win XP Pro appearing in Grub Boot Menu?? Please Help."
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by apple_head on 2008-10-25
Hi Guys
I have Triple booted Windows Vista, Windows XP Pro and Ubuntu 8.04 over two Hard Disks.

I have Win Vista on my SATA HDD and XP and Ubuntu on my IDE slave. However when I partitioned my IDE slave during Ubuntu install I made a 40GB Partition for Ubuntu (5GB used for SWAP, and another 40GB Partition for XP Pro. Once it was Installed Grub was installed it asked me which to boot as if Ubuntu was installed to my SATA HDD? This is fine however how do I get Windows XP Pro appear in the list? As I have to press F8 at post to boot XP as it only boots XP and not Ubuntu from that way?

Sorry if post sounds confusing. Thanks for help in advance.

---

### Post by bulldog on 2008-10-25
Open with a text editor like gedit as root your menu.lst/
```
gksu gedit /boot/grub/menu.lst
```
If your windows is on a secondary hard-disk then you want to add these lines to the end of your /boot/grub/menu.lst -file

title Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

---

### Post by apple_head on 2008-10-25
Hi Bulldog
Thank you It worked :D

---

### Post by celticbhoy on 2008-10-25
why give 5g to swap?

---

