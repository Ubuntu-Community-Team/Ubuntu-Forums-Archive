---
title: "Installing Ubuntu onto a harddrive with windows XP already installed"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by drahgo on 2006-08-25
[FONT="Arial"]Hello

I am slightly confuse at the part where the setup ask you to select the options to install Ubuntu onto a partion. 

My current operating system is Windows XP home edition and the hard drive is 250 gb and there is 55.83gb free space remaining. I don't want to install over windows and there is only one partion which is Windows is installed into.

What should I do? [/FONT]

---

### Post by az on 2006-08-25
The installer should offer you the option of resizing the current partition to make room for ubuntu.  Al lyou will have to do is tell it what size you want to make the original partition.

If you want your Ubuntu install to have 20 Gigs, tell it to resize the partition to 230 Gigs.

That's it.  It will then use the free space for the root and swap partitions.

---

### Post by Alvant on 2006-08-25
I had a similar experience when I installed Ubuntu a while ago. This is what I did:
1. I booted my Windows XP, got myself a HD partition tool. In my case it was "Partition Magic".
2. I created New partitions out of the free space on my computer.
3. I installed Ubuntu.

On my ~37GB HD I did it like this:
- 9GB Windows NTFS
- 24GB FAT (This is for all my movies and other stuff)
- The rest was left for the Ubuntu OS.


The thing is, besides creating a partition for the ubuntu OS, you might want to create a seperate partition for all your files that you may want to access (read and write to) when using either of your OS's.  In my case its the 24GB FAT partition. The why to this is simply because there are some issues with handling windows NTFS, although it is possible with some work. Search the forums for NTFS for more on this.
The other reason is that I like to keep every OS on its own partition, You know, incase I need to wipe it.

---

### Post by Herman on 2006-08-25
I wouldn't recommend Partition Magic for working with Linux partitions. It has problems handling partition numbers correctly for one thing.
 [PartitionMagic Error #114]("https://help.ubuntu.com/community/PartitionMagic_Error_%23114?highlight=%28CategoryDocumentation%29")

If you prefer using a stand-alone partitioner for working in a machine that is to have any Linux distro installed in it, any 'Parted based partitioning program would be much more suitable. QTParted or GParted are good examples. QTParted is found on many Live CDs such as 'System RescueCD and Knoppix.
GParted is available as a LiveCD on its own, it is only a small download and is very good.[GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")  I recommend that one.
GParted even has it's own web forums, [http://gparted-forum.surf4.info]("http://gparted-forum.surf4.info/") so you can get help with it if you need to. 
I can not find any public web forums for Partition Magic.

There is no reason not to use the Ubuntu installer's partitioning software.  The Ubuntu installer has no issues with NTFS that I am aware of.  I monitor these forums every day and have been doing so for quite a long time. I am certian we would all know about it if it did.
Regards, Herman :D

---

### Post by randell6564 on 2006-08-25
> **drahgo said:**
> [FONT="Arial"]Hello

I am slightly confuse at the part where the setup ask you to select the options to install Ubuntu onto a partion. 

My current operating system is Windows XP home edition and the hard drive is 250 gb and there is 55.83gb free space remaining. I don't want to install over windows and there is only one partion which is Windows is installed into.

What should I do? [/FONT]

Go into your XP disk manager and format that free space to Fat32. Then reboot using ubuntu cd.  She should then recognize it!  Install to that partition.

CHEERS!

---

### Post by adds2one on 2006-08-25
Check out these fool proof instructions. 

[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)

---

### Post by randell6564 on 2006-08-25
> **adds2one said:**
> Check out these fool proof instructions. 

[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/)

You GO BOY! or.,uh,girl.'Burp'

---

