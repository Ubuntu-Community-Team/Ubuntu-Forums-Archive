---
title: "Installing Unbuntu on a Beagle Board via SD-Card"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by Hasorko on 2011-08-29
Hi Community,

as the title sais, I'd like to install Ubuntu on a BeagleBoard (rev C4). It is a classic board no xM version!

This is what I did:

- get an image of ubuntu on my SD-card
- boot the system -> installation starts

This is my problem:

The installation stops and tells me, it has to redo the partitions, but can't do this, because it can't get rid of /cdrom

This is what my research told me what the problem is:

- the installation trys to format, but since my installation is on the same SD-card it must be unmounted, else its like cutting of the brench you are sitting on.

Well allright... but actually I have no idea what this means and what I have to do. I have to devide the installation files from the new partitions. I have to unmount it somehow. 

This is what I'd like to have. A detailed description what actually the partitions are, which have to be unmounted. And how I unmount on a windows machine.

If you see another problem, then go ahead and tell me :S

Thanks 

Hasorko

---

### Post by SiathLinux on 2011-08-29
Not up to date on the Beagle Board - however - it sounds like your installation is trying to install to the wrong place - ie back onto the USB that your 'image' is on... and it should be installing to another location (which would be however the Beagle Board is 'mapped' to your system).

Verify that your installing to the right location.

---

### Post by Hasorko on 2011-08-29
The Image is on the SD-card and the installation has to be done on the same SD-card. I think the location is alright, but it thinks it tries to install to the CD-ROM, but actually this is an SD-card. Can something like this be the case?

Here are all my steps I took in the partition step in the installation:

1. Click on Free Space
2. Click add
3. click "primary" select "2600"  select "swap" didn't do anything in the Mount line
4. after the SWAP is created I again selected the remaining free space and clicked add again
5. click "primary" select all the remaining space "4798" select Ext4 and in the mount line I wrote "/". 

So I got a root and a swap partition. On top there is another partition with the image file in it. (not sure if it is supposed to be there) I also already tried to delete these files and do the installation but same failure.

The Harddrive is called /dev/mmcblk0

in the end it looks like this

Harddrive------------Usage Mountpoint Format? Size---used
/dev/mmcblk0       
--/dev/mmcblk0p1---fat32------------------------550MB--529MB
--/dev/mmcblk0p2---swap------------------------2599MB unknown
--/dev/mmcblk0p3---ext4---/-------------y-------4797MB unknown

there is now no more free space

Is this what u needed?

---

### Post by Hasorko on 2011-08-29
double post nvm that one

---

### Post by Hasorko on 2011-08-29
Why does the Forum posts my posts over and over agina on refresh O.o

---

### Post by mörgæs on 2011-08-29
Because the browser is resending the information.

---

