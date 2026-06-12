---
title: "trying to do a simple install"
date: 2018-02-26
forum: Installation &amp; Upgrades
---

### Post by torm on 2018-02-26
I just bought a netbook, want to wipe windows 10 and just have xubuntu (with a 4gb swap space). I was playing around with the installer and the (automatic) Erase Disk option doesn't seem to give me the option to choose a size for a swap partition. Meanwhile, the manual install option shows me a bunch of stuff that I don't really understand yet. In particular, it shows that I currently have 4 partitions and I'm not entirely sure what each partition is for, so I'm not sure what to do for the manual install. In any event, can anyone advise me on how I can install just xubuntu and have a 4gb swap specifically? Thanks.

---

### Post by vasa1 on 2018-02-26
Which version of Xubuntu?

Details of the netbook?

---

### Post by torm on 2018-02-26
16.04.03 LTS

This is the netbook:

[https://www.amazon.com/VivoBook-E203NA-YS02-Featherweight-Dual-Core-processor/dp/B076BFSMPV](https://www.amazon.com/VivoBook-E203NA-YS02-Featherweight-Dual-Core-processor/dp/B076BFSMPV)

I haven't done anything with it, but for some reason it already has 4 partitions:

mmcblk0p1 260MiB FAT32
mmcblk0p2 16MiB unknown
mmcblk0p3 57.2GB NTFS
mmcblk0p4 800MiB NTFS

The 57.2gb partition makes sense to me. The rest of it doesn't.

---

### Post by vasa1 on 2018-02-26
Re. the four partitions, here's an oldish link to get started: [https://www.bleepingcomputer.com/tutorials/understanding-hard-disk-partitions/](https://www.bleepingcomputer.com/tutorials/understanding-hard-disk-partitions/)

If you search for why do windows machines have four partitions, you'll get a lot more information

---

### Post by torm on 2018-02-26
Thanks for the link. My takeaway is that windows does complicated things for reasons that don't matter to someone switching over to linux. :)

Back to the original question, is there a way to do an Erase Disk install and ensure that a (specifically) 4gb swap partition is created? Does the erase disk option even create a swap partition? If not, I'm also fine with creating a swap file after the fact. Thanks.

---

### Post by kerry_s on 2018-02-26
in the later versions of ubuntu it use a 2gb swap file, so no swap partition is made when you select erase disk.
before that it created a partition equal to your ram.

more than 2gb swap is fairly useless, as it's slow compared to actual ram.

what version of *buntu are you going for?
what are your current specs?

---

### Post by vasa1 on 2018-02-26
Again, which version of Xubuntu are you planning to go with?

IIRC, Canonical decided to do away with "swap" as implemented earlier and move to some sort of swap files: see [https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files) and the links it provides.

---

### Post by monkeybrain20122 on 2018-02-27
> **vasa1 said:**
> Again, which version of Xubuntu are you planning to go with?

IIRC, Canonical decided to do away with "swap" as implemented earlier and move to some sort of swap files: see [https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files) and the links it provides.

But OP can always create a swap partition if he uses the advanced/manual option to install. I could be wrong but my understanding is that if you want to put the laptop to sleep you need a swap partition, swap files won't do it.

---

### Post by vasa1 on 2018-02-27
> **monkeybrain20122 said:**
> ... I could be wrong but my understanding is that if you want to put the laptop to sleep you need a swap partition, swap files won't do it.
Or you could be right! I haven't looked at this aspect at all.

---

### Post by torm on 2018-02-27
> **vasa1 said:**
> Again, which version of Xubuntu are you planning to go with?
.

[COLOR=#000000]Still, 16.04.03 LTS. :)

[/COLOR]> 
[COLOR=#000000]But OP can always create a swap partition if he uses the advanced/manual option to install. I could be wrong but my understanding is that if you want to put the laptop to sleep you need a swap partition, swap files won't do it.


Wouldn't mind seeing some verification on this.

> 
[/COLOR][COLOR=#000000]IIRC, Canonical decided to do away with "swap" as implemented earlier and move to some sort of swap files: see [/COLOR][https://www.omgubuntu.co.uk/2016/12/...ons-swap-files]("https://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files")[COLOR=#000000] and the links it provides.


Yeah, that's 17.04 and later. I'm using the current LTS. Though, that will likely be of concern when 18.04 LTS is released and I change over to that.

So, the Erase Disk option doesn't seem to give an indication as to whether it creates a swap partition, swap file, or nothing. And, if the former two, what size it creates. Is there a way to find out what exactly it does? Thanks.[/COLOR]

---

### Post by LHammonds on 2018-02-27
When installing Xubuntu and presented with this screen:

Installation Type
 * Erase disk can install Xubuntu
 * Encrypt the new Xubuntu installation for security
 * Use LVM with the new Xubuntu installation
 * Something else

Choose "Something else"
Remove any partitions you do not want (except any "efi" partition) using the - sign button, then select "New Partition Table"

Look  through  [this  article]("https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation") for detailed steps.

**EDIT:**  If you want to setup custom partitions and use LVM, you will need to do a bit of terminal work.  [HowTo: Set up Ubuntu Desktop with LVM Partitions](https://help.ubuntu.com/community/UbuntuDesktopLVM)

LHammonds

---

### Post by ubname on 2018-02-28
> **torm said:**
> I just bought a netbook, want to wipe windows 10 and just have xubuntu (with a 4gb swap space). I was playing around with the installer and the (automatic) Erase Disk option doesn't seem to give me the option to choose a size for a swap partition. Meanwhile, the manual install option shows me a bunch of stuff that I don't really understand yet. In particular, it shows that I currently have 4 partitions and I'm not entirely sure what each partition is for, so I'm not sure what to do for the manual install. In any event, can anyone advise me on how I can install just xubuntu and have a 4gb swap specifically? Thanks.

I understand that you would like to have 4Gb swap but unless you do not have any specific reason to do so I would trust the Ubuntu team and go for the default that's erase all and install ubuntu.
The 16.04 release is surely a good choice but at this point for a simple laptop I would use 17.10 that is "more optimized" for SSD drive (as you have), then you can reinstall 18.04 in 3/4 month and enjoy the same experience.
In 17.10 (and 18.04) you do not have to worry about swap it's automatically managed and it is "more SSD friendly, and you surely can put your pc to sleep.
Also remember that _all windows partition and data will be erased_, so backup.

HTH

---

### Post by kerry_s on 2018-02-28
when you click continue its shows you what it's gonna do.

just select "something else" & do it manually it's not hard.

i chose erase, heres what it did on mine:
[ATTACH=CONFIG]278714[/ATTACH]

as you can see i have 2 partitions & from the system motor i can see it has 2gb of swap. i also know theres a mount for the swap file in fstab.

---

### Post by torm on 2018-02-28
> **ubname said:**
> 
Also remember that _all windows partition and data will be erased_, so backup.

So, I tried to backup the system. I got a 32gb flash drive and followed some instructions (I think even on microsoft.com) to create a recovery drive. It errored and said that a recovery drive couldn't be created. Apparently, this is a known thing with Windows 10. Do you any other way to create a recovery drive for the factory settings on this thing? Thanks.

EDIT: Just for funsies, I tried out the "broken" recovery drive and it worked just fine. Onwards and upwards I guess.

---

