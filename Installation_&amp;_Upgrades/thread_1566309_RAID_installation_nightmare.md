---
title: "RAID installation nightmare"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by LiLoather on 2010-09-02
Trying to do clean install of 10.4 incorporating RAID 1.

Followed instructions in:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

which admittedly relates to 9.01 and so I suppose cannot be reasonably expected to relate to 10.4

All went well until step 5, when I hit the button in writing the changes to disk.  Then the installer when ahead and cheerfully installed the base system to the hdd I'd partitioned.

When that finished and I had the opportunity to <go back> I went back to the partitioner and duly repeated all steps 1 to 5, after which the Installer happily went ahead and installed the base system all over again.

After a cup of tea while that as going on I had another chance to <go back> and followed the steps in the guide to configure the RAID array.  Fine.  Wrote the changes to disk.  

Hit the finished configuring button and was awarded a big red screen - no root file system selected.  

Now, I think the Partitioner auto-selected / when configuring the partitions for a second time.  Nothing was said about having to do it manually the second time and I don't even recall being given the option as it is, again, auto configured by the partitioner.

But now I can't make any changes to any partition because they're part of the RAID array and I can't install because the installer spits the dummy at the configuration.

Is it possible to finish installing to a single disk and then do in Ubuntu what is so easy in Windows, which is just to install another hard drive and tell Disk Manager that you want to mirror an existing partition to it?

---

### Post by LiLoather on 2010-09-19
Two weeks later, no helpful advice from the Ubuntu community and the nightmare goes on, and on and on.

Have just retried to set up Linux Raid for the fourth time and hit exactly the same brick wall - I have finished partitioning and want to write the changes to disk. I have RAID device #0 defined and RAID device #1 defined, I have identical partitions allocated to RAID on sda and sdb which were allocated to / and swap when being set up, (tho' that appears to have been forgotten) but the partitioner refuses to proceed, demanding that I define a root partition while refusing to allow me to make any changes to the defined partitions.

Jesus wept!

---

### Post by ronparent on 2010-09-19
Have you read: [http://ubuntuforums.org/showthread.php?t=1574722&highlight=raid](http://ubuntuforums.org/showthread.php?t=1574722&highlight=raid)

---

### Post by realzippy on 2010-09-19
*I have identical partitions allocated to RAID on sda and sdb which were allocated to / *
...the 2 partitions on sda/sdb should not be allocated to /,they are only used to "build" MD0,which has to be allocated to /...
BTW,for RAID1 you also need 2 boot and 2 swap partitions.
Use the Alternate CD to install.

---

### Post by LiLoather on 2010-09-21
> **ronparent said:**
> Have you read: [http://ubuntuforums.org/showthread.php?t=1574722&highlight=raid](http://ubuntuforums.org/showthread.php?t=1574722&highlight=raid)

I have now, thanks.  

My RAID is now actually up and running.  Silly old me didn't realise that hidden behind the "Use as: Do not use" line in the Partitioner is a whole list of possible uses for the partition.  I expect that's because I'm the kind of boring old fart who sees something that says 'Stop', or 'Do not swallow', or 'Do not use', and assumes it's telling me it's a bad idea to not stop, to swallow something, or use it.

I admiringly concede that you Linux types have a way of turning the simple and straightforward into a nine-step complexity down to a fine art.

Realzippy I followed the instructions slavishly and have two / and two swap partitions happily wed and my boots drying by the back door. And the computer still starts, so I've no idea where its boots are.

---

### Post by realzippy on 2010-09-21
yep,you do not need a seperate boot partition to boot.Wanted to say:
if you have a seperate one,you need 2 (to make a RAID1 device of them also).

---

