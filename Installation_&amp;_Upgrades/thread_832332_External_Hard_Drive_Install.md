---
title: "External Hard Drive Install"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by connord94 on 2008-06-17
OK, So, I installed ubuntu on my 80gb USB HDD, (Still have a partition for storage, though) But when I try to boot from it I get 
'Grub Error22:No Such Partition' 
I have read multiple things about it, and I know the menu.lst needs changed, and I *think* it is
```
root (hd1,4)
```
that needs changed, but what to?

I also saw someone elses similar problem being solved, In which they had to change some sort of list of devices to boot from ??

How can I fix my problem and boot into the ubuntu installation?

The External Drive shows this up with fdisk -l (from the LiveCD)
```

sdb1 <all of the block stuff> HPFS/NTFS   (I know this is my partition for storage)
sdb2 <block crap> Extended
sdb5 <block crap> Linux
sdb6 <block crap> Linux Swap/Solaris

```

I would also like to continue using the Windows boot loader, for when the USB Drive isn't plugged in, as I have an XP/Vista Dual boot.

Help booting would be greatly appreciated.


Connor

---

### Post by Pumalite on 2008-06-17
Herman and mierfra are the guys to consult here, but I think you have to edit your external's menu.lst and change 'groot' and 'root' to (hd0,0)

---

### Post by connord94 on 2008-06-19
But wouldn't that change the windows MBR? The external drive (as far as I know) should be HD1.


???

Connor

---

### Post by Pumalite on 2008-06-19
When you boot the USB; the USB is (hd0) If that doesn't work; try reinstalling it's own Grub to the USB.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by meierfra. on 2008-06-19
Don't reinstall grub. Just change "root (hd1,4)" to  "root (hd0,4)".  "# groot=(hd1,4)" needs to be changed,  too

---

### Post by connord94 on 2008-06-21
How do I change these permenantly?
The only way I can change them resets to default after a failed boot/restart.

I'm guessing I need to enter the grub CLI and do it that way? How?


Thanks a lot,
Connor

---

### Post by meierfra. on 2008-06-21
Open a terminal (Applications->Accessories->Terminal)

To open the file "menu.lst" type 


```
gksudo gedit /boot/grub/menu.lst
```
(l is a lower case L)


Change "# groot=(hd1,4)" to "# groot=(hd0,4)"

Save the file.

Once you fixed "groot" the next command will  automatically change all   "root (hd1,4)" into "root (hd0,4)":

```
sudo update-grub
```

---

### Post by connord94 on 2008-06-21
Thanks a lot meierfra!

---

### Post by meierfra. on 2008-06-21
You are welcome. Glad to be of help.

---

