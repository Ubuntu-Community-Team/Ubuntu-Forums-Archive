---
title: "Moving from 12.04LTS to 13.04"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by jonburton on 2013-05-19
Hi,

I was thinking of updating my 64bit 12.04LTS installation to 13.04, please could someone let me know how to do this - All the links I have seen online seem to suggest I need to move to 12.10 first?

Thanks in advance :)

---

### Post by fantab on 2013-05-19
Yes, that is true. You have to upgrade to 12.10 and then to 13.04.
Why don't you consider installing 13.04 on a separate partition? All you need is 20-30GB partition. Most of us here do that. We keep LTS 12.04 on one partition and install other versions on another partition.

---

### Post by jonburton on 2013-05-19
Thanks never thought of that, I suppose the only issue is I used up all my HDD when I first installed 12.04 and my home directory is there also - Beginners mistake!

---

### Post by ajgreeny on 2013-05-19
It may still be possible so let's see your current partition layout with the output from command ```
sudo fdisk -l
``` or if that tells you you have GPT partitions ```
sudo parted -l
```

---

### Post by kurt18947 on 2013-05-19
I have and would recommend maintaining an LTS install if you're at all concerned about stability.  I haven't done a separate /home partition lately but a Linux install should fit in 25 GB. with space for data.  Remember the support period for non-LTS releases is 9 months, I believe.  I use 13.04 primarily but periodically log into 12.04 to make sure it is in good working order.  I believe non-LTS releases are used to test and debug technologies for the next LTS so I don't count on them being stable.

---

### Post by jonburton on 2013-05-19
Sorry for more newbie questions but if I do a fresh install of 13.04 in a new partition I will have to reinstall all my apps wont I, for example, Steam, Chrome etc and thus have 2 copies of everything.

Is there a best practice at all? Thank you :)

---

### Post by ibjsb4 on 2013-05-19
You can create a backup list (markings list) of your installed app's with [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9").  And then use that list to [reinstall your packages]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager+markings+list&sa=Search&cof=FORID:9").

```
sudo apt-get install synaptic
```

---

### Post by sudodus on 2013-05-19
> **kurt18947 said:**
> I have and would recommend maintaining an LTS install if you're at all concerned about stability.  I haven't done a separate /home partition lately but a Linux install should fit in 25 GB. with space for data.  Remember the support period for non-LTS releases is 9 months, I believe.  I use 13.04 primarily but periodically log into 12.04 to make sure it is in good working order.  I believe non-LTS releases are used to test and debug technologies for the next LTS so I don't count on them being stable.
+1 (almost)


> **jonburton said:**
> Sorry for more newbie questions but if I do a fresh install of 13.04 in a new partition [COLOR=#ff0000]I will have to reinstall all my apps wont I[/COLOR], for example, Steam, Chrome etc and thus have 2 copies of everything.

Is there a best practice at all? Thank you :)

Yes, but it is a good idea to have the LTS version (12.04) as the production platform alias workhorse, and play with new features in the new version (13.04 right now).

---

### Post by fantab on 2013-05-19
That is correct. You will be installing a new ubuntu after all. However the packages in 13.04 will be latest compared to 12.04, especially Linux Kernel. And to try different things you use for instance Chromium instead of Chrome... 

Do you have a separate /home partition?

---

### Post by jonburton on 2013-05-19
I dont have a seperate home partition just a Windows 8 partition (pre installed on the laptop) and also a Ubuntu partition. Im wondering now if it would be best to wipe the disk, start again and use 12.04LTS as my base OS then run everything else as a VM within 12.04 - What do you think?

---

### Post by jamesisin on 2013-05-19
Is your laptop touch?  I don't know how well touch will transfer from host to VM.  Excluding that Win8 makes a fine VM (it's lighter than Win7) if you need Windows at all.

I have 12.04 on only one machine now.  The others I have upgraded through 12.10 to 13.04 without any troubles.  I find 13.04 is stable enough for my daily usage.

---

### Post by sudodus on 2013-05-19
> **jonburton said:**
> I dont have a seperate home partition just a Windows 8 partition (pre installed on the laptop) and also a Ubuntu partition. Im wondering now if it would be best to wipe the disk, start again and use 12.04LTS as my base OS then run everything else as a VM within 12.04 - What do you think?

A VM is something you can run without editing partitions. So it is fairly simple. But you will not see the full potential of the new version, unless you run it from its own partition.

- How much free space is there on your HDD?

If you mount your partitions, run the command

```
df
```

and post the result, we can give advice how to test the new version of Ubuntu.

- Do you have a good backup on another HDD (an external drive or in another computer)? If you plan to edit the partitions, you need a good backup.

---

### Post by jonburton on 2013-05-19
Thanks everyone, laptop is not a touch laptop its just an i5, 8gig Ram, intel video and 320gb hdd. I only use Windows for Word, Excel, Powerpoint and OneNote (which I cannot really do without due to work) I only ever boot Windows when I need these apps and use Ubuntu 12.04 and Chrome for everything else.

Results from df

Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda6      144649880 25289580 112012436  19% /
udev             4018368        4   4018364   1% /dev
tmpfs            1610872      948   1609924   1% /run
none                5120        0      5120   0% /run/lock
none             4027180     2944   4024236   1% /run/shm
/dev/sda2      156989660 46289836 110699824  30% /media/B6D8176DD8172ADF
/dev/sda1         358396   242996    115400  68% /media/System Reserved

---

### Post by sudodus on 2013-05-19
> **jonburton said:**
> Thanks everyone, laptop is not a touch laptop its just an i5, 8gig Ram, intel video and 320gb hdd. I only use Windows for Word, Excel, Powerpoint and OneNote (which I cannot really do without due to work) I only ever boot Windows when I need these apps and use Ubuntu 12.04 and Chrome for everything else.

Results from df

```

