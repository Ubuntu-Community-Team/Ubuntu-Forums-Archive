---
title: "Grub Headaches - Neither System Boots"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by goofeyfoot on 2008-06-14
Hello:

I had to reinstall Ubuntu because of general problems.

My windows drive is about the fourth hard drive down in BIOS.

My Ubuntu Drive is the third drive down in Bios.

The second drive is a backup drive of sorts.

All the above drives are Sata.

My first (and only) IDE drive has a bunch of personal stuff on it.  Files and so forth.

When I got done putting the Ubuntu on, I made that third drive the "boot" drive in BIOS.  That gives me a Grub menu on startup.  But from that menu I can't get to either Ubuntu or Windows.  I just get errors saying that Grub doesn't find what it expects there.

If I change BIOS to boot from my Windows drive first, then XP boots normally and everything works fine.

So the question is, how can I change grub and the menu.lst thing so that (a) they point where they are supposed to? and (b) I can dual boot from the grub the way I should be able to?

There has to be a relatively simple way of doing this without being a programming wizard.

Thanks for your help.

Michael

---

### Post by meierfra. on 2008-06-14
> When I got done putting the Ubuntu on, I made that third drive the "boot" drive in BIOS. That gives me a Grub menu on startup. 


At the grub menu, select Ubuntu, but do not press enter. Press "e" instead. At the new screen press "e" again. You get a line which looks like


root (hd3,2)

but of course the numbers might be different, 

Change it do

root (hd0,2)

So change the first number to zero, but  do not change anything else.
Press "enter" and then "b" to boot.

This should boot you into ubuntu. Once you booted into Ubuntu, you still need to make this change permanent:

Open a terminal and type


```
gksudo gedit /boot/grub/menu.lst
```

(l is a lowercase L)

change

# groot=(hd3,2)

to

# groot=(hd0,2)

(so again just change the first number to 0)

Save the file. Then in the terminal:

```
 sudo update-grub
```


For help with booting Windows from the grub menu post the output of

```
sudo fdisk -l
```

(again l is a lowercase L)
__________________

---

### Post by goofeyfoot on 2008-06-14
OK:

I will give that a try and see what happens.

Will get back to you on this.

Thanks.

Michael

---

### Post by goofeyfoot on 2008-06-14
> **goofeyfoot said:**
> OK:

I will give that a try and see what happens.

Will get back to you on this.

Thanks.

Michael

OK I'm Back Here is the fdisk -l thing:

Maybe after you look at this you will know what I need to do to get the windows XP system going.  By the way, to get to Ubuntu I had to edit the grub menu with "(hd1,0).  Then Ubuntu started right up.

Thanks again.

Michael


michael@michael-desktop:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf06af06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30139   242091486   83  Linux
/dev/sda2           30140       30515     3020220    5  Extended
/dev/sda5           30140       30515     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d726

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa48ba48b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         608     4883728+   b  W95 FAT32
/dev/sdc2             609       30401   239312272+   f  W95 Ext'd (LBA)
/dev/sdc5             609       15505   119660121    7  HPFS/NTFS
/dev/sdc6           15506       30401   119652088+   7  HPFS/NTFS

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ab91c2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       12161    97683201    7  HPFS/NTFS
/dev/sdd2           12162       24321    97675200    5  Extended
/dev/sdd5           12162       24321    97675168+   7  HPFS/NTFS
michael@michael-desktop:~$

---

### Post by meierfra. on 2008-06-14
> to get to Ubuntu I had to edit the grub menu with "(hd1,0). 

O.K but then you are not booting from the ubuntu drive. (Or something really  strange is  going on.)

For Windows  try one of these:


title Windows XP
root (hd0,0)
makeactive 
chainloader +1


title Windows XP
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1

title Windows XP
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
makeactive
chainloader +1

(you could also try with "1" in place of the "3", but that should not work since Ubuntu is on (hd1,0))


What is on the 500GB drive (sdb)? Is it unformated?

---

### Post by goofeyfoot on 2008-06-14
> **meierfra. said:**
> O.K but then you are not booting from the ubuntu drive. (Or something really  strange is  going on.)

For Windows  try one of these:


title Windows XP
root (hd0,0)
makeactive 
chainloader +1


title Windows XP
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1

title Windows XP
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
makeactive
chainloader +1

Thanks again.

Michael


(you could also try with "1" in place of the "3", but that should not work since Ubuntu is on (hd1,0))


What is on the 500GB drive (sdb)? Is it unformated?

Yes the 500 GB is currently unformatted.  I am going to fix that real soon.

So on the other point, I can't say why ubuntu is working but believe me, it is.  I made the change in menu list and it works perfectly.

As far as your above suggestions do I try them from grub or do I put them right in menulst?

Thanks for your advice.  I'm really optimistic that this is going to work.

Best regards.

Michael

---

### Post by meierfra. on 2008-06-14
Just add them all to menu.lst.  (Of course once you figured out which one is working, deleted all the others)

---

### Post by goofeyfoot on 2008-06-14
> **meierfra. said:**
> Just add them all to menu.lst.  (Of course once you figured out which one is working, deleted all the others)

Meirfra:

Yep, that did it.  All I did was paste in your last solution (cuz it's always that last one that works, you know?)and Windows XP fired up perfectly.

So the net result is that Ubuntu works and Windows works, so I am a happy camper.  

I want to thank you for your assistance.

Best regards.

Michael

---

