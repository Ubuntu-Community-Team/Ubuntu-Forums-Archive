---
title: "Ubuntu Installation - Which Partition Option?"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by famico666 on 2008-11-09
Hi all,

I'm of average computer literacy (I can't be as bad as some as I am actually making the switch to Linux).

I have a 320Gb hard drive. C has Vista on it, D is empty. They are both 160Gb.

I'm trying to install Ubuntu 8.10 on D, leaving Vista intact on C.

Now, I don't know what to do in the installation, when it comes to the partitioning part.

There are three options:

1) Guided something about sda1, sda2 etc, which I don't get.

2) Guided something or other - it mentions whole disk and 320Gb, which sounds like it's going to use both disks.

3) Manual - but again it shows all 320Gb blued out as being given over to Ubuntu and gives me no options... but I'm hoping I can change that on the next screen, right?

So which option do I need? I'm guessing not 2. I don't understand 1 at all, but it might be that.  3 seems like an option too but i was scared by the lack of immediate options - does the next screen give me some control? I'm just scared of selecting manual and then it doing some crazy stuff that I didn't want (I'd have liked some options available to me before clicking the dreaded 'next' button.

Thanks for your help guys. Have some popcorn. :popcorn:

---

### Post by jklslvch on 2008-11-09
**** it blow everything away... That way u wont mess up :lolflag:

Ihavent seen the new installer take a pic with ur phone or sumthin

the best thing is manual..and on the next screen it asks you how you want the space to be spread out like

sda1> already has vista
sda2> your D partition as you say wich must me NTFS so youd select that one for the "/" 
and aditionally makea swap space

what i would do take MIN 15GB for ubuntu if u want more go for it
and swapspace MIN 512MB but usually its the double of your ram

---

### Post by m_l17 on 2008-11-10
Adding to what posted jklslvch. I would also make a /home partition. That way if you want to reinstall or have to it will be much easier. Use the rest of the free space for it or whatever size you think is best.

Your /home partition is where all your user settings go and data like documents etc.

```
sda2> your D partition as you say wich must me NTFS so youd select that one for the "/" 
```

You also need to change the file system to ext3 and format it, you can do anything without doing this first. And whatever you don not touch sda1, unless you what to wipe out Vista.

It is good practice to make a backup of you current Vista install, just in case things go wrong. One last thing the sda1 , sda2 should be what will be listed by the Partition Editor, but might be different. Good Luck and if you get lost post back.

---

### Post by famico666 on 2008-11-10
No, no, you've got it all wrong, it's not supposed to be this hard! :o)

I can't see anything about changing the file system to ext3 in any documentation on the internet. Doesn't it do that itself? m_l17, you mention convertng to ext3, but jklslvch, you say it must be in NTFS.

My format hard drive option in vista only allows NTFS. SHould I just format it like that? I've deleted everything from the drive but I guess that isn't enough.

So, I need to:

1) Back up Vista - this is the hard part. One reason I'm changing is that my laptop is in German. So I can't back it up. Is there a high chance of it going wrong?
2) Format disk and change to ext3 (how?)
3) Select manual
4) On the next screen, leave sda1 alone, give 15Gb for Ubuntu, 2Gb for Swap and the rest for /home.

jklslvch, what does '/' mean? Is that where Ubuntu will be installed?

Thanks.

---

### Post by sinned3k on 2008-11-10
This was frustrating as I was stuck at the same place.

I installed 8.10 a a few days ago and had the same problem. When you get to partitioning screen. An easier alternative is to use option 1 as this install all your directories all on one partition.

The manual option is much better though all you might come across the blank screen once installations complete. 

For the Manual Option:

Like you say it shows 320GB right?

