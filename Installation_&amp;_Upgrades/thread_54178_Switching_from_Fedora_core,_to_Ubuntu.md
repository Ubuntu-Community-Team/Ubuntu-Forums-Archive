---
title: "Switching from Fedora core, to Ubuntu"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2005-08-03
Okay, please provide **VERY** detailed instructions for the following. I am new at this, and I want to be guided, not thrown in to the forest alone.

This is currently how my hard drive is set-up:

[http://img290.echo.cx/img290/8150/screenshothardwarebrowser7bj.png](http://img290.echo.cx/img290/8150/screenshothardwarebrowser7bj.png)

Now, what I want to do is replace my ext3 partiton and a swap partition with an ubunut installation ( that hopefully include a swap partition ),

Will I easily be able to do this in the installer? I don't want to accidently over write anything. 

Will GRUB recognize ( sp ) my windows partition on start-up?

I know I am being paranoid, but I already had to have an IT Administrator fix my Windows partition, I don't want to bother him again. 

Help greatly appreciated! :)

---

### Post by amohanty on 2005-08-03
> Will I easily be able to do this in the installer? I don't want to accidently over write anything. 

Yes. 

> Will GRUB recognize ( sp ) my windows partition on start-up? 

Yes.

AM

---

### Post by Jessehk on 2005-08-03
okay, off to back-up, then to installing.

thanks :)

---

### Post by Jessehk on 2005-08-03
Sorry, quick question. Can the installer format partitions, or do I have to use Partition magic?

---

### Post by amohanty on 2005-08-03
It will format partitions. If you specify a new mount point or fstype for a partition it will autoatically mark it for a format. In the installer in the verify partition table look for a column with characters that kinda look like '#'. Those are the ones that will be formatted. So you only want to mess with the partitions where you want to install stuff and leave the rest alone.

AM

---

### Post by Jessehk on 2005-08-03
Thanks again. I will post an update on how things went.

---

