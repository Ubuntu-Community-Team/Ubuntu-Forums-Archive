---
title: "Not getting dual boot install option"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by dudeyes on 2007-05-20
I've tried installing 7.04 , the first time creating a cd using bit torrent, then the other time just downloading the .iso from Ubuntu, checking that the downloaded files weren't corrupted by using the MD5Sum hash comparisons, then rebooting with the disk I just created. I'm able to use the livecd tu try out Ubuntu, and everything works fine, but when I try ti install it, the problems begin. I get past the first few menus without a problem , but when it gets to the partitioning screen, I'm only given 2 options - either have my entire hard drive taken over by Linux, or the manual install method. I'm not even given the option of creating a dual boot that is mentioned in all the installation walk throughs and FAQ's I've seen. Does anyone now of a good source for using the manual install method? I'd like to create a small Ext3 partition for Ubuntu and a small swap file - I have a 20 gb FAT32 drive and a 57 gb NTFS drive that I'd like to partition for Ubuntu. 
My machine uses an Athlon 1.8 gHz processor, has 528 Mb RAM and is about 3 years old. 
TIA

---

### Post by tgoose on 2007-05-20
It would be better if there an option in the installer for some kind of "automatic" dual boot setup, but I think at the minute it's quite difficult to design an automatic "one size fits all" solution (unless there is one somewhere, and I haven't noticed it!)

As for a guide, those on [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) seem pretty sensible, although they may need some adapting for your two hard drives. It also refers to the command line installation, but if I remember correctly the live one has all the same dialogue boxes.

If you are likely to be using Ubuntu on this computer in the long term, I would definitely recommend adding a separate /home partition (this is mentioned in the third of the guides) because it really can make upgrading or reinstalling a lot simpler: spending a little time reading these guides thoroughly and really understanding the importance of / and /home can save a lot of headaches later on: just because it's Linux doesn't mean things **can't** go wrong, and if they do being able to completely wipe your system partition without losing any personal data is a very useful tool to have.

---

