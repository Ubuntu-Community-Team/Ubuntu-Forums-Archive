---
title: "Cloning Ubuntu to test out an upgrade"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by martin.bartlett on 2010-10-23
I just went through a learning process that might benefit others. I cloned my Ubuntu 10.04 system into a VirtualBox VM and then tested the upgrade to 10.10 in that VM. It was a bit of a learning curve but with experience now the steps are actually quite easy!

As you might expect, the cloning was the toughest - but, again, only because I'd never done it before. I'll outline the steps here and then if anyone wants more detail just ask and I'll reply.

[LIST]
[*]So firstly you have to install VirtualBox - which you'll find in the 10.04 repositories - so that's handy.
[*]Then take a note of the partitions your system is on (df, then anything that is mounted on / or a subdirectory).
[*]Eliminate from that list anything that's not really gonna affect how the system runs - media partitions for example. Of course, if you only have one partition then skip this step.
[*]Now find yourself some space - about DOUBLE that of the total partition size you'll be cloning.
[*]Boot up a live cd.
[*]Mount the free space.
[*]then take copies of each partition: "dd if=/dev/sda1 of=/freespace/sda1.raw" - something like that
[*]Reboot back into your normal ubuntu, mount the freespace partition (if not already there) and bring up a terminal and go to the freespace directory.
[*]Using VirtualBox's VBoxManage command, convert each raw file into a vdi file: VBoxManage convertfromraw sda1.raw sda1.vdi
[*]Start VirtualBox
[*]Using the storage manager create a NEW vdi (in the freespace directory) of a bit more than your total partition size (don't worry, it won't actually take up that much space).
[*]Again, in the storage manager of VirtualBox, import your converted VDIs.
[*]Now, create a new virtual machine (using the standard VB wizard)
[*]Add ALL your VDIs (the converts and the new one) to the machine (in the settings dialog once the machine is defined)
[*]attach a copy of the live CD ISO file to the machine's CD device.
[*]boot the machine
[/LIST]

So now you have a VM running and all your DD'd data attached. You then have to mount the converted VDI files to recreate your physical machine's directory structure - put the root partition under /mnt and the the boot under /mnt/boot etc.

Then go into the GParted tool (System > Administration) and find your EMPTY NEW VDI - in THAT:

[LIST=1]
[*]Create a Partition Table
[*]Create a small partition as Swap
[*]Allocate the rest of the "drive" as an ext 3 partition, then mount that somwhere NOT in the mnt tree. You can create a directory in the root of the live system for that purpose - say, /stage
[/LIST]

Now copy all your data from the /mnt tree to the directory you mounted the free partition on: "cp -a /mnt/* /stage".

That'll probably take a WHILE!

When it's done, unmount the convert VDIs (the mnt tree) but NOT the stage tree.

