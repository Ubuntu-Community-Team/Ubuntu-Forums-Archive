---
title: "Install Xubuntu on 50GB partition"
date: 2014-06-04
forum: Installation &amp; Upgrades
---

### Post by feb3 on 2014-06-04
It has been a few years since I last installed Ubuntu (10.04 IIRC) and I have lost a bit of confidence.  
I have a 50GB partition already created and I want to have 10GB for Xubuntu, 2GB Swap (I have 2GB RAM) and the rest (41689MB) for Home. 
Before I click 'Continue' I wonder if someone would just check these screen shots and confirm that I am going in the right (or wrong) direction?

Thank you.

---

### Post by sudodus on 2014-06-04
> **feb3 said:**
> It has been a few years since I last installed Ubuntu (10.04 IIRC) and I have lost a bit of confidence.  
I have a 50GB partition already created and I want to have 10GB for Xubuntu, 2GB Swap (I have 2GB RAM) and the rest (41689MB) for Home. 
Before I click 'Continue' I wonder if someone would just check these screen shots and confirm that I am going in the right (or wrong) direction?

Thank you.

I think it will work like this, but I would prefer to have somewhat more space for the root partition. For example you might need space for large temporary files (in /tmp).

---

### Post by feb3 on 2014-06-04
Thank you. It is a relief that I am at least going in the right direction. I was a bit concerned whether the 'Device for boot loader installation' was right because it gives you different options. As for the 10GB to root, I could just as easily change it.  What would you suggest - perhaps 15GB?  I have never allocated separate space for /tmp - is that necessary?  I have no shortage of space because I don't tend to store much on the computer. I did consider allocating the whole drive to Xubuntu, which would have been easier but I could do with retaining the Windows partition in case my main W7 laptop goes down (I have software that I need which won't work on Linux).

---

### Post by sudodus on 2014-06-04
Wait a minute! I did not catch that.

You should install the bootloader into the head of the drive, ***/dev/sda***, not to a partition (where it will be 'lame' unless you chainload to it).

---

### Post by feb3 on 2014-06-04
Thank you - not installed yet. Just waiting for a few more replies. So the Device for boot loader installation is the top one in the list above which is (as you say) /dev/sda?

---

### Post by sudodus on 2014-06-04
15 GB for root is much better :-)

It is not necessary (and not recommended) to have a separate partition for /tmp. Use the free space in the root partition for that purpose. But you need a good margin above what is needed, when you have installed some extra program packages.

It might be a good idea, if you are short of space, to have only a root partition and no home partition. This gives you one single 'free space' instead of small chunks in two partitions. But a separate home partition has many advantages, and I think it is a good idea to stick to that configuration.

---

### Post by sudodus on 2014-06-04
> **feb3 said:**
> Thank you - not installed yet. Just waiting for a few more replies. So the Device for boot loader installation is the top one in the list above which is (as you say) /dev/sda?

Yes (unless you want it in another drive, and then it should be /dev/sdb or /dev/sdc ...)

---

### Post by stalkingwolf on 2014-06-04
am i missing something?  You are wanting to make seperate partitions for root / , home and swap correct?  all those are primary partitions. as i recall it will only allow 4 primaries so some place there will have to be a logical partition in to which the extra partitions can go.

---

### Post by ajgreeny on 2014-06-04
If you do not have a UEFI system you will need to use all that 50GB partition, sda3, as a new extended partition and then make the three logical partitions you want to use within that; Linux will boot fine from a logical partition, unlike Windows which will throw a wobbly, and refuse to boot from a logical partition.

PS:  Whilst I agree in principle with sudodus's comment about root size, I have never had any of my root partitions larger than my current Xubuntu 12.04 which is 6.4GB.  However, 15GB is probably worth using unless you are really short of space.  Don't forget you can open any Windows files using Ubuntu, though for safety do not open any windows system files, but you can not read your Ubuntu partitions using windows unless you install a separate ext# driver , which in the days I used it with WinXP was not very successful; it may now be better and safer.

---

