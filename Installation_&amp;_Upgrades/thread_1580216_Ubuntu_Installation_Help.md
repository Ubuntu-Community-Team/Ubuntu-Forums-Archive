---
title: "Ubuntu Installation Help"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by twunger34 on 2010-09-23
First of all, I'm wanting to install Ubuntu 10.10 beta over my existing Linux Mint partition without disturbing my Windows partition and wondering how that's done. I was also wondering if there was any way during the installation process I could possibly import my 70 gig home folder right over to Ubuntu...Or how I could back it up with these assets:

320 gb HD in laptop with a 40 gig Windows Partition
A wireless network
a 150 gb desktop
No flash drive or removeable media large enough for a sane man to attempt to chunk it up and carry it over one at a time until it's gone.

Could someone please Macguyver me a solution?

---

### Post by SaintDanBert on 2010-09-23
Duct Tape is like "the force." -- there is a light side; there is a dark side; and it holds everything together. (grin)  What you ask is straight forward, but like stepping stones in the stream, one false step and ... SPLASH!

By all means [highlight]make a backup[/highlight] of any files that you care about.

During the installer run, select **manual** partition setup. Select your existing Mint partition and check the []format disk option.

If you already have /home on an existing partition, simply tell the installer to use that partition for /home mount point but DO NOT check the format option.

By all means [highlight]make a backup[/highlight] of any files that you care about. The format will put them out of reach.

You might tell us how your drive(s) are currently partitioned.
```

#=== replace 'X' with the letter 'sda' 'sdb' as required.
#..... do you add a trailing number [1-9] to the name.

sudo fdisk -l /dev/sdX

```

Use a live CD or Mint to run this command.

Bonne chance,
~~~ 0;-Dan

---

### Post by sikander3786 on 2010-09-23
In my opinion, the best way around will be to free up some space (at least 70 GB as your home folder size) in Mint. You can use gparted for that. Format it to ext3 or ext4, mount it and carry on the following command.

```

cp -r  /home/you /media/sda1

```

Replce sda1 with the newly created partition. Home folder will be copied to a new partition. After that, comes the installation of Ubuntu.

Delete the partition/partitions containing Mint. And a basic drive setup for Ubuntu will look like this.

Size > File System > Mount Point
512MB > ext3 > /boot
30-50 GB (You can use whatever size you want) > ext3/ext4 > /
Newly created home drive > ext3/ext4 > /home
RAM X 2 > Swap > Swap

I think you already know about dual booting. Post back for further queries.

**[COLOR="Red"]Edit:[/COLOR]** During installation, make sure that /home is not selected for a format otherwise you will lose all your data.

---

