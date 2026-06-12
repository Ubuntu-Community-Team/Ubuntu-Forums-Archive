---
title: "failed grub installation"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by unisol on 2007-11-06
i have a laptop with vista installed.( acer 5100 with 2gig ram and 160gb hd) i tried to install gutsy 7.10, all went well until about 95% and i get a message grub failed to install. vista on hde2, gutsy on hde3. hde1 has some acer data from a previous version of windows. i have installed gutsy on another system, no problem. anyone help?

---

### Post by LaRoza on 2007-11-06
Can either OS boot?

---

### Post by unisol on 2007-11-06
yes i can still boot into windows vista.

---

### Post by LaRoza on 2007-11-06
Laptops sometimes have hidden partitions on them. I would search the forum / internet for your laptop and installing Ubuntu.

-EDIT I see from you original post there is a partition there. That is most likely interfering with the installation of Grub.

---

### Post by unisol on 2007-11-06
so what do i do with it? i think my problem is a dumb one. i made hde1 the swapfile. leaving no partition for the maser boot record. what to do?

---

### Post by unisol on 2007-11-07
i did a fdisk -l :

device boot     start   end    blocks  id   system

/dev/hda1         1       637   516671 82   linux swap
/dev/hda2       638    10015 7532875 7   hpfs/ntfs
/dev/hda3    10016   19457 75842865 c   w95 fat32 (lba)

anyone help?

---

### Post by bulldog on 2007-11-07
Curious were your ubuntu is installed,see only three partitions and no linux only a swap.

---

### Post by unisol on 2007-11-07
i guess whn the grub installation failed so did the ubuntu. i tried to install it on hde3.

---

### Post by bulldog on 2007-11-07
Ubuntu uses the ext3 file system not FAT32!
So when you install again,choose manual partition,mount the swap as swap and format it as swap
Mount the third partition as /  [root] set the bootflag on enable and set it to format ext3
Proceed with the install.

---

### Post by unisol on 2007-11-07
i know aabout the different filesystems for different os, i selected format hda3 as ext3 and somewhere along the line it failed. i have installed ubuntu  and debian since 2004, but, always on a desktop, never  a laptop. so this is a little different. but with you guys help,i should get thru it. thanks for your quick response. it is greatly appreciated!

---

### Post by unisol on 2007-11-07
i tried installing it again still wont install the grub bootloader. i repartitioned the drive giving ubuntu a 30gb partition ext3, but it still fails in the end.

---

### Post by bulldog on 2007-11-07
Can you try manual install grub with the live cd and keep an eye on errors?
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr[b] but be carefull here,if the find command returned (hd1,?)
the setup should be (hd1) not (hd0)!! [/b]
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by unisol on 2007-11-07
when i type find /boot/grub/stage1 i get an error15.do you think if i took say 100mb from the swap partition and formatted it as boot. would that work,without trashing the drive. my wife and daughter prefer windows.

---

### Post by bulldog on 2007-11-07
15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

It seems it didn't install.
Did you check the cd for errors?
Maybe try a new download [use the alternate cd if you do]
This one won't install I guess

---

### Post by unisol on 2007-11-07
i used this cdrom for my desktop no problem. but maybe it got scratched . ill burn a new one or download the alternate-install.

---

### Post by bulldog on 2007-11-07
Well making a separate boot partition I don't know if this makes  a difference,it won't install and failing to install grub is no reason to not install the file system.

---

### Post by unisol on 2007-11-07
i checked the cd integrity, no errors. i guess ill download th e alternate install.

---

### Post by bulldog on 2007-11-07
reading things back I saw something strange.
You mentioned several times you install to hde3 but the fdisk is talking about hda3,can you explain that to me?


i have a laptop with vista installed.( acer 5100 with 2gig ram and 160gb hd) i tried to install gutsy 7.10, all went well until about 95% and i get a message grub failed to install. vista on hde2, gutsy on hde3. hde1 has some acer data from a previous version of windows. i have installed gutsy on another system, no problem. anyone help?


i did a fdisk -l :

device boot start end blocks id system

/dev/hda1 1 637 516671 82 linux swap
/dev/hda2 638 10015 7532875 7 hpfs/ntfs
/dev/hda3 10016 19457 75842865 c w95 fat32 (lba)

anyone help?

---

### Post by farbror_ace on 2007-11-07
Dont want to hijack the thread but Im battling the exact same problem this evening:
[http://ubuntuforums.org/showthread.php?t=605995](http://ubuntuforums.org/showthread.php?t=605995)

Install goes fine until 96% configuring bootloader and crash.
See my thread for log error if it can help you in any way.

Also unisol can you check your log to see if we get the exact same error?

---

### Post by unisol on 2007-11-07
i meant hda3. my drive is a pata.  would that have anything to do with it?

---

### Post by bulldog on 2007-11-08
I have seen people who had the cd-rom as primary master and the hdd as slave device,they had problems with the mounting points.
But I don't think it's important in this case,just curious why you did  that.

---

### Post by unisol on 2007-11-08
im wondering if i delete hda1 (which use to be a acer data partition and the swapfile),create a new swap partition, maybe this would work?

---

### Post by bulldog on 2007-11-08
You can try but I,m out of options here.
Can't imagine hda1 could make this trouble,but than again,couldn't imagine ubuntu not installing either.
So try and see what happens.

---

### Post by unisol on 2007-11-08
i think it might work because this i believe was one of those hidden partitions that the manufacturer puts on the system,instead of giving you an installation disk.

---

### Post by bulldog on 2007-11-08
If you don't use it anymore,well  let ubuntu install on the whole hdd [first partition option I think] and it will be removed

---

### Post by unisol on 2007-11-08
bulldog, thanks for all your help. im going to give it a shot.maybe it will work.  windows is less hardware sensitive than linux. again thanks for your quick replys. ill let you know how i make out.

---

### Post by unisol on 2007-11-14
bulldog , i finally got gutsy installed using the giuded partitioning,using largest free continuous space. both linux and windows work. it was a last resort before trying other measures. but , it worked. thanks for your help.

---

### Post by bulldog on 2007-11-14
Very nice to hear you've got things solved and running.
Thank you

Have fun with ubuntu :guitar:

---

