---
title: "Trying to install UNR with no CD, floppy boot only"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by jrobinson5 on 2010-03-17
Hello,
I'm trying to install Ubuntu Netbook Remix 9.10 on a Compaq Evo N200. The problem is that it doesn't have a CD drive on board, and it only supports booting from USB floppy drives- not USB flash or CD drives. I have access to a flash drive, floppy drive and CD drive, all USB externals. I've tried a couple different floppy boot loaders with little success. I understand that it also supports network boot, so this might be an option. What is the easiest way to get UNR running on this laptop?
James

---

### Post by benmoran on 2010-03-17
I don't have any links handy, but i'm pretty sure it's possible to use a floppy boot disk to enable booting from your USB stick.

Maybe someone else can chime in with a link.

---

### Post by jrobinson5 on 2010-03-17
That would be great.

---

### Post by jrobinson5 on 2010-03-18
I got it working! But not in the way that you might think...
I had another laptop sitting around (a Compaq Evo n610c) that had very little in common with the target laptop. However it did have a CD drive and it used the same hard drive interface (2.5 inch PATA) as the n200. So I inserted the hard drive from the n200 into the n610c and installed Xubuntu on it. Then I swapped it back into the n200. The first time I tried to boot it I got a file system error, so I ran fsck and then pressed Ctrl-D to make it boot. Surprisingly everything ended up working out perfectly- I didn't even have to reconfigure Xorg. I ended up choosing Xubuntu over UNR due to the target laptop's low specs (700mhz, 128mb ram- soon to be upgraded to the maximum of 192mb).
Cheers!
James

---

### Post by tom4jean on 2010-03-18
I just want to say in admiration that was genius!:D

---

