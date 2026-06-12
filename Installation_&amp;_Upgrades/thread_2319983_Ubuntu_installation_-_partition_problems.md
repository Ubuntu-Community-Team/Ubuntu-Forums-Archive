---
title: "Ubuntu installation - partition problems"
date: 2016-04-09
forum: Installation &amp; Upgrades
---

### Post by Chocookie on 2016-04-09
Hi,

I'm trying to install Ubuntu alongside Windows 7 on an HP and I've run into some problems with the partition. I've used the standard Windows tool to shrink the C: disk ~100GB and left this space as unallocated. The Ubuntu installation however won't let me install on this (there's no "install alongside windows" option - I've read I shouldn't use that anyway? - and the unallocated space in the "something else" option is listed as unusable). So I've read up on MBR and have changed one of my 4 partitions (tools) from primary to logical/extended.

Now the whole disk is split into:
- system for windows, 200 MB, primary
- windows disk space, 800 GB, primary
- unallocated space, 100 GB
- recovery for windows, 18 GB, primary
- extended containing hp tools as logical, 100 MB
- unallocated space, 1 MB

I thougt maybe moving the unallocated space into the extended partition would help, but I'm not sure and I don't know how to do it. Can anyone please help me? This has already taken days and is starting to be really frustrating ...

---

### Post by Bucky Ball on 2016-04-09
Welcome. Well, with the extended partition you have four partitions already. If you try to install to the unallocated space you would have five and in a regular BIOS install that is not possible. In other words, what you have there is not going to work. You must start out with three partitions, primary or extended doesn't matter, and create an extended partition for Ubuntu as that need two partitions: / and /swap at least. 

You have a problem. If you could have the extended partition where you have the unallocated space at the moment and have everything else inside that, including the 100Gb unallocated space for Ubuntu (Ubuntu doesn't care about being installed on a logical partition, doesn't need a primary like Windows), that would work. 

So, ideally, if you could wipe everything after 'unallocated space' and make all of that unallocated space into an extended partition, then put your other partitions back inside that, including the Ubuntu install you'd be sweet.

---

### Post by Impavidus on 2016-04-09
> **Chocookie said:**
> 
I thougt maybe moving the unallocated space into the extended partition would help, but I'm not sure and I don't know how to do it. Can anyone please help me? This has already taken days and is starting to be really frustrating ...

Yes, that would help. The installer can create new logical partitions and Ubuntu can be installed on those, but there must be unallocated space in the extended partition. The installer is smart enough to move unalocated space into the extended partition if it's already adjacent, but in your case the recovery partition is inbetween. You have to switch the hp tools partitions and the recovery partition around somehow, or simply remove the hp tools partition if you're not going to use it (you can keep a backup somewhere).

It may be possible to use the Ubuntu live system to make a backup (clone) of that little hp tools partition, remove it and the extended partition, create a new extended partition in the 100GB unallocated space, clone that hp tools partition back into it and you'll have enough unallocated space in the extended partition to install Ubuntu. And you'll have 101MB of unusable space at the end of the disk, but that won't matter. I've never done such things myself though.

I'd be careful with the Windows recovery partition.

---

### Post by grahammechanical on 2016-04-09
You need to shift the 18 GB recovery partition so that the unallocated space is in front of the Extended partition. Then expand the Extended partition to include the unallocated space. Then using Gparted running from a Ubuntu live session create 2 Logical partitions out of the unallocated space inside the Extended partition. A large Logical partition for Ubuntu & a smaller Logical partition for swap.

Then you use the Something Else option. The partition for Ubuntu has a mount point of / and a format of Ext4. The partition for swap has a mount point of swap.

Regards.

---

### Post by Chocookie on 2016-04-09
> **grahammechanical said:**
> You need to shift the 18 GB recovery partition so that the unallocated space is in front of the Extended partition. 

Could you maybe explain to me how that part works? Is there some tool for it (windows or linux)?
And as for the two partitions for linux: I have to make them myself before the installation? Because I was following a tutorial and it didn't have a word of that in it, it just said to start the installation and that would work ...

Thanks for the help so far!

---

### Post by oldfred on 2016-04-09
You can create partitions in advance, but only require if you want more than the standard / (root) & swap. Installer will create those automatically.
Many want shared NTFSs, /home or other data partitions and then have to manually create those partitions.
Use Windows only for shrinking the NTFS partition and always reboot so it can run chkdsk and repair to its new size.
And use gparted to create new partitions. You can also use it to move partitions. It is on live installer, but will not be in your install as you cannot use it on mounted partitions.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 
    
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by Chocookie on 2016-04-09
Thank you all very much, it worked perfectly with gparted after all :)

---

### Post by grahammechanical on 2016-04-09
I am glad you found a way to success. Keep in mind. Windows tools for Windows partitions and Linux tools (Gparted in a live session) for Linux partitions. I have seen advice that says before resizing a Windows partition we should defrag the partition using a Windows tool.

Regards.

---