Filesystem 1K-blocks    Used Available Use% Mounted on
/dev/sda6 144649880 25289580 [COLOR=#ff0000]112[/COLOR]012436  19% /
udev        4018368        4   4018364   1% /dev
tmpfs       1610872      948   1609924   1% /run
none           5120        0      5120   0% /run/lock
none        4027180     2944   4024236   1% /run/shm
/dev/sda2 156989660 46289836 110699824  30% /media/B6D8176DD8172ADF
/dev/sda1    358396   242996    115400  68% /media/System Reserved

```


There are [COLOR=#ff0000]112[/COLOR] GB available in the system partition /dev/sda6. This is plenty, and it would work well, if you shrink it to allow for another 20 GB partition, that can be used for the new version 13.04. Shrinking a partition can be done with ***gparted***, but it is very slow (takes hours). So if your installed system is brand new and you have not tweaked it or put a lot of own data into it, you might as well reinstall the 12.04.2 LTS as well.

In that case you can consider remaking the partition table even more: Use those 112 GB in the following way

a. 32 GB for 12.04.2 LTS (an ext4 partition with the label ***precise***)
b. 20 GB for 13.04 (and later on reused for 13.10, with the label ***test-os***)
c. 60 GB for data (an ext4 partition with the label ***linuxdata***)

And there are still the ntfs partitions, which can be read and written by Ubuntu and Windows. But avoid writing from Ubuntu to the Windows system partition. Use the other big partition, that you might give the label ***windata***, to store and exchange data. (/dev/sda1 is reserved for other purposes).

---

### Post by jonburton on 2013-05-19
Thanks Ill give it a go and see how I do :)

---

### Post by jamesisin on 2013-05-19
I have a very different experience of GParted than does Sudodus.  I find that it works quite well for moving and resizing partitions and doesn't seem any slower than anything else.  One very important thing to note about resizing or moving a partition is that if you move the left edge (or beginning) of the partition it will break your boot.  This is fixable and therefore acceptable, but you should be prepared to deal with it in time.  If you are only talking about moving the right-edge (or end) of a partition this should not be a concern; and moving the right-edge over empty space should go very rapidly.

Another important thing to note is that the Windows MBR (Master Boot Record) will only recognize four primary partitions.  You must use extended partitions for some of your several partitions or you will run into real troubles.

Finally, each time you make a partition change (add, remove, move, or whatever) you will want to open a terminal and run *sudo update-grub* so that grub can re-index the boot information for your system.

I thought I'd written an article on moving partitions but I can't find it.  You might find this information useful:

[http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/](http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/)

---

### Post by sudodus on 2013-05-19
> **jamesisin said:**
> I have a very different experience of GParted than does Sudodus.  I find that it works quite well for moving and resizing partitions and doesn't seem any slower than anything else.  One very important thing to note about resizing or moving a partition is that if you move the left edge (or beginning) of the partition it will break your boot.  This is fixable and therefore acceptable, but you should be prepared to deal with it in time.  If you are only talking about moving the right-edge (or end) of a partition this should not be a concern; and moving the right-edge over empty space should go very rapidly.

Another important thing to note is that the Windows MBR (Master Boot Record) will only recognize four primary partitions.  You must use extended partitions for some of your several partitions or you will run into real troubles.

Finally, each time you make a partition change (add, remove, move, or whatever) you will want to open a terminal and run *sudo update-grub* so that grub can re-index the boot information for your system.

I thought I'd written an article on moving partitions but I can't find it.  You might find this information useful:

[http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/](http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/)

This is important information. I was not accurate enough, when I gave the advice. I agree with *jamesisin* (except that I think that shrinking might last for a long time, but let it be a positive surprise, if it is faster than I expected).

Normally the block device **[FONT=courier new]/dev/sda6[/FONT]** indicates, that Ubuntu's root file system is in a logical partition inside an extended partition, but it needs to be checked with ***gparted*** (GUI) or ***fdisk*** or ***parted***.

```
sudo fdisk -lu
```
```
sudo parted -l
```

Please post the output from these commands :-)

If /dev/sda6 is a logical partition we need not worry about the number of partitions, and you can follow the instructions in my previous post.

Otherwise, you need to check how many partitions there are already. We know of

/dev/sda1
/dev/sda2
/dev/sda6

from the output of ***df***. But you probably have a swap partition too. I think (and hope) it is the logical partition /dev/sda5.

Now, we need to check if you have an extended partition already, how it is located, and decide how to continue depending on the new information :-)

---

