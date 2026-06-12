---
title: "installing grub on a partition"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by g0l3m on 2008-01-29
Hello all,

I have a laptop with vista and ubuntu installed. I'm having some trouble configuring the bootloader and I was wondering if anyone can help.

I'm planning on installing grub on a partition (rather than MBR) and then use EasyBCD as per: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Here's the problem...At the end of the installation I'm getting something along the lines of:
"Unable to execute grub-install (hd0,3). This is a fatal error".

I'm pretty sure this means that I'm trying to write on some other partition (e.g. the recovery partitions of the laptop) rather than the ubuntu one, but I'm not sure how that's possible...

Can someone confirm the following is correct:

+ When selecting a partition for grub, the numbers start from 0, i.e. if your ubuntu installation went on sda3, then you need to install grub on (hd0, 2). Is this correct?

+ I'm installing grub on (hd0,3) and my partitions look as follows (in this order in case it matters):
sda1 ntfs 10Gig (recovery?)
sda2 ntfs 193Gig (vista)
sda4 ext3 42Gig (ubuntu)
sda3 ntfs 3Gig (some other acer recovery thing)

Am I right to install on (hd0,3)? Why is the order displayed as 1,2,4,3 rather than 1,2,3,4?
Obviously I don't want to trial-n-error this...I know grub can't write on the recovery partitions (since I've seen the "fatal error" but I've no idea what will happen if it tries to write on the vista partition).

cheers,
g.

---

### Post by syg00 on 2008-01-29
(hd0,3) looks o.k. - personally I prefer the "native" commands rather than that wrapper, but each to their own.
I would run the command manually and see if there are any messgaes from grub itself - that message looks to be from the installer.
The partitions are out of order as sda3 is probably at the "end" of the disk. Nothing to worry about - Dell do similar for their Mediaplayer.

---

### Post by c0met on 2008-01-29
The guy at the below link is a bit of a grub expert. He may have some advice to help.

[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by gnucklehead on 2008-01-30
I had the same installation issue, with Windows on partition 1, recovery on 2, and Ubuntu on 3. I found that the partitions are zero based, so when installing the bootloader, I used (hd0,2) for partition 3,  and it worked.

Hope this helps!

---

### Post by torgrot on 2008-01-30
Post the output of fdisk -l ( that is a lower case L),  I suspect that partition 3 is actually the extended partition wrapper( for lack of a better name ).  

torgrot

---

