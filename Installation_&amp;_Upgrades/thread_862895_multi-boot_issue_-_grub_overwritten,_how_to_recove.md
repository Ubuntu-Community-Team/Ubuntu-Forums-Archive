---
title: "multi-boot issue - grub overwritten, how to recover?"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by Donny Bahama on 2008-07-17
I had to do a system recovery of my Vista partition, which wrote a new MBR and clobbered grub. I'm fairly new to Linux and not sure how to restore grub (and move it to somewhere other than the first sector of the drive) so that I can boot both Linux and Vista. Can someone please point me in the right direction?

Thanks for your time and consideration.

---

### Post by dreadmeat on 2008-07-17
[supergrubdisk]("http://www.supergrubdisk.org/") helped me a lot.

---

### Post by arpanaut on 2008-07-17
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Many recomend this solution to dual booting with Vista,

---

### Post by smo0th on 2008-07-18
you can recover GRUB by booting with the live cd and typing the following in a terminal:

```
sudo grub
grub> find /boot/grub/stage1

```now, assuming your linux partition is in (hd0,0): 
```
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

```
now restart, your GRUB should be recovered

---

### Post by richlyn9 on 2008-07-18
This is the set of commands to solve your query,

First boot from the ubuntu live cd and select the start ubuntu option.
when in ubuntu type the following commands in a terminal

(command prompt)

1)
 ~:$ sudo grub
now will get a grub prompt as below,

2)
grub> find /boot/grub/stage1
As output u will get something like below, you will get atleast one entry.
(hd0,1)
(hd0,3)

3)
Then type
grub> root (hd0,x)   --where x is the number of partition where grub
is already installed. so substitute x accordingly.

4)
grub> setup (hd0)

Output will be something like,

Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

5)
grub> quit

Thats it now reboot the computer and ubuntu will be detected

---

### Post by smo0th on 2008-07-18
lol... nice work saying again things :)

---

### Post by Donny Bahama on 2008-07-20
> **richlyn9 said:**
> 
2)
grub> find /boot/grub/stage1
As output u will get something like below, you will get atleast one entry.
(hd0,1)
(hd0,3)Thanks for the nicely detailed response. Unfortunately, I didn't get what I should have...

grub> find /boot/grub/stage1

Error 15: File not found

I'm guessing this is because the MBR was wiped by Vista during the recovery process. (This is not a typical Vista installation but rather a "System Recovery" - restoring the notebook back to factory defaults, just as it was the day I pulled it out of the box.)

---

### Post by louieb on 2008-07-20
Sounds like restoring VISA not only wiped GRUB off the MBR but wiped Ubuntu off the hard drive.  

Back to the live cd and the terminal look at the partition table and see if there is a partition of** type Linux**

```
sudo fdisk -l 
```(lowercase L at the end)

At least you'll know if you have to reinstall. good luck.

---

### Post by smo0th on 2008-07-20
using [supergrub]("http://www.supergrubdisk.org/") CD/USB may fix your boot

---

