---
title: "Partition still showing 'Windows 7 loader'"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by 303 on 2010-04-30
I was dual-booting XP/Win7...
Uninstalled Win7 and reset boot loader with XP's
Went to install 10.04 for dual-boot and it is showing that loader as "Widows 7 loader"
why??

---

### Post by oldfred on 2010-04-30
Windows combines it boot loaders into the boot or active partition. You are still seeing bits of that combination. I thought the repair of the XP partition would have fixed it, but grub must still see something still configured as a win7 partition.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by kansasnoob on 2010-04-30
Also always boot into your Ubuntu and run:

```
sudo update-grub
```

after any changes!

---

### Post by 303 on 2010-04-30
> **kansasnoob said:**
> Also always boot into your Ubuntu and run:

```
sudo update-grub
```

after any changes!

*After* I install 10.04?

---

### Post by oldfred on 2010-05-01
If you run this I think it will show your windows XP partition at a win7 partition.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by 303 on 2010-05-04
> **oldfred said:**
> If you run this I think it will show your windows XP partition at a win7 partition.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.



Is there a way to do this without installing/booting 10.04?
ie. in XP?

---

### Post by wilee-nilee on 2010-05-04
Post the script if you really want to fix it.

---

### Post by 303 on 2010-05-17
> **wilee-nilee said:**
> Post the script if you really want to fix it.

[http://pastebin.com/ASFgKU6d](http://pastebin.com/ASFgKU6d)

---

### Post by oldfred on 2010-05-17
It is easier if you post here and put code tags.

/bootmgr /Boot/BCD are in your XP partition and are win7 files. Grub must see these and assume that it is a win7 boot partition.

rename or move to another place. if system is ok you can delete later.
After moving rerun the sudo update-grub

---

### Post by halversondm on 2010-05-17
I tried oldfred's suggested course of action and now my computer is operating as expected.  Thanks, oldfred.
 
Dan

---

### Post by 303 on 2010-05-19
> **oldfred said:**
> It is easier if you post here and put code tags.
-Uhh.... what??

/bootmgr /Boot/BCD are in your XP partition and are win7 files. Grub must see these and assume that it is a win7 boot partition.
-ok?


rename or move to another place. if system is ok you can delete later.
After moving rerun the sudo update-grub
-how do I do "rename or move"?

---

### Post by oldfred on 2010-05-19
To rename something you normally just right click on it and choose rename. Just put any letters in so it is not seen as the standard file. If that works and system still is ok then you can delete.

Code tags preserve formating. You highlight code in the message area and then click on the # in the edit panel above the message area. Mouse over the # when editing & it shows you they are code tags.

---

