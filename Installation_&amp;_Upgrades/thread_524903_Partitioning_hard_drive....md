---
title: "Partitioning hard drive..."
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by tk338 on 2007-08-13
I have an uncle who is very good at computers, he works on a lot of programs for pcs, but at homes uses versions of linux, and macs aswell. However he is basically uncontactable, and I havn't spoken to him in a while, added to the fact he is often very busy. He suggested I try Ubuntu, and install as another OS on my current laptop. I would love to do this if only I knew how. My laptop already has two hard drives, they came like that so im not sure if they are 1 that is partitioned or two separate ones they show as two drives in my computer. Basically I have a version of Ubuntu that I would like to install, how can I do it, and yet still keep all of my windows xp the same. Can you get it so it asks what OS you would like it to boot when you boot the pc. I have asked on PC forums but they were extremely unhelpful but im sure some of you kind people could help me with this... Thanks PS Im not at all fluent with linux, and so would need a fairly broken down guide.

---

### Post by logos34 on 2007-08-13
try this guide:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

more on dual booting here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by omegamike3 on 2007-08-13
If you run the Ubuntu live cd (by booting off the cd containing Ubuntu) the install will walk you through the process very gently, offering to import some of your settings from windows into Ubuntu. As part of the install, you will be given a few options for partitioning.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
This walkthrough can probably help you the most initially, and just post any questions you come across later on. The most important thing to remember is that you should backup all your important data in windows before beginning the install, as that's a good idea whenever making drastic changes.
Welcome to Ubuntu!:)

---

### Post by tk338 on 2007-08-13
Thankou both very much, only problem is if I muck up ill be in big trouble.

---

### Post by tk338 on 2007-08-13
Is there any way I can find out if I have one or two hard drives, and wether it is just a partition?

---

### Post by omegamike3 on 2007-08-13
> **tk338 said:**
> Is there any way I can find out if I have one or two hard drives, and wether it is just a partition?

More than likely it is partitioned, especially since you're using a laptop and i'm assuming you have an optical drive of some kind. the simplest way would be to just google the model of laptop you're using and see what the configuration is. you could also open up the laptop, which i'm assuming you don't want to do. or check the naming or labeling of the second drive, most likely it's just a restore partition and is named something along those lines. if you browse the drive, there won't be much there other than a few weirdly-named folders and something that looks like they recycling bin.

---

### Post by tk338 on 2007-08-13
From what ive read it is just a partition so does this mean I can then usuin g a live cd just select that drive and install it to that drive?

---

### Post by omegamike3 on 2007-08-13
no, you'll want to install to another, third, partition which Ubuntu will create for you during the install process. this partition will not be visible to windows so things in windows will appear nearly identical to they way they are now, with the exception of there being less total hard drive space, since a chunk will be going to Ubuntu.

---

### Post by tk338 on 2007-08-13
Sorry if im annoying I just want to get it clear, that I get Ubuntu to partition the second hard drive that windows isnt using... and how much space for this partition.

---

### Post by omegamike3 on 2007-08-13
the installer is going to split the drive evenly by default, half for windows, half for Ubuntu. as long as this configuration leaves a reasonable amount of space to poke around, maybe install a few additional things, until you decide whether you like it or not, at least 6GB (of course more is always better) then you should be fine. later on down the road, should you decide that Ubuntu is the path for you, the partition size can be increased to suit your needs. and shove windows into a dark, cramped corner of your hard drive ;) :P

---

### Post by bwtranch on 2007-08-13
It will partition it for you. Using the disk space it believes to be appropriate. But, do do that backup as requested, to an external sorce like CD or something.. And make sure you have a windoze rescue cd if something goes wrong. Laptops can be tricky.

---

### Post by merlinus on 2007-08-13
PMFJI, but in the OP's original message, it says the laptop has two hard drives, not one, and that he wants to install ubuntu on the second one.

If this is correct, then the directions for doing so need to be altered some.

-merlin

---

### Post by bwtranch on 2007-08-13
But, he found out later that it was just one HDD, with just 2 partitions. Right?

---

