---
title: "Ubuntu 12.04.2 LTS (Precise Pangolin) INSTALL failure"
date: 2013-09-11
forum: Installation &amp; Upgrades
---

### Post by ronxp20002 on 2013-09-11
I have downloaded the Ubuntu 12.04.2 LTS (Precise Pangolin) desktop i386 ISO  for my child's Acer Net-book.  I have to use an external CD drive to install it.

It gets around 70% or 80% done on the progress bar, then the installer crashes.  I have burnt multiple CDs, tested the hard drive, and downloaded the ISO multiple times also.

I have NO LINUX Boxes at all, I have to do everything from a Windows PC.

A couple years back, when installing on a slower older PC, I remember I had to somehow disabled UBIQUITY.  I assume this is to disable the graphical banners displaying the features during the install.  I had the same problem back then, but this fix allowed me to install it.

Is that what I need to do again ?  I lost the instructions on how to disable UBIQUITY using a Windows PC.  I have NO Linux boxes.  Will I be editing the a file within the ISO?

What the installer says is that the CD/DVD is bad, to burn a copy slower (something along this lines).   As mentioned above, I have done everything to avoid this error, and nothing helped.

One last bit of information, the net-book contains Windows 7 starter, and I am letting Ubuntu install along side it, so I have a choice of either OS for my child.

I hope to obtain some help from someone please.  Thank you.

---

### Post by VMC on 2013-09-11
When you boot the livecd, there a choice to check the media. If that checks out you don't have to keep downloading it again.
When you boot the livecd, press the 'F6' key then check on the 'nomodeset' and return. It should get you going. 

Also, when it start up and you see the Ubuntu logo push the 'Esc' key and then you can watch the messages come up. Maybe there will be an indication as to how it failed.

I do remember several releases ago, that we needed to alter the Ubiquity string, but it is the installer, so you need it.

---

### Post by ronxp20002 on 2013-09-12
There is NO choice to check media unless I do the F6 later during the install as you mentioned.  

LiveCD?  I am NOT downloading during the installation, I merely burned the ISO i386 desktop version.  Here is the link I use:

[http://old-releases.ubuntu.com/releases/12.04.2/ubuntu-12.04.2-desktop-i386.iso](http://old-releases.ubuntu.com/releases/12.04.2/ubuntu-12.04.2-desktop-i386.iso)

I select the first web link download, that says, PC (Intel x86) desktop CD

 I did find the nomodeset option, and selected it with enter so an X was beside it.  This DID not help.  I get the same CD/DVD hard drive error.  I know it isn't a CD or hard drive error, as I have another net-book, the exact same model, and it presents the same installation problem.  Only difference between the net-books is that one is blue, the other is purple...lol  Anyway, moving along..............

I just have a feeling it is related to the graphical interface installation that the old UBIQUITY option used to remove.

Any ideas now?  Thanks so much for helping.  I appreciate it, and I am all ears.

Perhaps I should discard 12.04.2 and try 12.04.3 ????

---

### Post by VMC on 2013-09-13
Can you do an md5sum on the iso you downloaded then copy results back here.

edit: open a terminal (Ctrl+Alt t), then type md5sum <whatever the name of the ubuntu file>.iso
for example:
*md5sum precise-desktop-amd64.iso*

---

### Post by mastablasta on 2013-09-13
he is on windows. to the OP - follow this guide here instead to check the md5sum of the downloaded ISO: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

you can search for mini.iso [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
then follow this guide: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
mini iso has text installer.

furhtermore what kind of CPU do you have? some Atoms have GPU that have very poor or even nonexistant linux support (becuase the GPU part is not from intel). though this is probably not the case here.

you can also try to install from USB instead (use linux live usb or unetbootin to move the image to USB stick).

Ubuntu might be too demanding on Atom, so you might consider Xubutnu or Lubutnu istead.  or maby even KDE with netbook plasma interface. although 12.04 should still have the 2D unity availbale i believe...

finnaly make sure you have less than 4 primary partitions (3 can be occupied, 1 has to be free) otherwise you won't be able to install.

---

### Post by ronxp20002 on 2013-09-13
Checksums are the same, 90a4c7bd3901cd980cd4b48198e84eb1.

Yes it is an atom CPU, but 12.04.2 lists my netbook as being fully supported.

I tried USB installs with both unetbootin and Universal USB installer, but evidently my system does not work with this type of install.  While I boot many things from USB on this system, Linux will not. I done researched this problem tho, and there are tooooooooooo many suggestions to change the subject at hand for this moment.  That is another battle.

The minimal may be my last resort.  I rather wait on a solution someone else may know.

One quesiton about the minimal CD tho, after I get it installed, will it eventually update to the full blown version that I am trying to install?  Or will it always stay minimal?

I have not altered any partitions.  It's just the net-books stock partition setup

---

### Post by ronxp20002 on 2013-09-13
Here is where it says my exact model supports Ubuntu.

[https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250](https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250)

---

### Post by buzzingrobot on 2013-09-13
> **ronxp20002 said:**
> 
One quesiton about the minimal CD tho, after I get it installed, will it eventually update to the full blown version that I am trying to install?  Or will it always stay minimal?

 

When you install with the mini iso, it eventually offers you a long list of desktops and other environments to install.  One of those is the standard Ubuntu Desktop. So, yes, you will get the "full blown" version.

The minimal install is minimal in this sense:  The CD image contains only enough software to boot and ask you a few questions. After that, it downloads everything from an Ubuntu server, rather than copying files from the CD or DVD. 

I'm not sure why you are grabbing a 12.04 image from "old releases" since 12.04 is the current LTS release.  That, by the way, has recently been bumped to 12.04.03.  Try downloading from here, just in case:  [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

More here, including how to burn CD/DVD/USB's in Windows:  [http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

---

### Post by ubfan1 on 2013-09-13
What is the partition setup?  You may have only four primary partitions, and since most installs will need a minimum of two partitions (one root, one swap), you may be running out.  What you need to do is ensure you have an extended partition as one of the primaries, then you can create as many logical partition inside the extended as you need.  Best to do this from a partition editor running on the live media (try), before attempting the install.

---

### Post by ronxp20002 on 2013-09-14
Problem solved.  I would like to thank everyone for their kind help and nice suggestions.

 "Apparently" the NEW external cd/dvd drive I was using was not getting the power needed to properly operate.  It is a LG slim GP50. Maybe the net-book USB ports aren't up to standards like on a desktop PC or full blown laptop.  The external cd/dvd works great on all the other computers in the house.

I took another suggestion,  I went and got a NEW USB thumb drive.  The older Kingston 2GB green Data Traveler's would NOT boot on the net book.  They boot on all other PCs in the house though.

So I got a Team USB 3.0 16GB from Newegg for about $11.  I took Universal USB installer, and the ISO I mentioned from my first post, and it booted wonderfully.  Ubuntu installed without a hitch.

 Thanks again to everyone.

---

### Post by BlinkinCat on 2013-09-14
Hi,

I am glad you solved your problem -

In case you are unaware - [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