### Post by feb3 on 2014-06-04
Thank you for the replies. 
> am i missing something? You are wanting to make seperate partitions for root / , home and swap correct? all those are primary partitions. as i recall it will only allow 4 primaries so some place there will have to be a logical partition in to which the extra partitions can go. 
I need to clear this up before installing; I hadn't realised that all of those partitions are primary. IIRC this is how I did it years ago when I was using Ubuntu/Mint 9 and 10 but I may be wrong.  Although I am a bit further on in my recall of events now, I can't remember the installer asking whether they should be primary or logical partitions. I really do want the separate root, swap and home partitions.  If someone could just clear this logical/primary partition business up for me, I think I could go ahead.  Alternatively, I have the option of waiting a couple of days as there is a LUG meeting in a neighbouring city. It is important that I do it myself but hopefully someone there can watch me then I would know that I have it right.

---

### Post by Bucky Ball on 2014-06-04
*Thread moved to **Installation & Upgrades**.*

Please do not insert large pics into the body of your posts. Use either 'Go Advanced' or 'Adv. Reply' and use the paperclip icon in the editing toolbar to attach them.

---

### Post by sudodus on 2014-06-04
It is OK to have 3 primary partitions and one extended partition as a container for the rest of the partitions you need.

But if you want Windows you had better start installing that and then install Ubuntu (and other linux distros). Otherwise you have to repair at least the linux bootloader. And depending on Windows version you have different options.

Older Windows versions want a primary partition. Newer Windows partitions may come with or want a GUID partition table (GPT) and UEFI (instead of the classical MSDOS partition table with max 4 (primary) partitions, or up to 3 primary partitions and one extended partition).

The GUID partition table can manage many partitions without resorting to extended partitions, but it needs special partitions to boot in BIOS mode as well as in UEFI mode.

---

### Post by feb3 on 2014-06-05
Thank you for all the advice and I apologise for posting the attachments incorrectly. I see that the mods have amended that so again, thank you for that.
I was unsure what UEFI is so I have checked it out and I forgot to mention that the W8 that is on the hard drive is an upgrade from Vista so it does not have secure boot.  Hopefully I will be able to get on and install later, although at this stage I am thinking of just putting Xubuntu on the 50GB partition as a whole without the three separate partitions - it may be enough for now.
Regards to all who have responded.

---

### Post by sudodus on 2014-06-05
You need not use three separate partitions - it may be enough with two - the root partition '/' and the swap partition. But it is fairly simple to create and use an extended partition, and linux is happy even to boot from a logical partition inside an extended partition. So as long as you don't fill all four slots for primary partitions, it is OK, you can create an extended partition. It is possible to have 0, 1, 2 or 3 primary partitions and one extended partition. It is possible to let Windows have its primary partitions and then have all linux partitions inside an extended partition.

(Only when Windows is set up with four primary partitions, there are 'partition problems' to make a dual boot system. Then the least important partition must be removed from the partition table. That partition is usually small, so disk space must be made unallocated by shrinking the Windows partition. Finally an extended partition can be created using the largest chunk of unallocated space.)

-o-

In other words, if you want a home partition, make one, even if it means that you need an extended partition and logical partitions inside it.

---

### Post by fantab on 2014-06-06
> I need to clear this up before installing; I hadn't realised that all of  those partitions are primary. IIRC this is how I did it years ago when I  was using Ubuntu/Mint 9 and 10 but I may be wrong.  Although I am a bit  further on in my recall of events now, I can't remember the installer  asking whether they should be primary or logical partitions. I really do  want the separate root, swap and home partitions.  If someone could  just clear this logical/primary partition business up for me, I think I  could go ahead.  Alternatively, I have the option of waiting a couple of  days as there is a LUG meeting in a neighbouring city. It is important  that I do it myself but hopefully someone there can watch me then I  would know that I have it right.

Logical Partitions (as commonly understood) are part of MBR(msdos) partition table that went with BIOS since the beginning of PC time.
MBR Table (which is what you probably have on HDD) has an ONLY FOUR Primary partitions limit. 
If you need more than four Partitions then you will use an **Extended Partition**, which is a Primary Partition but is just a container for the Logical partitions.
So you'd create one Extended Partition of the four allowed and then make further partitions in it to make Logical Partitions. You can have more than 100 Logical Partiions.

You only have 50Gb to manage. I guess your idea of 3 partitions (which will be Primary by default)... is good.
15Gb Ext4 Xubuntu /
2Gb SWAP
33Gb Ext4 /home

---

### Post by Bucky Ball on 2014-06-06
Make an extended partition, then, which takes up most the drive. You can stick as many logical partitions in there as you like. Otherwise, a physical disk is limited to four partitions, doesn't matter how you go about it, extended or primary. _This you must remember._ ;)

