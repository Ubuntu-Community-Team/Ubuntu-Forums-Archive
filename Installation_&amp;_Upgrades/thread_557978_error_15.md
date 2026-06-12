---
title: "error 15"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by enzopol on 2007-09-23
Hello,

After installing Ubuntu 7.04 i am unable to run earlier functioning windows.  Sorry, I tried helping myself but I am simply confused.

Please help me.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   245762369   122881153+   7  HPFS/NTFS
/dev/sda2       245762370   488392064   121314847+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   124021799    62010868+   7  HPFS/NTFS
/dev/sdb2       247802625   488392064   120294720    7  HPFS/NTFS
/dev/sdb3       124021800   242661824    59320012+  83  Linux
/dev/sdb4       242661825   247802624     2570400    5  Extended
/dev/sdb5       242661888   242677889        8001   82  Linux swap / Solaris
/dev/sdb6   *   242677953   247449194     2385621   83  Linux
/dev/sdb7       247449258   247802624      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order



Thank you for your guidance,

Renz

---

### Post by Pumalite on 2007-09-23
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
Post:
cat /boot/grub/menu.lst

---

### Post by enzopol on 2007-09-23
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
Post:
cat /boot/grub/menu.lst

this is what i got

cat: /boot/grub/menu.lst: No such file or directory

---

### Post by Pumalite on 2007-09-23
I was under the impression that you were INSIDE you Ubuntu system.
If that's the case and you don't have menu.lst, then Grub is not installed, but then how did you get in Ubuntu?

---

### Post by enzopol on 2007-09-23
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
Post:
cat /boot/grub/menu.lst

> **Pumalite said:**
> I was under the impression that you were INSIDE you Ubuntu system.
If that's the case and you don't have menu.lst, then Grub is not installed, but then how did you get in Ubuntu?


The only way i can run my pc is by booting from the Ununtu CD.  I have no options booting from the hardisk - i only get error 15.

---

### Post by Pumalite on 2007-09-23
With the Live CD you can get inside your filesystem, you just have to mount the partition, and then access your folders.

---

### Post by enzopol on 2007-09-23
> **Pumalite said:**
> With the Live CD you can get inside your filesystem, you just have to mount the partition, and then access your folders.

Thank you for your time, but will be a little more specific.  

So i accessed the files, what should i look for, and what should i edit so my pc get back alive - both in Ubuntu and in Windowz

Appreciate your detailed guide, please

---

### Post by Pumalite on 2007-09-23
You have to edit your menu.lst. That's what I intended to help you with.

---

### Post by enzopol on 2007-09-23
> **Pumalite said:**
> You have to edit your menu.lst. That's what I intended to help you with.

Many thanks again, and that too is what i am hoping you will help me with.

Problem is, i have booted from the Live CD...and i failed to locate the menu.lst.

Please tell me what to do.

---

### Post by Pumalite on 2007-09-23
Go to terminal:
sudo mkdir /media/Ubuntuer
sudo mount -t ext3 /dev/sdb6 /media/ubuntuer
cat /media/ubuntuer/boot/grub/menu.lst

---

### Post by enzopol on 2007-09-23
> **Pumalite said:**
> Go to terminal:
sudo mkdir /media/Ubuntuer
sudo mount -t ext3 /dev/sdb6 /media/ubuntuer
cat /media/ubuntuer/boot/grub/menu.lst


This is what happened