### Post by tk338 on 2007-08-13
Sorry me... again just to put things straight, I have a single physical hard drive that is partitioned, they are roughly both 30 and 35 gb each. The 30 gb one contains windows and has about 300 mb free, the second, the 35 gb one is just about empty. Is it:
1. Possible to move this partition at all making more space for windows and a little less for the other partition for Ubuntu?
OR
2.Format the second partitioned hard drive, then When installing Ubuntu select the empty hard drive and then install it to that, letting Ubuntu creating its own partition?

---

### Post by merlinus on 2007-08-13
I would definitely add more space to your windows partition.  Otherwise you will run into problems with defragmenting, adding new apps, etc.

I recommend gparted live cd for partitioning work:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by bwtranch on 2007-08-13
I would let Ubuntu use the free space and create the third partition. I have never had a problem with that. But, I have seen many a problem with people trying to do it themselves and if you do it wrong, you have to start from scratch. This is not recoverable. Unless you have special software and gets everything back out bit by bit. That's why the backup is important. Ubuntu will tell you what it's going to do and give you the final say. You can always opt out if it doesn't look right.

---

### Post by bwtranch on 2007-08-13
Re: # 15 That's right. He doesn't have any space left on the windoze part.  but, if you're gonna go Linux, does it matter?

---

### Post by bwtranch on 2007-08-13
But, one more thing, won't windoze stll recognize part #2? and be able to use that? I don't know but it seems like it will. I can access my windoze files from Linux on this system. Like mp3 and stuff like that.

---

### Post by omegamike3 on 2007-08-13
I'm not sure he's entirely ready to dive head-first into linux, so, keeping windows around for a while is going to be necessary. and yes, he can share that third partition, be it formated as FAT32 or NTFS, however if it is NTFS, Ubuntu will have to be configured to read/write to it, which isn't terribly hard. Although, linux isn't the best at writing to NTFS drives... but I'm sure he'll be fine ;)

---

### Post by moose16285 on 2007-08-13
:confused::confused:Ok ladies and gents;

I have had little exposure to Linux. I did the Lindows things a few years ago and went back. A buddy recommended me to Ubuntu last week and here i am now. I come to this post for help because the last post is right where my troubles are. here we go...

I have used partition magic 8 to resize my 40gb hdd to 19gb ntfs and 19gb linux ext3... now i'm installing... says i need a ROOT to install... no ROOT has been selected or something... i'm am on a laptop talking to you but am installing to a PC i build... never had any problem with windows but i did enjoy the linux thing when i was using it before... hope you can help so my dreams dont crash on me to get back to linux...


cheers,
Moose

---

### Post by merlinus on 2007-08-13
IIRC, right-click on the partition and you will see a dropdown list of mount points.

Select / for root.  /swap should be made automatically.  You may have to leave 1.5G free from / for it.

-merlin

---

### Post by bwtranch on 2007-08-13
Yeah, I ran into this one time. I don't know if I ever figured that one out or just said forget it. Overwrite windows and just went back to the GRUB installer. I think what it's asking is if you want to make a file system with windows or unix as root. Then it will put everything under the root folder that you specify. This is why dual boot systems are scary. maybe someone will put their 50 cents in. (Inflation ya know.) 'Cause you could theoretically have two Unix systems at the same time, as long as they use the same kernal version like /ubuntu/home/jim/usr or cd /mandriva/home/jim/usr and they could share the same files because they are using the same kernal version. I have never tried this, but it should be possible. I don't know if I would ever want to try it, either:) But, windoze uses a different file system that is not hierarchal and is not even based on anything that is Unix, because it is a bad hack. You guys can look at my post about that if you want. But, it doesn't matter. Let's see if anyone has anything to say about it.

---

### Post by bwtranch on 2007-08-13
Re: #21 Merlin's post hadn't come in yet. Sounds good.

---

### Post by tk338 on 2007-08-14
Someone has recommended me to Wubi... can you use that permanently

---

### Post by logos34 on 2007-08-14
> **tk338 said:**
> Someone has recommended me to Wubi... can you use that permanently

You'll get faster performance if you transfer it to a separate hard disk partition:
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

