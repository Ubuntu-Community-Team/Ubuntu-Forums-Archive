---
title: "Where art thou GRUB?"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Gene393 on 2010-07-15
Hi, recently I reinstalled windows 7, this stuffed up my ubuntu grub loader, because this isnt the first time Ive reinstalled windows, I found out that I had 8 ubuntu partitions (4 ubuntu, 4 linux swaps to power those ubuntu's) I used gparted to delete the 6 partitions I didnt need, but then the grub rescue mode came up, First I did this code into the terminal from a ubuntu live session 

```
sudo mount /dev/sda7 /mnt/
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
```
this made the grub turn into the same thing that happens when you type sudo grub into the terminal, from there I typed this code into the new grub loader thing

```
find /boot/grub/stage1
root (hd0,6)
```
I did hd0,6 'cos thats what the find command came up with

```
setup (hd0)
```
this came up with a few lines of code then done, so I now think that I have reinstalled grub, but my problem now is that i can't get back to the standard grub interface, its still as if I had typed sudo grub into the terminal, but I can't type quit to quit out of it

---

### Post by oldfred on 2010-07-16
With things getting moved around, run this from a liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

