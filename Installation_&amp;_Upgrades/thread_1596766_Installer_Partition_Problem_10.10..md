---
title: "Installer Partition Problem 10.10."
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by fifth on 2010-10-14
I've not jumped on the Alpha/Beta upgrade's this time round so have decided to upgrade by doing a fresh install. I'm using the normal desktop install cd via usb.

On the drive setup I choose to manually setup the partitions. I deleted the partition which help Lucid. Created a new partition with the root path. All good so far. I selected my home partition and selected use as 'ext2', entered /home as the mount point. Clicking ok to return, showed the /home partition as marked to be formatted, I was unable to change this ... so I decided to quit the installer and reboot ...

1st problem ... the root partition for Lucid was deleted, and a new empty partition created, despite the fact I had not confirmed the actions.

2nd problem ... rebooting with the live cd (which I'm on now) and running the installer, it hangs when I select manual partitioning.

Any and all suggestions welcome ... I'm guessing I should download the alternative cd ...

---

### Post by andrewthomas on 2010-10-14
> **fifth said:**
> I've not jumped on the Alpha/Beta upgrade's this time round so have decided to upgrade by doing a fresh install. I'm using the normal desktop install cd via usb.

On the drive setup I choose to manually setup the partitions. I deleted the partition which help Lucid. Created a new partition with the root path. All good so far. I selected my home partition and selected use as 'ext2', entered /home as the mount point. Clicking ok to return, showed the /home partition as marked to be formatted, I was unable to change this ... so I decided to quit the installer and reboot ...

1st problem ... the root partition for Lucid was deleted, and a new empty partition created, despite the fact I had not confirmed the actions.

2nd problem ... rebooting with the live cd (which I'm on now) and running the installer, it hangs when I select manual partitioning.

Any and all suggestions welcome ...** I'm guessing I should download the alternative cd** ...
I don't see why the installer would work once, then hang the next.  

Have you tried a third time? 

As to the /home partition, was it already an ext2 partition? 

 Why would you want it to be?

---

### Post by perspectoff on 2010-10-14
> **andrewthomas said:**
> I don't see why the installer would work once, then hang the next.  

Have you tried a third time? 

As to the /home partition, was it already an ext2 partition? 

 Why would you want it to be?

Yeah, don't use ext2. Use ext4 or ext3.

---

### Post by 23dornot23d on 2010-10-14
Question is ..... how did you exit the installer .... if you just crash out of it or hit the power down ..... it would probably mess up the partition table slightly .....

I had something similar happen once .... then the partitioner would just hang .....

Solved mine in the end using Testdisk .... but it took a while sorting it out .....

[B]Your data may still be there and ok if you did not format ..... and Testdisk can get it back.
[/B] 
______________________________________________________________________

As regards the install ..... if you can still see the partitions ok .....

  If I was doing a clean install then that would have gone on a completely separate partition to be safer ..... 
that's what I do anyway ........ always leaving a version to jump back to .....

---

### Post by fifth on 2010-10-14
> **perspectoff said:**
> Yeah, don't use ext2. Use ext4 or ext3.

Yeah my bad, that's why it wanted to format lol ... the home partition is ext3. But anyway that's not the problem, just how it started lol.

I left the installer by quitting back to the livecd desktop. I've checked and the root partition is there, but empty - as it should have been if I had continued with the install. But the installer still hangs when I select 'Specify Partitions Manually' then forward ... the screen and buttons appear, the busy pointer is there and the partition info never appears.

I guess the partition table is somehow messed up. I used parted to remove the root partition(s) since that seems to be the source of the problem, but the installer still hangs.

---

### Post by 23dornot23d on 2010-10-14
It can hang when trying to unmount partitions that are not correctly set up .... that's what I found out with mine. 

If you run Testdisk 6.11 ..... and analyze the disk its a good place to start ....

you do not have to commit to anything ..... just do a recon first and have a look what 

Testdisk makes of the partitions ..... you will soon see if there are any obvious problems.

post a screenshot .... if it seems confusing ...... 

You can create a backup in it too quite easily .......

Analyze ...... (PC type partitions) usually ..... depends what yours is ...

q is for quit ..... in it too ..... think you press this twice to get out clean .....

Nothing changes unless you write it to disk .......

It will possibly let you put it back to the original and then work ok .... but you have to be sure its all ok ....

It can be a dangerous tool** if you are not sure - then just do a analyze** ............

Here is the Wiki .... best read this first .... [**TESTDISK**]("http://en.wikipedia.org/wiki/TestDisk")

---

### Post by fifth on 2010-10-14
> **23dornot23d said:**
> It can hang when trying to unmount partitions that are not correctly set up .... that's what I found out with mine. 

If you run Testdisk 6.11 ..... and analyze the disk its a good place to start ....

Thanks for the tip on testdisk, unfortunately I was not able to download that via the live cd. I decided to grab the alternative cd ... initially trying to create a usb startup drive on a second flash drive ... but that kept hanging too when creating the bootloader.

Then decided to go the traditional route and burn a cd with the alternative version ... after that everything went very smoothly ... I was able to setup the partitions the way I wanted and install.

So I am backup and running with 10.10 :)

---

### Post by 23dornot23d on 2010-10-15
Good to hear ..... was maybe the flash drive causing the hanging then .... good to hear of another successful outcome ..... :)

---

