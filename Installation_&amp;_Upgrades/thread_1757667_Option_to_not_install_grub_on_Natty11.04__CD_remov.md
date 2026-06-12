---
title: "Option to not install grub on Natty/11.04  CD removed?"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2011-05-13
In previous versions, there was an 'advanced' button where you could select NOT to install grub. I can't find that in the latest Natty release iso's. Is it no longer an option? And if not, WHY? I find myself reloading Natty quite often on a test partition to play with various parameters in my attempt to get it working as needed. But I'd really prefer to have the option to no reload grub.

---

### Post by oldfred on 2011-05-13
If you are doing manual install (Something Else in Natty), you should have a combo box that lets you choose where to install grub2's boot loader to. 

Post #9 from Hedgehog1 shows the combo box in next to last graphic. They did change from beta to release from manual install to Something Else.
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by aeronutt on 2011-05-13
> **oldfred said:**
> If you are doing manual install (Something Else in Natty), you should have a combo box that lets you choose where to install grub2's boot loader to. 

Post #9 from Hedgehog1 shows the combo box in next to last graphic. They did change from beta to release from manual install to Something Else.
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Yes, I typically use the 'Something Else' option to load onto a current partition.
So I've looked at that, but none of the options on the pull down menu asking where to install grub, are "don't install". Am I missing something?

---

### Post by oldfred on 2011-05-13
Even the advanced button before did not have a do not install. There are many complaints but I have not seen anyone file a bug (but have not looked lately). 

Most just install to the Ubuntu partition. It is space not otherwise used anyway. Grub2 may complain about installing to a partition as it is less reliable using blocklists. Do not install to a windows partition as that has windows code in it.

---

### Post by aeronutt on 2011-05-13
> **oldfred said:**
> Even the advanced button before did not have a do not install. There are many complaints but I have not seen anyone file a bug (but have not looked lately). 

Most just install to the Ubuntu partition. It is space not otherwise used anyway. Grub2 may complain about installing to a partition as it is less reliable using blocklists. Do not install to a windows partition as that has windows code in it.

Maybe we're talking about 2 different things. I'm confident in 10.04 LTS and prior, when clicking advanced, there was an option to not install grub2.


Let me be specific about what I'm doing, maybe I'm asking the wrong question. I have several partitions on my HD.  1 is windows, 2 are used for Linux (plus the other typical maintenance partitions.)  I use 1 of the Linux partitions for my stable load I don't play with. I use the 2nd linux partition to screw around with things. There are a few simple things I like to change in the grub file. So.....when I install linux in my test partition, if it installs grub, I then have to manage grub in my test partition (re-edit, etc).

I'd really prefer to install linux in the test partition w/o installing grub, then just run update-grub when in my stable partition.

Hope this explains what I'm up to. If there's a better way, I'm all ears.

Thanks for you help!

---

### Post by aeronutt on 2011-05-13
Here we go. In 10.04LTS, I would just unclick the Install Boot Loader button.

[IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/large/ubuntu1004installation-large_008.jpg[/IMG]

---

### Post by Quackers on 2011-05-13
As oldfred said earlier, that stopped at 10.04. The 10.10 installer did not have that option and neither does the 11.04 installer. Pity really as it comes in handy in multi OS installations.

---

### Post by aeronutt on 2011-05-13
Well that bites. I noticed a few versions ago that Mint started doing this, and now Ubuntu. I just don't understand this decision. By the way, along with 'solved', there should be an option to put 'unsolvable' tag on a thread. :)

---

### Post by Quackers on 2011-05-13
Lol, that's a good idea :-)

---

### Post by drs305 on 2011-05-13
I'm not disagreeing with the point - in fact, I strongly agree the user should have the choice. If doing a manual installation with the partitions already created, a workaround might be to make a copy of the MBR with the dd command (or don't include the partition table), let the installation do it's thing, and then recopy the original.

---

### Post by aeronutt on 2011-05-13
> **drs305 said:**
> I'm not disagreeing with the point - in fact, I strongly agree the user should have the choice. If doing a manual installation with the partitions already created, a workaround might be to make a copy of the MBR with the dd command (or don't include the partition table), let the installation do it's thing, and then recopy the original.

Could you help me better understand what this might look like? (I think it was 1990 the last time I used the dd command. :))

---

### Post by drs305 on 2011-05-13
First, remember 'dd' is not nicknamed 'data destroyer' without reason, so be careful.

Second, I would wait for someone else to offer an opinion this might work. The commands below are correct, but whether installing G2 would also write to a portion of the MBR beyond this *and* mess up something with a Windows or other OS installation I don't know.

The commands would be:
```
sudo dd if=/dev/sda of=~/Desktop/oldMBR.img bs=**446** count=1
```
446 is for saving w/o partition table, use 512 if want to include partition table 
To restore: 
```
sudo dd of=/dev/sda if=~/Desktop/oldMBR.img bs=**446** count=1
```

---

### Post by aeronutt on 2011-05-13
Thanks very much, I'll wait for additional opinions. Seems this might be something others might want also!

---

### Post by drs305 on 2011-05-13
When Grub 2 first came out I used this method many times while experimenting with Grub installations. 

I'm fairly sure it will work, as I also played with the *lilo* bootloader and we use this to restore Windows fairly frequently. However, I try not to post commands or procedures which I have not accomplished on my own machines at some point. I always was doing this procedure on an Ubuntu machine and not one with a Windows dual boot.

---

