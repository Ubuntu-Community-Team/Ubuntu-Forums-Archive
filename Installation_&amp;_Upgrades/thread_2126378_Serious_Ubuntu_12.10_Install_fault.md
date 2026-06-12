---
title: "Serious Ubuntu 12.10 Install fault"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2013-03-16
Have one hard drive that had 2 partitions.

1) small partition with ubuntu installed

2)  larger partition with lots of data in it.

Reinstalled Ubuntu 12.10.  The installer asked me if I wanted to install over the existing install.  You know, that small partition with ubuntu on it?  I said OK.

It wiped out both partitions destroying all my data.

This is a serious bug, very serious.  Why on earth wouldn't Canonical's installer see the other partition as a seperate untouchable bit of space and why didn't it ask after warning me whether I wanted to wipe out all that data?  Probably because it didn't bother to check and it just wiped it out.

This is some serious loss.

This is the third major issue I've had to deal with on Ubuntu in the past week.

1) Kernel 3.8 not supporting remote samba shares (boot with kernel 3.5 and it works, boot with kernel 3.8 and it doesn't).

2)  One data file was damaged and that caused hundreds of Linux apps to crash with segmentation fault.

3)  This error where the installer arbitrarily wiped out my data on a separate partition.

---

### Post by iponeverything on 2013-03-17
Unintentional wiping of drives during install is way common of theme lately.. this is the third or forth case I have heard of in as many months.

---

### Post by Moose on 2013-03-17
Like iPon said, this error has happened to a few people lately, but this isn't extremely common. Neither are the other two issues you mentioned. You are just extremely unlucky. As you probably noticed Linux is pretty volatile and requires lots of care. You should just take care as to what you install, especially via terminal. As it's very easy to accidentally remove dependencies and programs by typing in the wrong command. As for the upgrade wiping out the partitions issue, no offence, but you should have known it would happen. You obviously weren't paying careful attention. It isn't a common issue because you would think someone would read it more carefully and pay attention.

---

### Post by nibal on 2013-03-18
> Have one hard drive that had 2 partitions.

> 1) small partition with ubuntu installed

> 2)  larger partition with lots of data in it.

> Reinstalled Ubuntu 12.10.  The installer asked me if I wanted to install  over the existing install.  You know, that small partition with ubuntu  on it?  I said OK.

> It wiped out both partitions destroying all my data.

> This is a serious bug, very serious.  Why on earth wouldn't Canonical's  installer see the other partition as a seperate untouchable bit of space  and why didn't it ask after warning me whether I wanted to wipe out all  that data?  Probably because it didn't bother > to check and it just  wiped it out.

> This is some serious loss.

Sorry to hear about that! The only thing I can think off is to always setup (edit) your partitions manually.
During my installation (did it twice) I edited "Do not use" for every Windows partition, and formatted the
Linux ones. How did you setup your partitions?

BR,
Nikos

---

