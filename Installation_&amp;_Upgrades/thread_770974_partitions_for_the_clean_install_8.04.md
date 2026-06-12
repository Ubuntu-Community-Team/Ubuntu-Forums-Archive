---
title: "partitions for the clean install 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by the badger on 2008-04-27
hi all - i'm "this close" to install the heron but i'm a little uncertain about the options given in manual partitioning mode. clarity is much appreciated -- or if someone found a similar post, pls redirect me!
[LIST=1]
[*]i want to set up a /boot partition. i have a separate /boot now after grub error 18 occurred on installation of 7.10... do i use "EFI boot partition" as the use-as? (what is "EFI"?)
[*]i'm setting up "/"10gb -- "/boot"100mb -- "/swap"1gb -- "/home" gets the rest ...am i missing something?
[*]primary and logical... oh, my. i should remember this stuff, but i'm not sure. what gets what?
[*]things used to be hdb0...hdb3 (or whatever). this time around i'm seeing sda or similar(?) what gives? am i looking at the wrong thing?
[/LIST]
thanks are many.

---

### Post by the badger on 2008-04-29
bumpity bump.

hi :)

---

### Post by the8thstar on 2008-04-29
> [*]i want to set up a /boot partition. i have a separate /boot now after grub error 18 occurred on installation of 7.10... do i use "EFI boot partition" as the use-as? (what is "EFI"?)

If you are doing a clean install, you can remove your /boot partition. It is useless. The /boot FOLDER which is going to be created in your / (root) partition will contain all the needed info to properly boot the system.

> 
[*]i'm setting up "/"10gb -- "/boot"100mb -- "/swap"1gb -- "/home" gets the rest ...am i missing something?

Follow my signature for an idea of how to customize your disk. If you want to save yourself a partition, don't use /swap but instead create a swapfile instead in / for instance. It works just as well.

Her is the link for the how-to: [https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0]("https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0")

Finally, I would definitely advise you to create a /Home partition. If you need to reinstall or upgrade the system located on /, your files and settings will remain safe on /Home.

> [*]primary and logical... oh, my. i should remember this stuff, but i'm not sure. what gets what?

Check this out: [http://en.wikipedia.org/wiki/Disk_partitioning]("http://en.wikipedia.org/wiki/Disk_partitioning")

> 
[*]things used to be hdb0...hdb3 (or whatever). this time around i'm seeing sda or similar(?) what gives? am i looking at the wrong thing?

Either you're using a different type of hard disk (ie. SATA, eSATA or IDE), or Gparted (the GUI disk partitioner) identifies it differently than it used to. IMO, no worries there. :)

---

