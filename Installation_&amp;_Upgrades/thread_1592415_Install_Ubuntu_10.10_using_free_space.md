---
title: "Install Ubuntu 10.10 using free space"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Vexiphne on 2010-10-10
Heeeeelp. 

I've just downloaded 10.10, made install USB, removed the partition that used 10.04 (have home on an other partition), started the installation but the choice "install using free space" is removed from the installation. 

How can I install 10.10 using the free space on harddrive???

WHY did they remove the choice "install using free space" :confused: :confused: :confused: ](*,) :roll:

---

### Post by ronparent on 2010-10-10
You can probably by-pass the problem by using gparted on the live cd to create an empty partition for the install.

---

### Post by Vanillalite on 2010-10-10
> **ronparent said:**
> You can probably by-pass the problem by using gparted on the live cd to create an empty partition for the install.

I'm trying to do the exact same thing as the OP.

I've got my free space, but what should I do with it in gparted?

[IMG]http://i52.tinypic.com/f25t9z.png[/IMG]

My NTFS partition is my Win 7 stuff, and I just want to install 10.10 along side of it. I assume I'd need my standard EXT4 partition as well as a small linux swap partition? Do I make those in gparted?

---

### Post by Old_Grey_Wolf on 2010-10-10
The installation should give you the option to "Use Entire Partition" or "Use Entire Disk". For me, the "Use Entire Partition" option was the same as selecting "Install Using Free Space" in the previous installers.

I shrunk the windows partition using windows first. Or using gparted for a Linux OS.

I have a backup of my important files; therefore, I can experiment with little fear of losing anything.

---

### Post by ronparent on 2010-10-10
I would suggest creating an extended (logical) partition out of the unallocated. Within that you should create a swap at least as large as your installed RAM. The remainder can be your /, or, / and/home. Putting everything after your existing win 7 partitions in the extended doesn't limit you to four partitions total. At least you won't be posting that the system isn't allowing you to crate a 5th primary partition. LOL

If you choose to manually partition during the install, don't forget to designate the / mount point in the target for your install and the swap partition as well as any other linux partition you want to install to (ie a separate /home). Good luck with all of it.

---

### Post by verymadpip on 2010-10-11
I reduced the size of my unallocated by whatever size I wanted my swap to be (about 5Gb, like it used to do automatically.  I use about 400Gb for my Ubuntu partiion) & made that my ext4 "/" mount point partition, leaving some unallocated space in the partition table. (I used a radio button to place the large space at the beginning of the partition). I then made the small unallocated space my swap.  I was pretty freaked out by the whole thing to be honest & nearly started smoking again :).  I'd post a screenshot, but I'm using a different machine at someone else's house at the moment.

Sorry, I should add I created the free space with GParted (deleted Ubuntu 10.04 & swap) & then booted the liveCD & used the installer

---

### Post by Vexiphne on 2010-10-11
Thanx for all the replys, but I decided to take backup of everything and install the easy way of letting it use the entire HD.