ubuntu@ubuntu:~$ sudo mkdir /media/Ubuntuer
mkdir: cannot create directory `/media/Ubuntuer': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb6 /media/ubuntuer
mount: mount point /media/ubuntuer does not exist
ubuntu@ubuntu:~$ cat /media/ubuntuer/boot/grub/menu.lst
cat: /media/ubuntuer/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 


I dont think it went as it should be.

Waiting for the next move

---

### Post by Pumalite on 2007-09-23
Get a Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to CD as image.Boot from it. Mounts all drives/partitions on boot automatically.
Then post: cat /boot/grub/menu.lst

---

### Post by enzopol on 2007-09-23
> **Pumalite said:**
> Get a Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to CD as image.Boot from it. Mounts all drives/partitions on boot automatically.
Then post: cat /boot/grub/menu.lst

Oh my, I chose [ftp://ftp.kernel.org/pub/dist/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso](ftp://ftp.kernel.org/pub/dist/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso) and have started the 700mb painful download.

Isn't there anything we can try while waiting.

..on the verge of begging

---

### Post by Pumalite on 2007-09-23
Play cards.:guitar:

---

### Post by enzopol on 2007-09-23
> **Pumalite said:**
> Play cards.:guitar:

1% percent downloaded so far, 14 hours remain.

I hope the problem in your "quotation" will not come true before I have my pc back up and running.

Patience, patience, patience.

Think, think, think,

There really should be something that could be done about this rampant problem.

Still 1 percent, 22hours remaining . this is gonna take forever

---

### Post by enzopol on 2007-09-23
It's me again, hi,

my internet connection is not too good today, i am still at 4% after almost an hour.  I guess i will download the Knoppix Live CD tomorrow.   

Meanwhile, isn't there anything at all that i can try, PLEASE - anyone, someone, say something.

Thank you,

Renz

---

### Post by Pumalite on 2007-09-23
I think I gave the best instructions I could. If there is someone with a better solution I'm sure he will chime in.

---

### Post by enzopol on 2007-09-23
I am very sure you gave the best instruction, and I sure appreciate your efforts.  Its just that my internet connection is very slow, and with my pc's current situation, I am open for experimentation.

I am concerned how such a supposed simple task of installing Ubuntu can go this wrong.  It too can be a turn-off for one without prior knowledge of Linux.

This installation is my eleventh (mostly for friends) and I am glad this problem occurred on my own pc, I would have been a real embarrassment.

Some sort of a utility could come in very handy in such cases, or better yet, the installation CD could be improved.

...just thinking out loud - and still can't believe this happened to me - and to make it worst, i have not the faintest idea what caused this predicament.

Thank you again.

Renz

PS:  I purposely got this Dell cuz I know Dell is a supporter of our common cause.

---

### Post by Pumalite on 2007-09-23
Don't be so sure. The Ubuntu installations of Dell are a problem for anyone wanting to install another OS in that machine.

---

### Post by enzopol on 2007-09-23
You sure know more in that regard, and you surely have your reasons.  My question now: Does mean that even after i download the Knoppix CD, i "may" still face the same problem.

More on a fishing expedition, I really wish you can expound on what possibly caused this problem (if you've got the time). Do you think that a possible cause is because all my partitions were Primary partitions.  I took note of that but I did not give it any meaning then.  As you may have noted; i have two 250 GB hardisks.  the first one is split in two (both windows) and i installed Linux on the second Hardisk (it too was originally split in two but during the first installation of Ununtu, the first half was used by Ubuntu after making some changes.

Ubuntu installed properly then, and gave me the grub normally but Ubuntu did not run, while windows continued running normally.  That made me re-install Ubuntu a second time in the hope of resolving the problem, and the rest is history (neither work from hard disk, i am running on a live cd for now).

Please join me in my fishing for possible faults, the solution may just be within grasp - i can hope, can't I.

Sorry for taking too much of your time,

Renz

---

### Post by Pumalite on 2007-09-23
Try re-installing Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Let's see what happens.

---

### Post by enzopol on 2007-09-25
Hello again, and yes, it still is me unable to find my way to the right solution.

I managed to download and have booted using Knoppix and wait for the steps to follow to rebuild/repair the grub file so that i can choose to boot either windowz or linux.  

Please help, anyone able to participate is very much welcome - two days without a normal pc is tough.

I am listing the following just to give you a clear picture of my HD.

Many thanks in advanced to all you kind hearted people in Linux'landia

just me,

Renz



   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       30401   121314847+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7720    62010868+   7  HPFS/NTFS
/dev/sdb2           15426       30401   120294720    7  HPFS/NTFS
/dev/sdb3            7721       15105    59320012+  83  Linux
/dev/sdb4           15106       15425     2570400    5  Extended
/dev/sdb5           15106       15106        8001   82  Linux swap / Solaris
/dev/sdb6   *       15107       15403     2385621   83  Linux
/dev/sdb7           15404       15425      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Pumalite on 2007-09-25
Ubuntu is in sdb6. Let's see your menu.lst. Post:
cat /boot/grub/menu.lst ( from Knoppix and from appropriate partition sdb6; look in /media or /mnt)

---

