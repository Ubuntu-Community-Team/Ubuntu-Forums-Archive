---
title: "Choosing GRUB installation location"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by Xyem on 2007-01-10
Just a ( hopefully ) quick question regarding Ubuntu installing GRUB.

I intend to do a bit of magic getting Ubuntu to install on my laptop ( harsh restrictions, ie. no bootable media except HDD ) and I would like the following partition layout on my 6GB drive.

1st partition ( ~100MB ): GRUB ( would usually be the contents of /boot )
2nd partition ( ~2GB ): Windows 2000
3rd partition ( ~2GB ): Ubuntu
4th partition ( ~1GB ): Installation files ( for Windows/Ubuntu ), later shared files
5th partition ( remainder.. ~500MB ): swap

( Any additional advice regarding this partitioning is, of course, welcomed )

My question is this..

During the Ubuntu installation, can I choose that the files for GRUB be installed to the first partition as opposed to in the Ubuntu partition? Will I need the alternate install CD or will the "standard" CD be able to cope with this?

---

### Post by scrooge_74 on 2007-01-10
AS far as I know windows has to be in the first partition or it will not boot, you can put Linux in any other partition even an external drive

The share file partition should be fat32, the Ubuntu partition may need to be a little bigger unless you plan to put the /home folder in another partition

Your swap file should be twice the size of your RAM

/boot partition can be in the same place as Ubuntu, Grub gets installed in the first partition so Windows and Linux can see it dont worry to much about it

---

### Post by K.Mandla on 2007-01-10
I believe (but I don't know for sure) that you should be able to do that. If you start from a blank drive, use the Windows partitioner to set up two partitions -- the first ones on your list. Install Windows to the second, but don't touch the first.

Then when you install Ubuntu, manually point Ubuntu at the partitions you have left to build, making sure you mount the /boot partition to that first space you made with Windows. 

Again, I've never done that, but I think in theory it should work.

---

### Post by Xyem on 2007-01-11
I have 256MB of RAM in my laptop so ~500MB is about 2x my RAM.

Unfortunately, I can only have one harddrive in my laptop and the only one I have is 6GB ( well.. closer to 5.75GB ) so I am quite limited on space.

K.Mandla, will I require the alternate install CD for this. I am asking because I don't recall the "standard" CD asking particulars about where GRUB is installed etc..

---

### Post by scrooge_74 on 2007-01-11
I think you should go for an alternate CD and install the lightest  possible system so you have room for other stuff

---

### Post by Xyem on 2007-01-13
Well, unfortunately, my laptop is now out of action. :(  The power cable has become frayed and the break is too close to the plastic part that is actually inserted into the laptop for me to repair. It may not be worth buying a new power supply, so I believe I will be looking into a new laptop ( with a CD drive ;) ).

Just to let you all know, the problem I got to before this was I could not start the Ubuntu install from the CD files using loadlin. It would always kernel panic after trying to mount the filesystem ( RAM ). I did quite a bit of research into what parameters to use with loadlin and none brung up installation.

Thanks for your time and efforts :)

---

