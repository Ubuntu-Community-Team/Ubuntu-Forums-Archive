---
title: "Formatted, installed XP, then 8.10, but its not dual booting"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by Les Oeufs on 2008-11-06
I guess the problem is pretty much outlined in the title. If I remember correctly, the last time I did this, all I had to do to dual boot was install one, then the other, and then GRUB just kicked in when I started my pc. But now when I turn on my pc, it just goes to XP. There's no dual booting option. The installation seemed to go fine, and the C drive has been resized accordingly in XP, but I cant get at Ubuntu. Can anyone give me a hand?

---

### Post by caljohnsmith on 2008-11-06
How about booting your Live CD, open a terminal (Applications > Accessories > Terminal), and posting:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by Les Oeufs on 2008-11-06
Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcf11cf11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   234372284   117186111    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5fea45c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   204635969   102317953+   7  HPFS/NTFS
/dev/sdb2       204635970   625137344   210250687+   5  Extended
/dev/sdb5       204636033   619096904   207230436   83  Linux
/dev/sdb6       619096968   625137344     3020188+  82  Linux swap / Solaris

sda returned grub, sdb returned "missing operating system". The hexdump thing on sda gave

0000000 8104                                   
0000002

seems like bad news because both os's are installed on sdb

---

### Post by caljohnsmith on 2008-11-06
OK, the output of those commands clears up the ambiguity, because if you are booting directly into Windows, you must be booting from the sdb drive right now on start up. What happened is Grub was installed to the MBR of your sda drive, not sdb, so sdb still has a Windows MBR which will cause you to boot directly into Windows. 

The solution to your problem should be simple; from your Live CD, do the following:
```
sudo grub
grub> root (hd1,4)
grub> setup (hd1)
grub> quit
```
Reboot, and you should get the Grub menu now. If you have any problems booting Windows or Ubuntu from the Grub menu, let me know. Otherwise let me know how it goes.

---

### Post by Les Oeufs on 2008-11-06
Thanks! Worked like a charm!

---

### Post by caljohnsmith on 2008-11-06
Glad to hear it worked, and I'm glad your problem turned out to be something simple. Cheers and have fun with Ubuntu. :)

---

### Post by Les Oeufs on 2008-11-06
Ah no! I know this isnt linux, but I just tried booting into XP for the first time and now it says "NTLDR missing press control-alt-delete to restart"
I've been looking into it, and NTLDR has something to do with the boot sector. Not sure if grub just screwed something up for windows. Anyone have any suggestions?

---

### Post by caljohnsmith on 2008-11-06
What entry are you using for Windows in your /boot/grub/menu.lst? How about opening your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very end, add the following two entries for Windows:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title Windows XP (hd0)
root (hd0,0)
chainloader +1
```
One of those entries will most likely work to boot Windows. If not, let me know exactly what happens when you select each of them from the Grub menu, and also please clarify whether Windows is on the Ubuntu drive or the other drive. Let me know how it goes. :)

---

### Post by Les Oeufs on 2008-11-06
Man you're awesome. OK, I'm going to shove those in and give it a shot.

edit: And XP is on the same drive as Ubuntu

---

### Post by Les Oeufs on 2008-11-06
Posting from Windows. The hd0 entry worked. Man, if I lived in California I'd totally drive down and buy you a drink

---

### Post by caljohnsmith on 2008-11-06
> **Les Oeufs said:**
> Posting from Windows. The hd0 entry worked. Man, if I lived in California I'd totally drive down and buy you a drink
That's great news, glad it worked. Since I can't take you up on your kind offer for a drink, if you want you can always "pay it forward", i.e. help someone else (doesn't have to be computer related even), and that would make me happy. Cheers and have fun with Ubuntu. :)

---

