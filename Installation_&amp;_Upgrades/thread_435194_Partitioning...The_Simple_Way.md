---
title: "Partitioning...The Simple Way?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by teejay17 on 2007-05-06
I have a question regarding partitioning. I have a fairly large hard drive, 380 Gig, and I would like to set aside about 100 Gigs for Ubuntu/Kubuntu so I can have a dual-boot machine. 
I'm not that technically savvy, but I have done some preliminary research.  

From what I understand, with the most basic dual-boot install, Ubuntu will take up all the remaining non-Windows space for itself. I don't want that much space for Ubuntu.
Actually, I wouldn't mind having my hard drive partitioned half-and-half.
Does anyone have any suggestions as to the best way for me go about this? I'm stuck right now as to what method to use for installing Kubuntu 7.04, and I'm looking at the 3 separate options, one of which I won't be using (Guided - use entire disk).

I'm undecided between the first option and inserting a "new partition size" and changing the partition to 50% (In this area, what is changed to 50%? Windows, or Kubuntu?)
Or do I do the manual install? The manual install seems pretty daunting and complicated.

All I want is 50% hard drive space for Windows, and 50% for Kubuntu.

Thanks in advance,
Tee Jay

---

### Post by K.Mandla on 2007-05-06
If you want 50-50, it's fairly easy. Set up windows with half of the space (or whatever proportion you want to give it), then tell Ubuntu to use the remaining space. Make sure you leave the non-Windows area unpartitioned and it will do the rest.

Does that help?

---

### Post by teejay17 on 2007-05-07
> **K.Mandla said:**
> If you want 50-50, it's fairly easy. Set up windows with half of the space (or whatever proportion you want to give it), then tell Ubuntu to use the remaining space. Make sure you leave the non-Windows area unpartitioned and it will do the rest.

Does that help?
Yes, that sort of helps. The only thing I need to know now is that how does this all go if I already have Windows on the machine, and I don't want to reinstall it? 
What I want to do is take Windows, as it is on the hard drive now, turn that into a 50% partition for Windows, and use the rest of the hard drive space for Kubuntu.

---

### Post by teejay17 on 2007-05-07
bump

---

### Post by teejay17 on 2007-05-12
> **teejay17 said:**
> Yes, that sort of helps. The only thing I need to know now is that how does this all go if I already have Windows on the machine, and I don't want to reinstall it? 
What I want to do is take Windows, as it is on the hard drive now, turn that into a 50% partition for Windows, and use the rest of the hard drive space for Kubuntu.
To simplify my question a little: what would be the easiest and safest way to put Kubuntu on my main desktop machine without ruining what's already on the hard drive, and also leaving enough room for future downloads--for Windows and for Kubuntu?

---

### Post by bulldog on 2007-05-12
The gparted live cd is an easy way of doing the job.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it to a disk and boot from it.
You have a graphical interface which is easier to understand.

You can resize your windows to 50% or 60% that's your choice to make.
You can leave the free space unpartitioned and let the installer do it for you,or you can create manual partitions for your needs.
If you do it manually create a 10GB /  [root] partition and format it ext3
Create a 1GB swap file and format as swap.
The rest of the space you can make a /home or divide it in more than one partition to have a /data partition.
These all should be formatted as ext3 file system.

---

### Post by teejay17 on 2007-05-12
> **bulldog said:**
> The gparted live cd is an easy way of doing the job.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it to a disk and boot from it.
You have a graphical interface which is easier to understand.

You can resize your windows to 50% or 60% that's your choice to make.
You can leave the free space unpartitioned and let the installer do it for you,or you can create manual partitions for your needs.
If you do it manually create a 10GB /  [root] partition and format it ext3
Create a 1GB swap file and format as swap.
The rest of the space you can make a /home or divide it in more than one partition to have a /data partition.
These all should be formatted as ext3 file system.
Okay, thanks. I'll give that a try and let you know how it goes. Hopefully all goes well.

---

### Post by teejay17 on 2007-05-14
There must be someone out there who knows the answer to my dilemma...

---

### Post by cstronach on 2007-05-17
I'm no expert, but some noob help is hopefully better than nothing.

As a minimum K/ubuntu needs two partitions, the root/main partition and a swap partition. IMHO, the simplest thing four you to do would be to use gparted (by running Ubuntu from the CD) to resize your windows partition to about 280G (back everything on it up first!), then in the newly created unpartitioned space create a large ext3 partition that take up all but 1-2G of space of the free space. Lastly, in that remaining 1-2G which you left alone, put a linux swap partition. 

In gparted you can play around with the configuration first before you apply the changes. If you've backed everything up you shouldn't be too scared of playing around, but I think the chances that you'll frag the Windows partition are really low (if you're sober and being sensible). I also think it might help to do a defrag in Windows before you start with anything else.

