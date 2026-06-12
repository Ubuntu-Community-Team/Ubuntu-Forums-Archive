---
title: "[SOLVED] Multiple Swap partitions"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Kevbert on 2008-05-06
I have installed Fedora X64, Kubuntu Hardy X64 and Ubuntu Gutsy X64 on a single hard disk.  With each install a separate Swap partition was made (approximately 3Gb in each case).  I currently have 1Gb of RAM and want to install 3Gb more (4Gb total).  Will the Swap partitions be used together (9Gb) or used (only separately) for each OS (3Gb) ?  Or will I need to re-setup (re-install) each OS when I upgrade ?

---

### Post by petteriIII on 2008-05-07
Ubuntu uses that swap what is referenced in /etc/fstab. One may use several swap-partitions at the same time and it even is benefical in theory. But it is wisest to use just one. All your Ubuntus can use the same swap if only one instance of Ubuntus is running at any time - with virtual software you can run several OS:s at the same time, and then they all must have own swap.

You can reference any swap-partition by changing swap's UUID in /etc/fstab. You get a list of UUID:s with the command: blkid.  
In theory your swap must be at least same size as RAM, but 3GB is pretty much ok. for 4GB RAM.

---

### Post by zvacet on 2008-05-07
All these OS should use just one swap,bacause they wil run one at the time.I think they all will recognize swap partition,so one is enough.

---

### Post by Kevbert on 2008-05-07
> **petteriIII said:**
> Ubuntu uses that swap what is referenced in /etc/fstab. One may use several swap-partitions at the same time and it even is benefical in theory. But it is wisest to use just one. All your Ubuntus can use the same swap if only one instance of Ubuntus is running at any time - with virtual software you can run several OS:s at the same time, and then they all must have own swap.

You can reference any swap-partition by changing swap's UUID in /etc/fstab. You get a list of UUID:s with the command: blkid.  
In theory your swap must be at least same size as RAM, but 3GB is pretty much ok. for 4GB RAM.

Thanks peteriIII. I thought that it was necessary to have a swap partition of at least two and a half times the RAM in case of a system crash or the system going into standby/hibernation. I think I'll leave the swaps alone.

---

### Post by Pumalite on 2008-05-07
In laptops /swap=RAM for hibernation.

---

### Post by az on 2008-05-07
I thought you need 25 per cent more swap than ram to hibernate.

As well, if you hibernate, the saved state of your ram will be wiped out by booting onto another OS if that other OS uses that swap space.

That being said, you are never forced to hibernate.  I don't think the system will hibernate due to crash.  If you never use hibernation, you can share one swap.

As for the ideal size of swap, it depends on your needs.  If disk space is not an issue, then have a swap that is twice the size of your ram or greater.  If disk space is an issue, use a smaller swap.

---

### Post by Kevbert on 2008-05-07
> **Pumalite said:**
> In laptops /swap=RAM for hibernation.

Thanks for clarifying.  Why then do you need a swap partition for a desktop if the PC never is going to hibernate ?  I run boinc in the background and as far as I know the PC runs continuously.

---

### Post by az on 2008-05-07
> **Kevbert said:**
> Thanks for clarifying.  Why then do you need a swap partition for a desktop if the PC never is going to hibernate ?  I run boinc in the background and as far as I know the PC runs continuously.

You can hibernate a desktop.  It can cut down on boot time.  There are also some other reasons for doing it, such as changing hardware without having to shut down the OS.

---

### Post by flaggh on 2008-05-07
From what I understand, swap is effectively a place the system will store information if it runs out of RAM.  This is the same thing Windoze refers to as Virtual Memory.  I don't think you really _NEED_ swap space if you never sleep or hibernate your computer, but it should still improve the performance of your computer by increasing the available amount of memory.  However, since it takes a lot longer to swap information from your hard drive than it does from RAM, it definitely will not be as effective as adding more RAM.

As was metioned before, your OS will only use the swap partition that is specified in your fstab.  The most efficient use of hard drive space would probably be to make a single swap partition and then share it amongst the OSes.  If you are worried about losing data when you hibernate and such, you can make three separate swap partitions.  The easiest thing to do IMHO however is to not create swap partitions at all.  You don't really need a separate partition for swap.  A swap file on your root partition (or any active partition) works just as good.  See the swap faq for more info:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Kevbert on 2008-05-07
Thanks for the link flaggh.:)

---