And thank you Ubuntu for going back to the "good" old days when things was so God D**n complicated :(

This is taking ubuntu backwards instead of forward.:cry:

---

### Post by diafygi on 2010-10-11
WTF! I am totally screwed! I'm having the same problem!

I have a windows partition (10GB), video editing files partition (60GB), and a logical partition (10GB). I usually have Ubuntu installed on the logical partition (both '/' and swap).

In previous versions, I've always booted into the live cd, deleted the Ubuntu partitions ('/' and swap) with gparted, and then selected the "use largest free space" option in the installer. It makes for an easy clean install of Ubuntu without losing my editing files. WHERE DID THIS OPTION GO???

I've never used the advanced install option, and it scares the crap out of me. I can see the free space in the list of partitions. I tried to format this free space as a root (/) ext4 partition on the advanced screen, and then I got a popup asking for a swap partition when I tried to continue. I have no idea how big to make a swap partition! When I selected "use largest free space" before, ubuntu made the swap and root partitions automatically. How big should I make a swap partition.

I'M SO BORKED. WHY WOULD THEY DO THIS??? HELP!!!

---

### Post by Vexiphne on 2010-10-12
> **diafygi said:**
> WTF! I am totally screwed! I'm having the same problem!

I have a windows partition (10GB), video editing files partition (60GB), and a logical partition (10GB). I usually have Ubuntu installed on the logical partition (both '/' and swap).

In previous versions, I've always booted into the live cd, deleted the Ubuntu partitions ('/' and swap) with gparted, and then selected the "use largest free space" option in the installer. It makes for an easy clean install of Ubuntu without losing my editing files. WHERE DID THIS OPTION GO???

I've never used the advanced install option, and it scares the crap out of me. I can see the free space in the list of partitions. I tried to format this free space as a root (/) ext4 partition on the advanced screen, and then I got a popup asking for a swap partition when I tried to continue. I have no idea how big to make a swap partition! When I selected "use largest free space" before, ubuntu made the swap and root partitions automatically. How big should I make a swap partition.

I'M SO BORKED. WHY WOULD THEY DO THIS??? HELP!!!


I share your pain...

I wonder what they were thinking of when they removed that function. Did they have an office party and got drunk and removed it under the influence?

---

### Post by mtron on 2010-10-12
imho this is a regression in the installer. Did somebody file a bugreport about this?

---

### Post by mörgæs on 2010-10-12
@diafygi: If you want help with your problems, you might do yourself a favour by using a more moderate language.

---

### Post by Vexiphne on 2010-10-12
> **mörgæs said:**
> @diafygi: If you want help with your problems, you might do yourself a favour by using a more moderate language.

But I do understand him ;)

---

### Post by setcho on 2010-10-12
I agree that this is a regression in the installer... however I managed to achieve my aim by going back into windows and extending the volume into the unallocated space, I then returned to the Ubuntu partitioner where I used the slider to partition the drive.

If windows won't let you extend the volume try using a free partition tool like Easeus or Parigon they should be able to do it, I'm sure you can do it in gparted as well but I don't use it very often so I wouldn't know

Having said that this won't work for the people that have a partition between windows and the unallocated space. Therefore it is illogical for Ubuntu to have removed the free space option in the first place.

---

### Post by Vexiphne on 2010-10-12
> **setcho said:**
> Having said that this won't work for the people that have a partition between windows and the unallocated space. Therefore it is illogical for Ubuntu to have removed the free space option in the first place.

Amen to that :)

---

### Post by iclestu on 2010-10-12
Yeah - I have the same issue. Seems nuts to remove the option?

I have just slid the slider along to the smallest possible size for the ubuntu install. I hope to use gparted after install to then increase this partition by taking up the free space. I have nicked a couple of gb from the windows partition to achieve this but ho hum. Copying files on netbook as we speak... wish me luck!

---

### Post by verymadpip on 2010-10-12
Good luck.

How did it go?

---

### Post by diafygi on 2010-10-13
Ok, so there's a bug entry on this issue ([#652852]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852")).

Pjotr12345 posted a [workaround]("http://sites.google.com/site/easylinuxtipsproject/partitioning") for those who want to install 10.10 in free space. This is how I was able to install 10.10.

I created a swap partition (750MB*) in the free space with gparted on the Live CD, then began the installation process. I selected the advanced partitioning option in the installation steps. I added an ext4 partition to the free space and set that partition as '/'. Ubuntu was able install completely after that.

Whew! I pray this will be fixed by 11.04...

*Note: if you need to hibernate your computer, the swap partition should be bigger than your RAM amount.

---

### Post by Niva on 2010-10-14
Wow, what a horrible omission to make on the installer.  I always delete my old Ubuntu partitions within windows prior to doing a clean linux install.  This time I can't select to use the free space.

I surely hope they bring it back in the future but 10.10 fails big time.  Now i gotta figure out how to partition the free space manually.  Nobody should have to do that.

---

### Post by Niva on 2010-10-14
Quick google search reveals a guide here:

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Hope this helps folks, I've done this before and the guide looks complete.