If you're feeling a bit more comfortable with all of this, you could add one more partition. With this setup you could would reduce windows to, say, 20G, give Ubuntu another 20G and a 1G Swap, and make all the rest of the HDD a FAT32 partition, which is where you store all your own files (you could even move your My Documents directory in windows over to that partition, which is very easy to do) in a shared area that is easily (automatically) accessible by both windows and Ubuntu. 

Read this for more detail: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[EDIT] Once you've set up you partitions you should still be able to boot to windows as per normal, but you C: drive will have gotten smaller. Reboot again to the Ubuntu CD and install. When the option comes up choose to manually edit the partitions, then select the ext3 partition as '/' root and the swap partition for the swap (I think it'll default to these automatically for you). Then go ahead and install. Once it's installed, when you reboot you will automatically get a menu that let you choose between booting Ubuntu or windows (you can easily edit this menu from Ubuntu later, if you want to change the default or whatever).

Hope I've helped and not confused.

---

### Post by bulldog on 2007-05-17
> **teejay17 said:**
> There must be someone out there who knows the answer to my dilemma...

I'm not sure if I understand your dilemma...............can you fill me in?

---

### Post by teejay17 on 2007-05-17
> **bulldog said:**
> I'm not sure if I understand your dilemma...............can you fill me in?
Sorry...
Anyway...I have a copy of Knoppix and I think it has Gparted included. Is this all right to use, or should I download an independent copy of Gparted?
Then, once I've got Gparted in the machine and ready to partition...Can I resize Windows to, say, 150 gigs without losing data? Then let's say I want to create a partition for about 150 gigs. Let's say I call this "ubuntu partition." When it comes time to install Ubuntu...will it recognize this "ubuntu partition"?
Now I still need a swap...in Gparted, let's say I devote about a gig to swap...and I call it "swap." How do I make Ubuntu recognize that this should be used for swap?

---

### Post by bulldog on 2007-05-17
Your making it to hard for your self :)

You can use any gparted program your familiar with.
Before resizing windows be sure it's thoroughly defragmented.
Than use gparted to resize windows as you want,let the free space unallocated.
Boot ubuntu and when you come to the partition section,use the free space option.
Ubuntu will create your / partition and a swap file too.
That's all to it.

Just don't make your windows too small!!

---

### Post by teejay17 on 2007-05-18
> **bulldog said:**
> Your making it to hard for your self :)

You can use any gparted program your familiar with.
Before resizing windows be sure it's thoroughly defragmented.
Than use gparted to resize windows as you want,let the free space unallocated.
Boot ubuntu and when you come to the partition section,use the free space option.
Ubuntu will create your / partition and a swap file too.
That's all to it.

Just don't make your windows too small!!
You know what, that does sound easy! I'm going to build up my confidence, back up my data, and just delve into it over this long weekend.

---

### Post by teejay17 on 2007-05-24
For everyone whose helped me on this thread, I want to thank you very much. Your lengthy explanations have been a great help. 
I haven't done the partitioning yet because I went camping last weekend, and I've spent the rest of this week studying and going over all of your feedback in this thread. In the process, my confidence is going up, and I'm getting the nerve to do this...
This forum is great.

---

### Post by teejay17 on 2007-05-26
Okay, so I got my hands on Partition Magic 8. I think it should be pretty straight forward to partition the drive 50/50. The only thing is, how do I make sure I get the screen (I think it's called a grub screen) at the beginning, the one that gives me the choice to boot into Ubuntu or Windows? Does this happen automatically, or is it something I should do? 
For example, if I call my new partition "Ubuntu" and the older one is NTFS, will things automatically do as they should?

---

### Post by teejay17 on 2007-05-26
bump

---

### Post by merlinus on 2007-05-26
When you install Ubuntu, it will set up grub for dual booting.

Just be sure, at the partitioning screen, that you tell it to use the one you set aside, not your windows one.

Good luck!

-merlin

---

### Post by teejay17 on 2007-05-28
> **merlinus said:**
> When you install Ubuntu, it will set up grub for dual booting.

Just be sure, at the partitioning screen, that you tell it to use the one you set aside, not your windows one.

Good luck!

-merlin
Okay, thanks.

---

### Post by teejay17 on 2007-05-29
Hooray, I did it last night! The whole process went without a hitch, and quickly I might add. I have a successful dual-boot machine with Kubuntu and Windows almost evenly split down the middle. 
The whole process was seriously way simpler than I expected--I didn't even *have *to partition anything. Kubuntu was able to partition the drive all by itself, almost directly half and half. Grub and everything at boot-up also works fine. 
I love my new system: now my spouse can have her Windows, and I can work happily away in Kubuntu!
[I](I have a feeling that my wife will come to be more familiar with Kubuntu, the more she sees it and interacts with it). 
[/I]Cheers!

---

