---
title: "Can't boot anything, grub rescue prompt"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by nautica17 on 2010-06-19
So I had Ubuntu Server installed and I decided to make some new partitions using gparted via a live usb of Ubuntu desktop. And so I think messed up pretty badly. Ubuntu Server won't boot and I get the following error followed by a grub rescue promt: 
```

Diskette drive 0 seek failure
error: file not found
grub rescue > 

```To me, it seems like some boot files may be missing if not the whole system. After I made the partitions, the live USB of Ubuntu was still working fine until I rebooted.

So here is the bigger issue, I figured I would just reinstall everything all over again, but instead I can't. I can only do installations from the usb drive (was like that from the beginning on this computer), and when I try to install Ubuntu server or anything for that matter, I get the following problem:
```

Try (hd0,0): FAT32 : No GRLDR
Try (hd0,1): invalid or null
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (hd1,0): EXT2: No grldr
Try (hd1,1): non-MS: skip
Try (hd1,2): EXT2: _

```
The underscore on the last line keep blinking.

The grldr thing seems to be from GRUB4DOS that I once had on the drive. None the less, is there anything I can do in grub rescue to fix this issue? Any ways to wipe the disk clean?

---

### Post by oldfred on 2010-06-19
Just so we can see what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by nautica17 on 2010-06-19
> **oldfred said:**
> Just so we can see what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

See, that's part of the problem though. I can't boot into anything to use that script.

---

### Post by darkod on 2010-06-19
> **nautica17 said:**
> See, that's part of the problem though. I can't boot into anything to use that script.

How about the Desktop live usb?

---

### Post by nautica17 on 2010-06-19
> **darkod said:**
> How about the Desktop live usb?
I tried that. I'm thinking now maybe my usb drive is just bad since I've used it so much. Going to try a new usb drive and see if that works maybe. I'm desperate at this point.

---

### Post by darkod on 2010-06-19
I was just about to say, the messages you are getting about errors trying to boot, come from the hdd. There is no way to get those messages if booting from the stick.

You should be able to boot from the stick and reinstall if that's what you want (no data to try to save).

As long as your usb stick is good.

---

### Post by nautica17 on 2010-06-19
Okay, I fixed the problem. It turns out my usb drive was indeed corrupted. Darn things..

---

