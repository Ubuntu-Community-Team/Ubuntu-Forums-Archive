---
title: "Question Install  14.04.3 LTS using Something Else"
date: 2015-11-27
forum: Installation &amp; Upgrades
---

### Post by just_me76570 on 2015-11-27
Hi, I'm going to Install Ubuntu 14.04 LTS, using the Option for Installation is **"Something Else" **I installed Ubuntu 12.04 using the option **"Install Along side Windows/8" **Now i wanna try to install the Ubuntu 14.04 and Remove the Ubuntu 12.04 if I'm going to Installed the the Ubuntu 14.04 using something else, do you think by removing **/dev/sda7 **(refer to picture) is also remove the home, / , and swap? (I'm dual booting with Windows 8 and Ubuntu 12.04)

[IMG]https://z-1-scontent-sea1-1.xx.fbcdn.net/hphotos-xtl1/v/t1.0-9/12274498_553759044780815_4801442586826249154_n.jpg?oh=bc3bb5f9cadad2041d0cde0e05efd08f&oe=56AC9297[/IMG]


Added: Another Question: I Boot Ubuntu in Live DVD but when i try to Install, I got some problem, 

```

[COLOR=#333333][FONT=monospace]The installer has detected that the following disks have mounted partitions:[/FONT][/COLOR][COLOR=#333333][FONT=monospace]/dev/sda[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Do you want the installer to try to unmount the partitions on these disks before continuing? If you leave them mounted, you will not be able to create, delete, or resize partitions on these disks, but you may be able to install to existing partitions there.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace](buttons at the end are "No" and "Yes")[/FONT][/COLOR]
```

It's safe to press **'Yes' **to remove the current Ubuntu 12.04 (in **/dev/sda7**) and Install Ubuntu 14.04 (in **/dev/sda7**)?

---

### Post by coldraven on 2015-11-27
> do you think by removing **/dev/sda7 **(refer to picture) is also remove the home, / , and swap
Ideally you should not have to remove anything. For /dev/sda7 you should be just be able to select "Use as /" and check "Format this partition". Same for swap usually I just leave it in place and select "Use as swap" (or something similar to that) Having said I'm concerned that I cannot see the /home or swap partitions that you mentioned.
Make sure that you have backed up all your Windows data!
I would wait a while for some more advice before starting.

---

### Post by just_me76570 on 2015-11-27
> **coldraven said:**
> Ideally you should not have to remove anything. For /dev/sda7 you should be just be able to select "Use as /" and check "Format this partition". Same for swap usually I just leave it in place and select "Use as swap" (or something similar to that) Having said I'm concerned that I cannot see the /home or swap partitions that you mentioned.
Make sure that you have backed up all your Windows data!
I would wait a while for some more advice before starting.


But If i click this sign "[SIZE=4] **-** [/SIZE]" in installation to remove the /dev/sda7 do you think this will also remove the home and swap? I think the /home and /swap is inside the /dev/sda7 (not sure) because I'm not the one who created the /home partition or /swap when I chose "Install alongside Windows" the Ubuntu Installation create that. waaaaa

---

### Post by Bucky Ball on 2015-11-27
Try this:

[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352)

Full instructions with pictures.

/home is probably in sda7. It would be impossible for /swap to be (unless you have manually jumped through some hoops and intentionally put it there yourself).

You could safely get rid of sda3, sda7 and sda8 and install to sda7, yes, if you no longer want 12.04 LTS. Add a 2Gb /swap somewhere (end of drive is usual).

---

### Post by yancek on 2015-11-27
There is no sign of a separate /home or swap partition so everything is on sda7.  If you have data on the current system you will need to back it up to a separate drive and then as suggested above, install to sda7.  Installing to sda7 will overwrite anything currently on that partition.  You could also after backing up resize(shrink) the partition which is currrently / (root) and then create a separate /home partition from the new unallocated space.

The message you posted about unmounting partitions is just informational.  If you want to create a new /home partition, you would be better off running GParted from the installation medium and doing it before the install.

You have windows 8 and GPT/UEFI so make sure you select to boot/install Xubuntu UEFI.

---

### Post by grahammechanical on 2015-11-27
Microsoft Windows 8 and later gets a fast boot by not fully shutting down and instead going into hibernation. If Windows 8 is indeed in hibernation then, I think that, the Ubuntu partitioner will show all Windows related partitions as mounted or locked. This is indicated by the key icon against those partitions. It even includes the one Linux partition that is Ext4 (sda7). And I wonder why.

If we do not have a separate /home partition then installing Ubuntu in the / partition using the Something Else option will over-write the /home folder that is in the / partition.

Regards.

---

### Post by just_me76570 on 2015-11-29
Thanks for helpful replay, I will update this thread soon after I successfully Installed the Ubuntu 14.04 LTS :) wish me luck :D

---

