---
title: "Cannot install Kubuntu 12.04 on Dell XPS8300"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by Ctulhu on 2012-07-17
Hi all

I have a Dell XPS8300 with 1.5TB hard drive which, it seems (I know nothing about RAIDs etc.), comes in the form of two 750 GB drives in some sort of RAID array (whatever the hell that means). I had Mint 11 installed there without problems. When I looked at the configuration, Disk Utility told me this:

SATA host adapter RAID controller
750GB /dev/sda   not partitioned
750GB /dev/sdb   not partitioned

Peripherals
1.5TB /dev/dm-0
30GB  /dev/dm-3 (swap)

I had things partitioned such that there was
- a 40GB or so / partition
- a 1.4TB or so /home partion
- a 32GB swap drive

I backed up everything and wanted to switch to Kubuntu 12.04, but the Kubuntu DVD can't handle whatever the Mint installer did. I ran the Dell boot tests and the Kubuntu set up tests and the hard drive etc. is fine. However, when I say "use entire disk so I don't have to worry about anything, I get "Executing 'grub-install /dev/sdb failed. This is a fatal error.
:
And when I want to set up my partitions like above again and click on "Manual" when the installer wants the disk info, then different things happened on different attempts but the list of drives etc. would show everything multiple times:

/dev/mapper/isw_bcdcfggdeb_ARRAY0
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p1 type: ext4 (40.3GB)
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p5 type: ext4 (1.4TB)
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p6 type: swap (32GB)
/dev/mapper/isw_bcdcfggdeb_ARRAY0p1               (40.3GB)
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p1            (40.3GB)
/dev/mapper/isw_bcdcfggdeb_ARRAY0p2               (1.4TB)
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p2p1     ext4 (1.4TB)
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p2p5     swap (32GB)
/dev/mapper/isw_bcdcfggdeb_ARRAY0p5               (1.4TB)
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p5       ext4 (1.4TB)
/dev/mapper/isw_bcdcfggdeb_ARRAY0p6               (32GB)
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p6       swap (32GB)
/dev/sdg                                          (2.1GB)
   /dev/sdg1                                 ext4 (2.1GB)

What can I do? I have no data loss but I can't use the computer ...

---

### Post by Ctulhu on 2012-07-17
In an attempt to at least get a running system again for now, I am trying to reinstall Mint 12 KDE and there the disk setup looks just very simple:

/dev/mapper/isw_bcdcfggdeb_ARRAY0
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p1 ext4 (40.3GB) /
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p5 ext4 (1.4TB)  /home
   /dev/mapper/isw_bcdcfggdeb_ARRAY0p6 swap (32GB)

The only thing I have to figure out now is which location to choose for the boot loader installation: one the above three or /dev/sda

Still, any feedback on my original question would be much appreciated, I would like to switch to Kubuntu 12.04, which I like better than Mint 12 (plus it's LTS).

---

### Post by darkod on 2012-07-17
If you look carefully, RAID support is specified under the Alternate CD image:
[http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/12.04/release/)

For best raid or lvm support, you need to use the alternate cd. If you use the standard cd, the installation of the grub2 bootloader often fails, like it happened to you.

---

### Post by Ctulhu on 2012-07-17
Thanks so much :-), downloading it now ...

---

### Post by darkod on 2012-07-17
Note that making 1.5TB array from two 750GB disks means they are in raid0, which means the data is written half on one disk, half on the other. That means if one disk dies, you lose everything.
There is no recovery possible since the good disk will have only half the data. That's why it's called raid0, there is no redundancy which you might expect when you hear the term raid.

You should plan regular backups, or consider configuring raid1 array (mirror) but that will give you only 750GB array usable. But in this case, if one disk dies, the other has all the data because they are mirrored.

---

### Post by Ctulhu on 2012-07-17
Thanks for that advice. I do need the whole 1.4 tho, but I am the king of backups, I have everything important in at least three locations so if the disk really were to die, so be it ;-)

---