NOW... edit /stage/etc/fstab and ensure you have only one swap entry, pointing to /dev/sda1 (the swap patition on your new vdi) and one root partition pointing to /dev/sda2 (what's currently mounted on /stage). Note, even if the new vdi is NOT /dev/sda, make these entries point to /dev/sda - because the NEXT time you boot it WILL be /dev/sda.

Now to setup GRUB (the boot loader). This doc explains all ... [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2") ... BUT the essential command to enter NOW is:

sudo grub-install --root-directory=/stage/ /dev/sdX

where sdX is the current device for your new vdi.

You've now created an ALMOST bootable clone of your live system.

unmount /stage and shutdown the VM.

NEXT, go into the VMs settings and remove all the clone vdis but NOT the one you created from scratch (which now contains your system clone). Detach also the live cd ISO.

Reboot the VM and...

Well, GRUB won't find your root device yet. Follow the on screen instructions (or those in the above link) to get to the GRUB command line. Once there enter these commands:

set root=(hd0,msdos2)
linux /vmlinuz root=/dev/sda2 ro
initrd /initrd.img
boot

THEN it should boot just fine (if a little slowly and verbosely).

Once in your familiar desktop the first thing you should do is bring up a terminal and enter:

sudo update-grub

to sort out the GRUB menu, and then shutdown again.

THEN copy that fresh vdi that contains your wonderful system clone so you can always take your VM back to its initial clean cloned state.

Reboot the VM and test out the 10.10 upgrade - which has just finished perfectly on my clone!

Feel free to add to, prune and/or correct these instructions and note - no real data was harmed in the making of this system clone!

---

### Post by psusi on 2010-10-23
You should use cp to copy the files, rather than dd to clone the entire partition, since dd will waste time and space copying the unused space as well.

I've been experimenting the last few days with using LVM snapshots to test upgrade, then revert.  Quite handy.

---

### Post by martin.bartlett on 2010-10-24
Well, yes and no. DD is the only way to get a file that VirtualBox can CONVERT to a VDI, but you COULD try SHARING each partition with the Virtual machine - that, however, has its own issues because sharing live partitions with the VM and doing cp's of the data directly into the VM COULD end up with various permission problems and inconsistent data. In the end, the dd-clone-copy cycle ends up with a VDI that is about the same size as all the original data WITHOUT the empty space (and you can delete the RAW and VDI files once you have cloned and copied them).

You can also change the dd-clone-copy cycle to a simple dd-clone if you really want to create a FULL clone of your entire disk - but, again, this can end up wasting space. On my machine I have about 8 partitions, only four of which were really required for a full test and these only took about a max of 60Gig on a half-terrabyte disk - a "dd if=/dev/sda of=full_disk.raw" command would indeed have taken up a whole lot of space completely unnecessary for the purposes of the clone.

I have no experience with LVM - I'll have to fire up a VM and see what its all about (I LOVE VirtualBox - shame Oracle owns it now!).

Other Physical-to-Virtual (P2V) guides on the web use things like CloneZilla to do the partition copy (and then a CloneZilla recover step to build the VDI) - that seemed a valid way to go, except it meant learning CloneZilla which I didn't want to do (yet). There are also guides that use VMWare's Stand-Alone P2V capabilities - pushing that tool's live-system-clone capability - well, it would be nice it that worked, but it doesn't unless you have a FULL VMWare infrastructure installation, which costs!

---

### Post by psusi on 2010-10-24
You don't have to dd the entire original volume to end up with an image file for the vm.  You can just create a small image file, loop mount it, copy the files into it, then unmount and pass it to the vm.

---

### Post by perspectoff on 2010-10-24
> **psusi said:**
> You should use cp to copy the files, rather than dd to clone the entire partition, since dd will waste time and space copying the unused space as well.

I've been experimenting the last few days with using LVM snapshots to test upgrade, then revert.  Quite handy.

Yeah, I do this, too.

Does dd require the filesystem type to be the same? That is, if your filesystem is ext3 and you want to move to an ext4 filesystem, can you use dd?

I know you can with cp -a, but I haven't tried it with dd...

Also, I think the use of dd is the reason he needed double the partition size. (There is an option in dd, though, to copy only used portions of the partition, I think, although I can't find it at [http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29) ).

That is a very good how-to, overall.

The trickiest part for me was to also figure out these steps (I use ones slightly different, but close):

> Well, GRUB won't find your root device yet. Follow the on screen instructions (or those in the above link) to get to the GRUB command line. Once there enter these commands:

set root=(hd0,msdos2)
linux /vmlinuz root=/dev/sda2 ro
initrd /initrd.img
boot

THEN it should boot just fine (if a little slowly and verbosely).

Once in your familiar desktop the first thing you should do is bring up a terminal and enter:

sudo update-grub

to sort out the GRUB menu, and then shutdown again.

---

### Post by psusi on 2010-10-24
> **perspectoff said:**
> 
Does dd require the filesystem type to be the same? That is, if your filesystem is ext3 and you want to move to an ext4 filesystem, can you use dd?

dd does not know or care about filesystems; it just does a sector by sector copy.

> **perspectoff said:**
> 
Also, I think the use of dd is the reason he needed double the partition size. (There is an option in dd, though, to copy only used portions of the partition, I think, although I can't find it at [http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29) ).

Of course, since dd copies every sector, you need the same amount of space for the image as the original partition, even though 80% of it is free space.

---

### Post by perspectoff on 2010-10-24
> **psusi said:**
> 
Of course, since dd copies every sector, you need the same amount of space for the image as the original partition, even though 80% of it is free space.

Then why does he need double the disk space to copy a partition?

---

### Post by psusi on 2010-10-24
> **perspectoff said:**
> Then why does he need double the disk space to copy a partition?

Original + copy = 2x the space.

---

### Post by martin.bartlett on 2010-10-25
The way I did it was dd a copy of each partition, then a virtualbox conversion of those copies - immediately after which you have two copies of your partitions.

There are various different ways of doing the copy, I admit - the goal of course is to end up with your live system reproduced in one of more VirtualBox VDIs that can then be booted, so any technique that gets you there is good. I was "lucky" in that I have a spare almost un-used ide drive that I use for staging backups and the like. It had enough room for the partitions I wanted in the VM (amounting to 60G including unused space), plus the target consolidated VDI (which, in the end, was only 20G) - and it really didn't take that long to dd-convert - especially considering I had to sneak in occasionally from cutting down trees and trimming bushes to do this anyway - wife wanted a "computer-tweak-free day"! As if!

---

