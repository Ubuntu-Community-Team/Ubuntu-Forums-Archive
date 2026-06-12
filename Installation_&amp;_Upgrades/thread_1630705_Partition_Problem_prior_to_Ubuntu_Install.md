---
title: "Partition Problem prior to Ubuntu Install"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by Luke11 on 2010-11-25
Hi,

I've been running Ubuntu off the LiveCD and am ready to do the install along side my existing Vista OS. Knowing next to nothing about Linux, I decided to go the easy route and shrink my primary partition via the Disk Management Utility in Vista.

When I went to perform the shrink I noticed I had a 1.6GB partition ahead of my active partition (see attached). It's labeled EISA configuration? Not really sure what this is, but I'm told my OEM put this there to allow the system to be restored to "factory settings". 
Anyway, my problem is I am unable to shrink the active partition? The shrink button is grayed out and all zeros are filled in. I wonder if this tiny partition has anything to do with this. I am also unable to delete this smaller partition.

Finally, when running the Ubuntu LiveCD, I can use both DiskUtility and GParted to perform any number of operations on either partion, including deleting the 1.6GB. I wasn't too sure about this so I didn't do anything.

If anyone can take a look at the screenshot and offer any suggestions, I'd appreciate it.

Thanks.

---

### Post by coffeecat on 2010-11-25
This is not uncommon, and the 'EISA' partition is not to blame. Have a look at this for an explanation and some possible workarounds:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by wilee-nilee on 2010-11-25
:-\"

---

### Post by coffeecat on 2010-11-25
> **wilee-nilee said:**
> You have the Windows partition 70% full 

Actually, it's 70% free. :) So, hopefully the OP should be able to move whatever's at the end of the partition.

---

### Post by wilee-nilee on 2010-11-25
> **coffeecat said:**
> Actually, it's 70% free. :) So, hopefully the OP should be able to move whatever's at the end of the partition.

Should have looked closer my bad.:-\"

The second de-fragger mentioned is the one that will move everything, although it runs slower in general, and to get it to really work it defraggs at startup off line of the actual install.

I use the auslogics defragger myself works fast and is quite efficient.

---

### Post by Luke11 on 2010-11-25
> **coffeecat said:**
> This is not uncommon, and the 'EISA' partition is not to blame. Have a look at this for an explanation and some possible workarounds:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)


Thanks for the suggestions. I took a look at the article and judging by the comments it looks like it may take a combination of following the instructions and also running PerfectDisk. Assuming I can move the MFT and other necessary files and then shrink the Windows partition, I'm wondering if the presence of this other partition is going to give me a problem when it's time to install Ubuntu?

---

### Post by coffeecat on 2010-11-26
> **Luke11 said:**
> I'm wondering if the presence of this other partition is going to give me a problem when it's time to install Ubuntu?

I should think unlikely. It's some sort of maufacturer's utility and won't interfere with Ubuntu. As it's a primary partition it will have used one of your allowance of four primary partitions, but that won't be a problem because, once you've shrunk the Vista partition, you can create an extended partition in the space for as many logical Linux partitions as you might need. That's one of the benefits of Linux. It can happily live in and boot from a logical partition, unlike Windows which needs its boot files in a primary partition.

---

### Post by Luke11 on 2010-11-28
Coffeecat - I just want to make sure I understand what you're saying. Assuming everything goes according to plan, after I shrink the Windows partition, I will be left with two primary partitions. I will also be left with a chunk of free space at the end of the second partition.

I then need to create the Ubuntu partition. I've been thinking that would also be a primary partition. Are you suggesting I would be better off creating an extended partition with the free space? Does it matter? Finally, what method do I use to do this? Do I do this again from within Vista or do I use the Ubuntu installer?

Sorry, to go over this again. I'm just trying to avoid mucking up my laptop.

---

### Post by coffeecat on 2010-11-29
> **Luke11 said:**
> I've been thinking that would also be a primary partition. Are you suggesting I would be better off creating an extended partition with the free space? Does it matter?

You would be better off making an extended partition in the free space and then as many logicals as you need in the extended. The main reason for this suggestion is that it gives you much more flexibility now and for the future. You can only create two more primary partitions and you need, as a minimum, two partitions for Ubuntu - not one. There will be your root partition  and a separate small swap partition. Linux can use a swap file like Windows but the usual (and easier) option is to have a dedicated swap partition. In addition to these two, some people like to have a separate /home partition and/or you might want to consider creating a separate data partition formatted NTFS which can be used by both Windows and Ubuntu.

You must create your partitions with Ubuntu. Windows knows nothing about Linux filesystems and cannot create a partition with the ext4 filesystem you need for Ubuntu. Also, it oversimplifies how it presents the partition layout and doesn't distinguish between primary and other types of partition. If you use the Vista Disk Management tool you will probably end up with only primary partitions, all formatted NTFS, which won't do at all. Gparted in the live CD can create NTFS filesystems as well as Linux ones, so you can do all your partitioning with that.

One thing to beware of if you are installing from the 10.10 Maverick live CD. There used to be an option in the installer to install to 'continuous free space' (or words to that effect). In your situation that would have been the easiest option. But this has been removed from the Maverick installer, much to many people's justifiable annoyance. What you probably need to do is to work out what partitions you need beforehand and then set them up with Gparted in the live CD session before you start the installer. Then, when you get to the partitioning stage of the installer, choose the manual (advanced) option. I believe you can also set up partitions directly in the manual option if you have free space. As this is all a bit daunting if you're new to this, have a look at this link:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Follow all the links in it. It has most of what you need.

---

### Post by Quackers on 2010-11-29
I tend to set up new Linux partitions as and when required by choosing the "specify manually" part of the installer. You just click on the free space and then "change" and create to your heart's content :-)

The "install alongside" option is fraught with danger in its present form!!!

Also, with Vista, it seems to be the case that if the Vista partition has been resized once, it will not allow a second resizing via the Disk Management console. I have come across this before and I needed to use the Gparted Live CD to do it. Obviously using this method there is a small risk of corruption, but mine ran ok.

---

### Post by coffeecat on 2010-11-29
> **Quackers said:**
> The "install alongside" option is fraught with danger in its present form!!!

Thanks for mentioning that, Quackers. I'd read some disaster stories but couldn't remember the details. What with the disappearance of the 'free space' option and the potential for the 'install alongside' to wreak havoc, it seems that the only options left are to use the whole disc if you want to get rid of Windows completely or the manual/advanced option if you need to do anything more demanding.

@Luke11, don't be put off by the 'advanced' label in the manual option. You have to know something about partitions and you don't have a wizard to follow, but if you take it easy it's not that off-putting. And you can bail out before you commit to changes if necessary.

---

### Post by Quackers on 2010-11-29
Absolutely, coffeecat.
Manual partitioning is scary but you just need to be careful.
You must make sure you are using the correct disc (if you have more than one) - ask me how I know :-)

---

### Post by Luke11 on 2010-11-29
OK, well, thanks Coffeecat for the lengthy explanation. And thanks to you Quackers as well. I think I have everything I need. I will give this a whirl and see what happens. ;)

---