Follow these steps:
- edit the partition and set used size to be 160000 (it has to match your current desired partition size for your C:Drive

- create a new partion
  1. ext3 - mount on "/"
  2. swap - mount on swap
  3. ext - mount as "/home" optional
  4. FAT32 - to access your folders on your vista - mount as /windows


That should at least get you on the right track.

---

### Post by INeedaCoffee on 2008-11-10
Sinned, given the 160GB available space, what size would you recommend for each partition?

---

### Post by antoz on 2008-11-10
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

The above link gives a lot of help regarding partitioning, I would do my partitions manually, leave C alone and repartition D 
15 gig are enough for "/" about 2 gig for "swap" the rest I would split with some space allocated to "home" and the rest format FAT 32 so it is accessable to both windows and Ubuntu. Hope this helps, cheers,A.

---

### Post by famico666 on 2008-11-10
Thanks, that makes it clearer.

But you say "create a new partition". I thought I had one already. From what you're saying, am I right in thinking D: is going to be split into D: E: F: and G: for each of the points 1-4 you mention?

Also, what does "mount on" and "mount as" mean?

---

### Post by Bölvaður on 2008-11-10
Do like the people above me say. Do it manually, because of 2 main reasons; you have more control over what is happening and secondly because it is the only wise way until the other options are made more intuitive.

some things that was not told above me:

On the live cd (the ubuntu disk you have) is a program called gparted (partition manager) which is probably the place where you would want to do all the partitioning before continuing to install.

swap is like pagefile in windows when ram overloads. the best way is to have special partition on the harddisk.
Swap partition is supposed to be small (similar to your ram size) and is mounted automatically so you only have to make the partition and linux will do the rest.

/ is the filesystem, where all programs are kept. leave it about 10-20gb, perhaps a tiny bit more to be safe.
There is a drop box to pick / during the installation (under manual partitioning). Also you should be able to pick ext3 as the filesystem on that partition.

/home should be the rest, it is a place where all your data and config files are kept. you do the same as above.



*added*

Mount is when you connect device to your computer. When you are installing and pick the manual option you are faced with which partitions to use, what filesystem should be on each of it and where it is connected (mounted).
The entire thing should have root (aka "/") and under it you have your personal data (/home). You have to select which partitions are used as each. And by that it will be automatically done for you each time you turn on the computer.. otherwise you might need to mount manually.

Also. Only windows uses letters to distinguish partitions. Here we use "logical names" which is sda0 which means satadisk A (that would be B if this is second harddisk) and then number of the partition.

you can see how it is in gparted (the partition manager which you find under System &#8594; Admininstrator &#8594; Partition manager or by typing gparted in terminal)

---

### Post by INeedaCoffee on 2008-11-10
famico666, when you select Manual and click next, you are able to create the partitions. You probably have to delete the existing NTFS partition to allow you to create the Ubuntu ones. Make sure you have good backups!

fwiw I am at the same stage as you. I have a large empty space on a second disk but Ubuntu doesn't want to create a partition in that space. It seems to prefer shrinking the Windows partition on the first disk! As a result I have to use the Manual method. I'll try tonight.

---

### Post by antoz on 2008-11-10
When I say create new partitions it means first of all you would delete D then create new partitions in the unalocated space. 1 for your ubuntu install "/" (format ext 3), 1 for "home" (format ext 3), 1 for "swap" (format solaris swap),  and another one if you wish for sharing (format fat 32).

As you can only have a certain number of primary partitions you may have to create an extented partition to accommodate it all.

---

### Post by antoz on 2008-11-10
Here is a screenshot of my partitions to give you an idea.

---

### Post by Bölvaður on 2008-11-10
to repeat my self, always use gparted, the same program antoz was showing.

---

### Post by famico666 on 2008-11-10
Thanks guys. It worked. Though there was nothing called GPartEd.

There were a few silly hiccups along the way - such as it not liking me using a capital letter in my name and then not letting me delete the capital letter (I had to push back and redo the whole partitioning palaver again).

But in the end, it worked. Now hopefully I can say goodbye to Microsoft forever!

---

### Post by antoz on 2008-11-10
Glad it worked out, I think in the later Ubuntu versions they just call Gparted "partition editor".
Another very solid program to do partitions and also to create complete backup images of your partitions is Acronis but it is not free. Cheers,A.

---

### Post by m_l17 on 2008-11-11
I'm glad you got it working. I should have posted this earlier:

[https://help.ubuntu.com/community/DrivesAndPartitions]("https://help.ubuntu.com/community/DrivesAndPartitions")

That will give you a better understanding about partitioning in Linux. A suggest you mark this thread as solved. On the first page, click on thread tools and click on the last option.

---

### Post by SisterNotes on 2009-04-15
Thank you all for the additional details on partitioning. I'm still stuck on one issue. First I have a c drive that I don't want to touch (though it's the reason I'm switching to Ubuntu...). I also have a d drive with nearly 20 gig. At least I did until this morning. For reasons no longer clear to me, I thought I needed to split it to dedicate a portion to Ubuntu. So I tried to resize the 20 gig to a 10 gig for installing Ubuntu. The result is that I have a 10 gig partition and 10 gig of free space that is now called "unusable". Have I now "lost" the opportunity to use 10 gig of hard drive space? But before we go there, because I'm anxious to get this installed...assuming I started with 10 gig, would I now create a new partition or edit the existing partition? In other words to get to the 1. ext3 (on "/"), 2. swap (on swap), 3. ext (on "/home") and 4. FAT32 (on "/windows") described in an earlier reply, do I keep "creating new partitions"? Thank you for your insights!

---