Now I'm uncertain what 10.10 was supposed to be using but I guess it's going to be EXT4 for all partitions.  I'll see if I can find a quick answer.

---

### Post by diafygi on 2010-10-14
For everyone who is affected by this problem, please mark the [bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/652852") as "This bug affects me" at the top of the page.

---

### Post by C.S.Cameron on 2010-10-14
So what is the problem with going to manual partitioning and selecting the space you want to use there?

---

### Post by diafygi on 2010-10-14
> **C.S.Cameron said:**
> So what is the problem with going to manual partitioning and selecting the space you want to use there?

Well, several reasons:
1) Some amateur users (including me) have installed Ubuntu with the free-space method for several iterations. A change like this throws them into a realm they haven't experience before. It adds a lot of stress to their install process because they have never used manual partitioning. They don't fully understand all the options and worry that they will do something wrong and brick their computer. I know, it's a silly anxiety, but this is uncharted territory.

2) For people who are doing this the first time, they may not know what partitions to create. The swap partition was created automatically in previous Ubuntu releases when selecting the free-space option. I had no idea how much space to allot for the swap partion. There are no instructions in the manual partitioning option for which partitions to create.

3) The Ubuntu partition was previously ext3, but now it is ext4. How are users supposed to know. Luckily, there is online help, but people might not have access to the internet while installing.

---

### Post by miki4242 on 2010-10-26
I've added myself as being affected by this bug and have added my take on the matter to the bug report.

IMHO this throws the Ubuntu installation experience right back to the previous century, never mind the nice eye-candy graphics in the installer.

This bug adds so much more gravity to 'that other bug", [LP: #1]("https://bugs.launchpad.net/ubuntu/+bug/1"), and a closely related one pertaining to a certain fruit company whose CEO likes making bold statements while wearing turtleneck&jeans(TM). Neither of the two OSes force users to delve into partitioning schemes and filesystem choices for the default use case.

Ubuntu, we need you to fix this!

---

### Post by Niva on 2010-11-11
> **C.S.Cameron said:**
> So what is the problem with going to manual partitioning and selecting the space you want to use there?

The ease of use is the main issue here that folks are complaining about.  

Another hideous problem with the manual partitioning is that it has a limit of only allowing up to 4 partitions.  Why they chose 4 is beyond me, and why the old automatic install wasn't affected but this is beyond me... then again, maybe it was but I never noticed up until I had to do this manually.  

PS:  I have 2 windows partitions on this disk already.  Win 7 also actually likes to create it's own little partition for giggles just to throw a wrench in this.

---

### Post by shokoup on 2010-11-18
I don't know why ubuntu programmers always want us suffer!!, I always expecting removing a good major feature such " install in free space", every new version you should see a good feature removed, i don't know if this upgrading for them??!!! I'll change to fedore till next ubuntu version

---

### Post by Tankerdog2002 on 2010-11-21
There simply is no excuse for this.

---

### Post by Tankerdog2002 on 2010-11-21
> **Niva said:**
> Quick google search reveals a guide here:

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Hope this helps folks, I've done this before and the guide looks complete.

Now I'm uncertain what 10.10 was supposed to be using but I guess it's going to be EXT4 for all partitions.  I'll see if I can find a quick answer.

Can't use this guide. We tried it on two new laptops and got hosed both times. We go through all the steps but the free space gets grayed out and says "unusable". 

We get errors even if we create a partition with Gparted.

Either way 10.10 won't install.

Any ideas anyone?

---

### Post by kansasnoob on 2010-11-22
> **Tankerdog2002 said:**
> Can't use this guide. We tried it on two new laptops and got hosed both times. We go through all the steps but the free space gets grayed out and says "unusable". 

We get errors even if we create a partition with Gparted.

Either way 10.10 won't install.

Any ideas anyone?

You might find some of the info here useful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

If you need some specific partitioning recommendations we'd at least need to see the output of:

```
sudo fdisk -l
```

and:

```
free
```

---

### Post by jehiva on 2010-11-22
I really dislike Ubuntu after this change.

---

