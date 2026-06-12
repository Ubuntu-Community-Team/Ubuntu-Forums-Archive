---
title: "install issues with partion editor"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by ginestre on 2008-10-19
Hello. I'm wanting to put Hardy on a dual boot machine, the other boot being XP. The machine was previously Feisty/XP. I've decided to do clean installs of everything so as to clear out the attic, as it were.

After reinstalling XP on its own partition, I launch the live CD for Hardy. No problems until I get to the partition editor: it does not see the HD, which is still partitioned exactly as it was under Feisty. Any ideas anyone?

---

### Post by ginestre on 2008-10-20
<BUMP> and more info

The partition editor options are all greyed out at step 4 of 7 - preparation of the hard disk - and I get an error message saying that no root file system has been defined (which is true, because the partitioner doesn't give me any options to anything at all).

Additionally, I now notice that the new Places browse function on the left doesn't contain any reference whatsoever anywhere to the HD. It seems it is just invisible. If I look in /media, it's empty. 

Any ideas?

TIA, as always.

---

### Post by Ususbuntung on 2008-10-20
hi, when you are in hardy desktop, can it see the disk?
i mean if you click place home etc, your disk is well seen?

---

### Post by ginestre on 2008-10-20
> **Ususbuntung said:**
> hi, when you are in hardy desktop, can it see the disk?
i mean if you click place home etc, your disk is well seen?

No. There's nothing there at all.

---

### Post by az on 2008-10-20
I have seen the Windows install disk tie the partition table into a knot when trying to deal with preexisting linux partitions.  What does

cat /proc/partitions 

show?  (Run it from the live cd.)

As well, what does

sudo lshw -C disk -short

show?

If you can see the drive using the above commands, then I would suspect the partition table is corrupt and needs to be fixed (is is simple to do - use Testdisk)

---

### Post by ginestre on 2008-10-20
thanks. This is what I get

> **az said:**
> 

cat /proc/partitions 

show?  (Run it from the live cd.)

As well, what does

sudo lshw -C disk -short

show?


ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name

   7     0     685352 loop0
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo lshw -C disk -short
H/W path               Device      Class       Description
==========================================================
/0/100/1c/0.1/0.0.0    /dev/cdrom  disk        DVDRAM GSA-H42N
/0/100/1c/0.1/0.0.0/0  /dev/cdrom  disk        
ubuntu@ubuntu:~$:confused:



EDIT: I tried Testdisk to see what it could see, and it returned the worrying message

no harddisk found

---

### Post by az on 2008-10-20
I figure you can't see the drive in the bios.  If that is the case, then there is no way any software can see it.  Can you confirm this?

---

### Post by ginestre on 2008-10-20
Can the BIOS see the HD?

Well, XP boots happily; and the BIOS setup correctly reports both make and model (MAXTOR STM 325882) in the HD Boot Sequence Priority options, so I think it does. Is there another way to double-check this, or is that enough to say the BIOS is seeing the disk? 

I also tried GParted live disk, and it doesn't see the HD. Yet XP does!*?!|:confused:

---

