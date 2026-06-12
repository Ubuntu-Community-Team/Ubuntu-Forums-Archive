---
title: "Partition issues"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by Niteowler on 2008-02-02
Anyone know where I can find a out how to partition my newly formatted hard drive  for a Ubuntu install?  I'm using a windows 98 startup disk.  Tried putting everything on the C: drive as a primary dos partition.  No matter what version of Ubuntu I try, the live cd doesn't want to mount the hard drive.  Do I need to make a logical or swap partition?   I'm using fat 32.  Don't have a clue how to even make a swap partition if needed.  Thanks for helping a newb if there's any responses.

---

### Post by Niteowler on 2008-02-02
Anyone know where I can find a out how to partition my newly formatted hard drive  for a Ubuntu install?  I'm using a windows 98 startup disk.  Tried putting everything on the C: drive as a primary dos partition.  No matter what version of Ubuntu I try, the live cd doesn't want to mount the hard drive.  Do I need to make a logical or swap partition?   I'm using fat 32.  Don't have a clue how to even make a swap partition if needed.  Thanks for helping a newb if there's any responses.

---

### Post by jan quark on 2008-02-02
download the gparted live cd / 50MB or so/

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

burn a cd and boot with it if

it is a good application for formating and to create partitions

ask for more info

---

### Post by cilynx on 2008-02-02
None of the recent versions of Ubuntu require that you partition your drive at all before you start the install.  A utility called GParted is included as a part of the install system and it allows you to graphically partition the drive as necessary.  What version of Ubuntu are you working with?

Given that, let's see if we can work out what the actual problem is...

Here's how I understand the situation, please make corrections as necessary:

1. You're looking to dual boot your machine so that you can run either Win98 or Ubuntu.
2. You already have Win98 installed and running.
3. Your Win98 partiton is formatted as fat32.

You can successfully boot into the Ubuntu Live system, yes?

Once running Ubuntu Live, if you click on the *Install* icon, it should take you to the partitoner to setup your hard drive as you want it.

Let us know how far you get into that and we'll go from there.

---

### Post by jan quark on 2008-02-02
when you install ubuntu with the live CD or the alternate CD ubuntu takes care of everything if you dont want to

check this sites for a description of the installation process
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by Niteowler on 2008-02-02
Thanks for the info Jan!  I'm sure that gparted is a fine program and I'm going to try it but what I'm really unsure about is exactly how I need to partition the drive to make everything work.  I can partition with the windows 98 startup disk but I'm unsure what kind of partitions I need.

---

### Post by Niteowler on 2008-02-02
I can't even get the live cd to load.  I always get a "timeout waiting for dma" or "hdc:drive not ready for command" errors.

---

### Post by jan quark on 2008-02-02
using a kernel boot parameter of ide=nodma should help

When you are here
[http://img255.imageshack.us/my.php?image=feistysingle01fb0.png](http://img255.imageshack.us/my.php?image=feistysingle01fb0.png)


 hit f6 to get to the boot menu, select your kernel, type 'e' to edit the line, then 'e' to edit the boot line. This line has some other options like 'ro quiet splash' (possibly) on it.

 Add ide=nodma, then type 'b' to boot.

---

### Post by jan quark on 2008-02-02
check this excellent guide
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Niteowler on 2008-02-02
I'm not going to run a dual boot system.  This system is going to run Ubuntu and Ubuntu only.  There's no other operating systems involved in any way.  I used a windows 98 startup disk (floppy) to format and partition the hard drive because I'm familiar with it and works well.  When i try the Ubuntu 6.04 live cd I get a "timeout waiting for dma" and "hdc:drive not ready for command" error.  Ubuntu 7.10 live cd freezes when the orange bar is going across while loading.
     I formatted the hard drive and made the whole drive into one primary dos partition.  Was having this problem with another hard drive before but I thought the problem was because it had no cache but the new drive has 2 mb and still has the same problem.  Can't get the live cd to load.

amd xp 2900+
abit kv7 motherboard
1 gig ddr ram
40 gig maxtor hard drive (ide)
nvidia 6600gt video card

---

### Post by cilynx on 2008-02-02
Alrighty, I follow:

I'm sticking by that you don't need to partition or format the drive beforehand.  Once you get past the hardware issue that we're looking at, you'll be golden.

It sounds like there may be something wonky with the DMA controller on your mobo if you have the same problem across a couple of drives.  I would try setting your DMA to as low (failsafe) of a mode as your BIOS supports (disable it if you can), then try booting the Live CD again.

---