---

### Post by feb3 on 2014-06-18
Please could someone explain about / and /boot? I am about to install Xubuntu now and it is asking for mount point. Presumably I use /?

---

### Post by sudodus on 2014-06-18
***/ is the root partition***. If you have only one mounted partition, this is the one. (In addition to that we recommend a swap partition.)

If you want to you can have a /boot partition, a /home partition etc. There are advantages and disadvantages to use several partitions. The standard (automatic) installation will only create a root partition and a swap partition.

---

### Post by feb3 on 2014-06-18
Thank you for helping me out Sudodas.  I have decided to do a simple install on that partition and have attached graphics of how far I have got. Please could you tell me if I am now ready to click 'install'?  Thank you.

---

### Post by sudodus on 2014-06-18
It looks good to try to use /dev/sda3 for the root partition and to create an ext4 file system in it.

***But*** you have forgotten the swap partition.

I suggest that you change your plans and ***make /dev/sda3 an extended partition***.

Inside that partition you create one big partition for the root file system (it will probably become /dev/sda5) and one small partition for swapping (probably /dev/sda6). You can use the installer for these tasks, but I think it is easier (more intuitive) to use ***gparted***.

Gparted comes with the Ubuntu install iso file, and is available in the live session.

---

### Post by feb3 on 2014-06-18
Thank you for all the advice.  Pleased to say that I have managed to install Xubuntu (dual boot) as originally planned, with the three partitions.  Root is primary and the other two logical. 
The reason I couldn't remember how to do it is because the installer is different to how it used to look.  I hadn't clicked on the minus sign to convert the partition to free space.   Following the instructions [here](http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/) it suddenly all came back to me and I now have Xubuntu up and running. It is first to boot, have to use the down arrow to select Windows.

---

### Post by Bucky Ball on 2014-06-18
Good news. So what partitions do you have? You say you have / and two others. Are we to presume these two have the mountpoints /boot and /home. If so, again, you have omitted the /swap partition. It only needs to be 2Gb, so if you have not included a /swap I suggest you boot from the LiveDVD/USB, launch Gparted, shrink the last partition in the extended partition and leave 2Gb of free space, then create /swap there.

---

### Post by feb3 on 2014-06-19
I have the root partition / (Xubuntu) which is 15GB and primary, then I have swap at 4GB and logical. Sounds like I didn't need so much but I remembered from last time reading that swap should be double the amount of RAM. The third partition is /home and logical.  It is not quite as snappy in operation as I thought it would be but it is better than Windows and perfectly acceptable. 

FWIW I think that the installer could do with being a bit more user-friendly.  I am old so have to think about things for a bit longer but even so the system of having to click on the minus sign to convert the second partition to free space is not very obvious.  If I had known this, I'd have managed it before and not needed to start this thread.  I did look at various websites too but couldn't find the answer to getting started. Is there anyone who agrees that there could be a better way of doing this?  I can't remember it being so vague when it was 9.04.  Sorry - I'm probably just a dim old person but Linux has made great strides to be usable for the masses and I just think this is not so clear for some of us.

---

### Post by LastDino on 2014-06-19
That SWAP being double the amount of RAM is old instruction for really really low RAM machines. These days, you only need it in equal amount of RAM if you plan to hibernate and if not, you should keep it around for 2GB. If you've machine that has 8+GB RAM, you may even choose to not make it. But since you've made it, let it be.

Actually, part you're referring to is Gparted and not an installer itself, and IMO, it is admittedly not easy to deal with if you're not used to, but in terms of handling by new users, it is better than its counterparts, including windows partitioning tool you see when installing windows.

---

### Post by sudodus on 2014-06-19
You have a root partition, a swap partition (twice the size necessary but it is OK), and a home partition. And Xubuntu is working for you. Congratulations :KS

I suggested that you use ***gparted*** to do the partitioning work. It is much more intuitive for that purpose compared to the installer. But you can do it with the installer too.

---

### Post by Bucky Ball on 2014-06-19
Excellent. Please mark the thread as solved to help others and post new threads for any further issues (marking as 'solved' does not close the thread, and consequently, will not end any further discussion on this topic).

---

### Post by feb3 on 2014-06-19
Thank you. Have marked the thread solved, as requested. Just in case it is useful for others, I found the itsfoss website very good for instructions.  I mentioned it above but [here is the link](http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/) in case anyone is interested and missed that previous one.

---

