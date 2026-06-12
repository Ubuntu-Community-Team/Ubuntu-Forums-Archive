---
title: "Installing on MicroSD for Raspberry Pi and got error:"
date: 2016-11-22
forum: Installation &amp; Upgrades
---

### Post by jasonbunnell on 2016-11-22
I am installing Ubuntu onto a MicroSD card with 64GB from a OSX using [this guide]("https://developer.ubuntu.com/en/snappy/start/raspberry-pi-2/").  Getting trouble with this command:
```
sudo dd if=~/Downloads/ubuntu-core-16-pi3.img of=/dev/rdisk2 bs=32MB
```

I get this error:
```
dd: bs: illegal numeric value
```

Tried going through a few times.  The SD card is definitely disk 2.  Double checked the .img file name.  What am I doing wrong?

---

### Post by sudodus on 2016-11-22
Welcome to the Ubuntu Forums :-)

I have found that ```
bs=4096
``` works well in many computers. Smaller chunks of data (default is 512 bytes) makes the transfer slower, but larger chunks will not really improve things (at least when I tested).

I have not much experience of MacOS, so I have to believe that the target drive is seen as /dev/rdisk2 ;-)

Otherwise you can probably check with the command

```
sudo lsblk -f
```
and
```
sudo lsblk -m
```

to get help to identify the target drive (the card).

---

### Post by QIII on 2016-11-22
I would also cut down on complexity by navigating into the containing directory.

---

### Post by spjackson on 2016-11-22
I think that the OSX equivalent of 
```
bs=32MB
```
is
```
bs=32m
```

---

