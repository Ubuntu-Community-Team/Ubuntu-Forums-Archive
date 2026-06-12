---
title: "I ought to be able to boot through grub after resizing with gparted, right?"
date: 2019-01-04
forum: Installation &amp; Upgrades
---

### Post by robertcull1 on 2019-01-04
I do not have enough space on my Windows (NTFS) partition to install some software that I want. I have backed up my Ubuntu partition. I want to increase the size of the Windows partition at the expense of the Ubuntu partition. I am not asking for anyone to take responsibility in case something goes wrong, I am just looking for reassurance.

I have done this kind of thing before and it worked albeit a long time since I did. The last time I did this kind of thing I was able to reboot through Grub after the resizing. My question is:

I ought to be able to shrink the Linux partition on its left side and then expand the Windows partition on its right side. Then I still ought to be able to boot into both partitions again through Grub, right? I mean, that's the way it's supposed to work isn't it? I just want to know if that is the way it is supposed to work. Remember I have everything backed up.

---

### Post by robertcull1 on 2019-01-04
I need to increase the size of my Windows partition at the expense of my Ubuntu partition.

[IMG]http://robertstestimony.com/Pictures/Gparted_1.png[/IMG]

As you can see my NTFS partition has an exclamation point (!) next to it. When I ask for information I get the following message:

[HTML] 
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs.[/HTML]

I tried to install the software, but it says it's already installed:

```
 
$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version (1:2017.3.23-2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$
```

I can't seem to resize the NTFS partition. I get a window that looks like this:

[IMG]http://robertstestimony.com/Pictures/Gparted_2.png[/IMG]

I can't drag the arrows or enter a size in the fields below.

What do I need to do in order to resize the NTFS partition? Any help would be greatly appreciated.

---

### Post by CatKiller on 2019-01-04
You can't make it any bigger until you've made somewhere to make it bigger into.

You'll need to shrink sda6 and sda4, and move their start points first.

It's best to resize Windows partitions with Windows. It's a bit fragile. You definitely can't do it when Windows is hibernated.

---

### Post by yancek on 2019-01-04
You neglected to inform us which windows operating system you are using.  This is significant information since windows has been selling licenses for their operating systems for over 30 years.
If you do happen to have the most recent windows 10, the most likely reason you are seeing the exclamation point in GParted is because windows 10 is hibernated.  That is the default and major update will turn it back on.  You won't be asked if you want this nor will you be informed that it is happening.  If you do not have windows 10, please indicate what you do have.

You have a Legacy install with Ubuntu and the swap partition on logical partitions within your Extended partition (sda4)  so you will first need to use GParted from a CD or from your Ubuntu installation media to resize.  You cannot use GParted to do this from the installed Ubuntu.  Turn swap off and then unmount sda5 (Ubuntu OS partition) and sda4 (Extended) then resize it by moving it to the right .  It might be simpler to delete the swap and re-create it later but move sda6 to the right.  YOu will then need to move sda4 (Extended partition) to the right.  This could take some time as you will not only be re-sizing the partition but moving data.

When that  finishes and if it is successful, I would suggest you re-size (increase) your windows partition from windows Disk Management tool.

---

### Post by yancek on 2019-01-04
Problem is you are moving the Grub boot files.  See your other post for some suggestions.

---

### Post by robertcull1 on 2019-01-04
The OS on the NFTS partition is Windows 7.

After I resize the Ubuntu partitions, will I be able to boot into the Windows OS?

---

### Post by oldos2er on 2019-01-04
Threads merged.

---

### Post by oldfred on 2019-01-04
Best to have a Windows repair/recovery flash drive and the Ubuntu live installer.
Then you can make repairs, if needed.
And you always want good backups, so if things go wrong, it is easier to reinstall & recover, rather than start all over.

Windows after a resize will want to run chkdsk. 
And grub only boots working Windows, so if chkdsk flash is on, grub will not boot it to prevent further damage. Then at least temporarily you may need a Windows boot loader to directly boot Windows, make repairs, and then restore grub. Relative easy if you have the repair tools.

---

