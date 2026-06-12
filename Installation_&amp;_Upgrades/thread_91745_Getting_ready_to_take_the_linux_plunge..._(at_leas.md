---
title: "Getting ready to take the linux plunge... (at least partway)"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by cgrucelski on 2005-11-17
Hi all.

Over the past year or so, I've sampled a number of different flavors of linux... (usually in LiveCD format) and now I believe I've found a keeper in Ubuntu! I love what I've seen and experienced with the Ubuntu LiveCD and am looking forward to learning linux in the process of giving it a permanant home on my harddrive. 

However, I still have several games (i.e. CS:Source) and applications (i.e. Macromedia studio) for which I still want and need to keep my XP Pro, so I'm wondering what's the best way for me to install Ubuntu without causing me too much grief. 

My primary drive is a 40 GB drive and my secondary is a 20 GB drive. I have read through some of the help files, forum posts, and user guides and think I have a basic understanding of the install. If I understand correctly, the Ubuntu installation CD will step me through the process and allow me to repartition a portion of my 40 GB primary drive to allow for the linux-specific partitions without compromising my existing Windows installation. Then, I also will need to reformat my secondary drive (currently NTFS) so that I can use it as a common location for both operating systems to share for file storage, etc. 

Are there any good step-by-step install guides available that anyone can recommend? Also, can anyone offer any pointers or things for me to watch out for? For example, I am slightly unsure about the whole grub/boot loader issue... while I will be using Ubuntu as my primary system, I don't want to have problems getting back into Windows when necessary.

Thanks in advance!

---

### Post by SuperMike on 2005-11-17
[QUOTE=cgrucelski]
However, I still have several games (i.e. CS:Source) and applications (i.e. Macromedia studio) for which I still want and need to keep my XP Pro, so I'm wondering what's the best way for me to install Ubuntu without causing me too much grief. 
[/QUOTE]

Ah, custom partitioning. Sounds like you're a little new to Ubuntu. If you have the 5.04 CDs, not the new 5.10 CDs, I have experience with custom partitioning. I tried this and create a partition for /boot, another for / (root), and another for /home. That way, my reasoning was that I could upgrade safer and not effect my /home partition. I found, however, that when I did custom partitioning, it didn't prompt me to install /swap. I found to my horror after this that I had no swap partition and I had to create a swapfile, which many people say is not as efficient as a swap partition.

In your case, with two physical hard drives, you sound like you want to put / (root) (along with every other Ubuntu subdir underneath it) on 40% of drive 1 (which I recommend be the 40MB because Windows XP is a disk hawg), and the other 60% can be Windows XP. Then, on drive 2, you can create one big FAT32 volume for shared data, although on bootup you'll get "btw, this is beta" warnings that I would usually ignore because it does indeed work. As for grub -- you want that. You first put XP on 50% of drive 1 and then go back and put Ubuntu on the other 50%. When you reboot, you'll be prompted on whether you want to boot XP or boot Ubuntu.

HOWEVER, saying all this, I can tell you that you can save yourself the hassle by just putting XP on a separate system, turn on Remote Desktop with it, put Ubuntu on your favorite system, and then use rdesktop/tsclient from Ubuntu to reach your XP system. I take you understand networking a little so that you can network the two systems? If not, ask a friend or post something here.

For me, I do the latter and I have less hassle. However, I have done the former and made it work too.

---

### Post by cgrucelski on 2005-11-18
*[QUOTE=SuperMike]Ah, custom partitioning. Sounds like you're a little new to Ubuntu. If you have the 5.04 CDs, not the new 5.10 CDs, I have experience with custom partitioning. [/QUOTE]*

Yup, new to Ubuntu installation on harddrive. I have installed other flavors, but never kept them... they were always just a novelty item. And yes, I have the latest 5.10 CDs... just got my free copies in the mail the other day (although I had already downloaded and burned a CD image). Needless to say, I was even impressed with the presentation/packaging of the CDs. Not to shabby for free!

*[QUOTE=SuperMike]In your case, with two physical hard drives, you sound like you want to put / (root) (along with every other Ubuntu subdir underneath it) on 40% of drive 1 (which I recommend be the 40MB because Windows XP is a disk hawg), and the other 60% can be Windows XP. Then, on drive 2, you can create one big FAT32 volume for shared data, although on bootup you'll get "btw, this is beta" warnings that I would usually ignore because it does indeed work. [/QUOTE]*

I am certainly not opposed to leaving the existing primary drive #1 (40 GB) as XP only and using the secondary drive #2 (20 GB) for Ubuntu. In this scenario, I could just partition part of the 40 GB drive for the shared location if I wanted to share files. However, drive #1 is currently formatted in NTFS, so I would need to use PartitionMagic or some other similar utility to repartition part of it to FAT32. If I am not mistaken, I believe one can repartition drives on the fly without affecting an existing operating system installation. Also, since I am not that familiar with Linux, Grub, etc., how does it work having two different operating systems on two different physical disks? Would the boot prompt still be able to find both operating systems?

*[QUOTE=SuperMike]As for grub -- you want that. You first put XP on 50% of drive 1 and then go back and put Ubuntu on the other 50%. When you reboot, you'll be prompted on whether you want to boot XP or boot Ubuntu.[/QUOTE]*

By this, do you mean that it is preferable that I reinstall XP? I guess I could do that... it's been about 8 months since I last reinstalled Windows. If this is the case, it kind of makes the above question irrelevant though. If it is necessary to do a fresh reinstall of XP, then I don't have to worry about repartitioning on the fly, etc.

*[QUOTE=SuperMike]HOWEVER, saying all this, I can tell you that you can save yourself the hassle by just putting XP on a separate system, turn on Remote Desktop with it, put Ubuntu on your favorite system, and then use rdesktop/tsclient from Ubuntu to reach your XP system. I take you understand networking a little so that you can network the two systems? If not, ask a friend or post something here. For me, I do the latter and I have less hassle. However, I have done the former and made it work too.[/QUOTE]*

I am not familiar with the rdesktop/tsclient within Ubuntu, but surely you don't mean this is compatible with Windows XP's Remote Desktop Connection, do you?  (pause, while I pick up my jaw from the floor at the thought of this...) Not only am I familiar with Windows RDC, I use it literally everyday since my office is connected to another company office about a mile down the road via RDC. I also connect to our servers from home via Windows RDC to do work in the evenings. This would be an interesting option if this is available... and it would give me an excuse to go my another PC  :)


Thanks in advance...

---

### Post by cgrucelski on 2005-11-18
The other option I have been reading about is using Wine to run Windows-based programs.... I gather that there are more and more programs that function within Wine. But, I also gather that there may be performance issues and game support is spotty at best.

---

### Post by yesplease on 2005-11-18
It is easy to run windows and ubuntu on 2 disks (I do it, like many others).

When you can use your 120GB disk for ubuntu, make a / (root) 5GB, swap 1GB and the rest for the /home partition, format in ext3. You can use the ubuntu 5.10  install disk to make the partitions.  Install does not take much time, and no matter how many problems you read here, usually it is very easy.

 You may have to edit grub, so you could read some howtos on that beforehand. Dont use Partition Magic, you dont need it, and it may cause problems.

Use windows for games, you can always try wine later.

Make the fat partition later, if you still think you need it.

---

