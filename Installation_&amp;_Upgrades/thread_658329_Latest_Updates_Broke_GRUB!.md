---
title: "Latest Updates Broke GRUB!"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by Tsu Dho Nimh on 2008-01-04
I an running 7.04 v(Ubuntu, kernel 2.6.20-15-generic ot be precise), and accepted a bunch of updates on Wednesday, Jan 2.

**Problem:** As soon as I restarted to get the kernel updates going, I could not boot because the partition was not found.

**Apparent Cause:** One of the updates rewrote GRUB to boot from partition 0,2 which is not where my boot partition lives. 

I've fixed it by specifying (hd0,0), but is there any way to know which bit of software did this, so I can prevent it from happening again? 

And why would an update trash my GRUB file by telling it to boot to someplace different?

---

### Post by bereanone on 2008-01-04
Maybe they are actually trying to fix the slow start problem.  My computer takes almost 3 minutes to boot up now. Feisty Fawn actually worked better. My SD chips no longer boot up, Automatix doesn't work anymore and I still struggle with tarballs, my external drives don't work, in short every time I turn around, I find little problems and new releases don't fix them. In fact, they break old things that were fixed, while not fulfilling promises of great new things to come. I am actually finally looking at macintosh.  The linux crowd is right, Windows sucks, but Ubuntu is NO BETTER.  Somewhere out there there has got to be a good operating system that is bullet proof and actually works as advertised.
Frustrated.

---

### Post by Tsu Dho Nimh on 2008-02-08
And it did it again with another round of updates ... GRUB rewritten so partitions were not findable.

---

### Post by Pumalite on 2008-02-08
Fix menu.lst and change 'groot' to avoid further changes with kernel upgrades. Backup first.

---

### Post by bikeman01 on 2008-02-09
> **Pumalite said:**
> F...and change 'groot' to avoid further changes with kernel upgrades..

again in noob speak please

---

### Post by Pumalite on 2008-02-09
Post:
cat /boot/grub/menu.lst

---

### Post by Tsu Dho Nimh on 2008-02-28
> **Pumalite said:**
> Post:
cat /boot/grub/menu.lst

And then what do you do to it after that? 

The kernel 2.6.20-16 updates persist in rewriting GRUB so it points to non-existent hard drives. I wouldn't mind the -16 updates so much but they also change the pointers to the -15 vresion (which is all I use because -16 FUBARs some software I like to use)



title		Ubuntu, kernel 2.6.20-16-generic
**root		(hd0,2)**
kernel		/vmlinuz-2.6.20-16-generic root=UUID=10570462-aa97-45d6-88a4-a9948ecdf27d ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=10570462-aa97-45d6-88a4-a9948ecdf27d ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=10570462-aa97-45d6-88a4-a9948ecdf27d ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=10570462-aa97-45d6-88a4-a9948ecdf27d ro single
initrd		/initrd.img-2.6.20-15-generic

---

### Post by confused57 on 2008-02-28
> **bikeman01 said:**
> again in noob speak please
This should explain how groot works:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

To edit your menu.lst, open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

---

