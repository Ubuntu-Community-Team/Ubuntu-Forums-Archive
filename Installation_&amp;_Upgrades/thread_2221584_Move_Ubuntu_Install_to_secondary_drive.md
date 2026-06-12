---
title: "Move Ubuntu Install to secondary drive"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by migratorysean on 2014-05-02
Here is the situation -

I currently run a dual boot (Win7/Ubuntu) install off of a single 1Tb drive.  I just got my hands on a second 250Gb drive.  This is what I want to do -

Migrate the existing Ubuntu install (which is a flat all in one partition) and swap to the secondary drive.
Remove the Ubuntu and swap partitions from the main drive.
Expand the Win7 install to take up the whole 1Tb drive.
Be able to use existing Grub install to boot to either partition.

Now, I often discover what looks simple often isn't, and I really can't afford to lose my main machine to a borked install.

Does anyone have suggestions for a safe way to do this?

Screen shot of the partitions here - [http://puu.sh/8wHti.png](http://puu.sh/8wHti.png)

---

### Post by pfeiffep on 2014-05-02
Possibly use [Clonezilla  ]("http://clonezilla.org/")

---

### Post by Petro Dawg on 2014-05-02
I would hook up the 2nd drive, install Ubuntu on it.  Probably safest to select "do something else" on the installation screen and manually setup the partitions on the new drive.  Just format most of the  drive to EXT4 and mount it as root "/" and create swap partition at least the same size as your RAM.  Also make sure you select the new drive as the location to the boot loader to be installed.   The installation program will install GRUB and see the windows, and both Ubuntu installations. 

From your new installation copy everything over from your old ubuntu installation that you wish to save.    Then install Gparted and delete the old Ubuntu installation, and expand your windows partition.  When done run...
 ```
sudo update-grub
```

You will also need to adjust your boot priority in your BIOS at some point to make your new drive boot first, since it will have the new GRUB boot loader.

If you are extra paranoid, like me, I have also been known to remove an old drive that I absolutely do not want to "bork" and install Ubuntu on the new drive.  When finished, hook up the old drive and run the update-grub command to find all the installations.  Then continue copying files and deleting/expanding partitions.

---

### Post by migratorysean on 2014-05-03
I wouldn't be so picky, but I have spent a lot of time getting my Ubuntu install just the way I like it, with bash aliases and cron jobs and themes and all.

---

### Post by ubfan1 on 2014-05-03
I think the clonezilla mentioned above should work, but I have just used tar.  Set up the partitions on the new disk, add any filesystems, then from the old system mount the new fs (e.g. /mnt/new ) and from the root (/) of the old:
sudo tar -cf - * | (cd /mnt/new; sudo tar -xpBf -)
Then fix up the UUIDs for the new system in /mnt/new/etc/fstab and in /mnt/new/boot/grub/grub.cfg (or maybe just install grub to the new disk, and you should be all set).  Put the new disk first in the boot order and try it.  When it works, then think about removing the old system on the 1T disk.

---

### Post by migratorysean on 2014-05-16
Well, I ended up

Formatting secondary drive as NTFS
Moving a great deal of files over to it, including a good chunk of my Steam library and junction pointing them, as well as relocating my downloads folder.
Added a small partition and moved my Windows swap file to it.
Shrunk the Windows partition.
Moved then grew the Linux partition, as well as adding a little space to the Linux swap partition.

It was a bit of a pain, as the defragmenter I prefer would not relocate files properly to the shrink, so I ended up resorting to a tool for Paragon for that.  Did the Windows partition shrink in Windows, and everything else from a Gparted live CD.

Once everything was done, it worked a treat.

Cheers all!

---

