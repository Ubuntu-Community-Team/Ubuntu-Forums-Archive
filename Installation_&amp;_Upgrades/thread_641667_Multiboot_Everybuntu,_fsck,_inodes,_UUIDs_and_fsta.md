---
title: "Multiboot Everybuntu, fsck, inodes, UUIDs and fstab."
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by stoodleysnow on 2007-12-15
I have set up my laptop to run all the major Ubuntu distros, with the intention of using it to demonstrate the pros and cons of each. I thought I'd let you know how I got it to work together.
Acer Aspire 5633WLMi laptop
120GB Toshiba HDD, divided thus:
|------------------60GB-------------------|[COLOR="Navy"]|--12GB--||--12GB--||--13GB--||--13GB--||Sw|[/COLOR]
Blue = Extended partition.
I already had Ubuntu installed over the whole hard drive. I used GParted on the Ubuntu LiveCD to shrink the Ubuntu partition to about 60GB, and to expand the extended partition in which the Swap space already resided; to fill the rest of the space (now freed up) on the Hard Drive. Then I created four small ext3 partitions in the extended partition, and installed Kubuntu, Edubuntu, Xubuntu then Fluxbuntu The result:
sda1 60GB Ubuntu
sda6 12GB Kubuntu
sda7 12GB Edubuntu
sda8 13GB Xubuntu
sda9 13GB Fluxbuntu
sda5 Swap
Fine, or so I thought. But during the installation of Kubuntu, I had a problem with the DVD drive. Each time I opened or shut it, it switched off the laptop (the cause was deduced to be a loose connection). 
This had the effect of leaving an inode disconnected on sda6 (a corrupt bit of hard drive in laymen's speak). Furthermore, the fact that I had created all the partitions beforehand meant that, on installing the OSes, each one would reformat its partition (because they have to), therefore changing its partition's UUID without the already installed OSes knowing, the already installed OSes still listing in their fstab the old partitions's UUIDs. So each OS did not realise that the next one had reformatted its partition. (except Ubuntu where I reinstalled GRUB) This had the following effects:

Each time I booted Kubuntu, Edubuntu or Xubuntu it forced an fsck check. 
In Kubuntu, the errors were: fsck sda6 disconnected inode
                                              fsck.ext3: Unable to resolve 'UUID = (long string of hex)'
                                                                                            'UUID = (another long string of hex)'
                                                                                            'UUID = (yet another long string of hex)'

In Edubuntu, the errors were: fsck.ext3: Unable to resolve 'UUID = (another long string of hex)'
                                                                                            'UUID = (yet another long string of hex)'

In Xubuntu, the error was: fsck.ext3: Unable to resolve  'UUID = (yet another long string of hex)'
:(
Fluxbuntu, being the last one installed, listed all the UUIDs correctly.
After a sleep, my head clear, I went on.
I ran fsck sda6 as root from Ubuntu, which fixed the inode.
Since Fluxbuntu has no errors, its fstab is the correct one. The best bet is to copy the UUIDs from Fluxbuntu's fstab and use them to replace the incorrect UUIDs in Kubuntu, Edubuntu and Xubuntu's fstabs. That done, I had finally solved the problem! Moral to this part: do not pre-partition. Leave an empty extended partition, and add logicals one by one during installation.

Next,** Compiz Fusion/Emerald combo**. It will work in Ubuntu, Kubuntu, Edubuntu, Xubuntu. But not (at least not easily) in Fluxbuntu.

Interestingly, I can **access and edit my existing files** in my Ubuntu home directory from all of the other distros. Whether this is because I have the same username and password on them all or just good compatibility, I don't know. But it's pretty useful!

So now I can show off all the different versions of what Ubuntu can offer on my laptop. :)

If this post can be of any use to you, cool. Replies are good.:popcorn:

---

### Post by stoodleysnow on 2008-02-25
Bump

---

