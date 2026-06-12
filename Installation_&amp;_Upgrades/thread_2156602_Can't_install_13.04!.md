---
title: "Can't install 13.04!"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by soumoks on 2013-06-22
During the installation process,i select install alongside windows 7,after giving required space,i hit install system,it just stays there with no progress whatsoever,i waited for about half an hour before rebooting back into windows 7,the partition seems to be unaffected,since check disk couldn't pick up any errors.
How do install 13.04 on my system?

---

### Post by 2F4U on 2013-06-22
How many primary partitions are already on your system?

---

### Post by soumoks on 2013-06-22
Only 1 primary partition which has windows 7 installed
edit: just checked and ubuntu had created a partition.

---

### Post by 2F4U on 2013-06-22
Maybe the downloaded iso file is corrupt. Did you verify the checksum? Are you using usb or cd/dvd media to install?

---

### Post by soumoks on 2013-06-22
iso file is proper,using rw dvd

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]soumoks; Hi !

Can you boot the liveDVD in "try ubuntu" mode ? That will answer a lot of questions, and give a place to trouble shoot from.
[/COLOR][INDENT=2][COLOR=#000000]
try'n to help

[/COLOR][/INDENT]

---

### Post by soumoks on 2013-06-22
Yup!,i did the "try ubuntu" option and it worked flawlessly,just getting stuck at the partitioning stage :(

---

### Post by sudodus on 2013-06-23
Please mount all partitions that you can mount (using the file browser in the live session) and post the output of the following commands

```
 sudo fdisk -lu
```
```
 sudo parted -l
```
```
 sudo blkid
```
```
 sudo df
```

And please describe the computer, at least CPU, RAM, graphics card (just to be sure, it should work, since you see it work in the live session). It is particularly important that there is enough RAM for the installer. If not you may have better luck installing from the alternate iso file.

---

### Post by soumoks on 2013-06-23
edit: tried again with a usb stick and worked like a charm!,thanks a lot guys :)

---

