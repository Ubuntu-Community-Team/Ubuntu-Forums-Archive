---
title: "Partitioning for a Windows/Ubuntu dual boot"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by WebDrake on 2005-11-23
Hello all,

Hope this is not a pain-in-the-ass question, because how to partition your system is not exactly secret info.  But I want to make sure I do this right... ;-)

Currently I have a Dell laptop with 80GB hard drive, formatted as one big NTFS partition with about 25GB actually in use.  (Funnily enough, by going through the directories in the C:\ drive and selecting their Properties to check how big they are, I can only account for 17GB of this.  Any ideas as to why?)

The idea here is to resize the NTFS partition and add other partitions to the disk so as to have dual-boot with Linux.  My personal data files (documents, MP3s, graphics files, the works) should be accessible from either OS, and key applications like Firefox, Thunderbird etc. should likewise share the same profile.

I have the ext2fs.sys driver installed under XP so I can read/write to ext2 and ext3 partitions.

So, here's what I had in mind...

**/dev/hda1/**    ... the NTFS partition for Windows OS and applications, probably about 30GB.

**swap/**   ... swap file for Linux---3GB sound good?  Is it possible and worthwhile setting this up so that both Linux and Windows can use this swap space?  What file system is best here?

**root/**    .... Linux OS installation.  I take it this is also where Linux applications are installed---there's no sense in having a separate partition for apps?  Probably worth dedicating 15-20 GB to?  I'd like this to be *not* readable by Windows, so maybe an alternative file system such as XFS is in order.

**home/**   .... Home directory for users.  This is where all my personal data files would be stored, and so it should be accessible from both Linux and Windows.  So, about 10GB, ext3 ... ?

The remainder could be given over to a scratch partition or maybe I could give it all to the home/ partition or the install directories.

... Is there anything I've missed out here, or anything that would be a good idea to do?  Any thoughts?

Many thanks,

       -- Joe

---

### Post by aysiu on 2005-11-23
Five things.

1. Follow these directions:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

2. I don't have full confidence that Windows writing to Ext3 leads to stability long-term. It's probably better to have a FAT32 partition to share information between the two.

3. The /home partition (which holds all the files) should be bigger than the / partition, unless you have very few files and plan on installing a lot of programs.

4. 3 GB of swap is excessive. 1 GB is probably more than enough.

5. Always back up your work, even if you think you know what you're doing.

Otherwise, your plan looks good.

---

### Post by yesplease on 2005-11-23
Suppose you take 40GB for ubuntu: 5 or 6 GB / (root) 1GB swap (windows needs its own swap) and the rest /home. format all in ext3. 

If you really want to, you can make a FAT32 partiton for exchage. Leave some space unformatted and do this later.

Well, synchronous posting with Aysiu :)

---

### Post by tomski on 2005-11-23
you could format with reiserfs and download rfstool, yarg, or rfstool gui for copying files whilst in windows as i use these all the time for my ubuntu/winxp setup all i make sure of is that i dont write to ntfs and have a seperate Rfs partition mounted as /public in fstab

i'll see if i can find the links to these tools and edit this post (if wanted)

---

### Post by tomski on 2005-11-23
you may find this helpfull to copy the files from a reiserfs partition within windows

Extract this in program files
[http://p-nand-q.com/download/rfstool/rfstool-0.14.zip](http://p-nand-q.com/download/rfstool/rfstool-0.14.zip)

and extract this in the same directory
[http://yareg.akucom.de/download.cgi/YAReG-0.9.9.zip](http://yareg.akucom.de/download.cgi/YAReG-0.9.9.zip)

if you have problems with those try this
[http://www.wolfsheep.com/map/rfsgui-2.0.zip](http://www.wolfsheep.com/map/rfsgui-2.0.zip)

i'll see if i can find similar tools for ex2 & ex3 partition and post the links
ok

---

### Post by WebDrake on 2005-11-23
> **aysiu]2. I don't have full confidence that Windows writing to Ext3 leads to stability long-term. It's probably better to have a FAT32 partition to share information between the two.[/quote]

Let's clarify to make sure I completely understand---the home/ directory is to Linux what the "Documents and Settings" folder is to Windows, right?  A directory containing user configuration info and also documents.

So, with this in mind, wouldn't it be best to simply set up the home/ partition as FAT32, to be read from both Linux and Windows?  Or are there good security reasons why I shouldn't do that, and should have a separate partition for shared files?

To what extent do you think the Windows/ext2 issue is a serious problem?  Is it something which regular maintenance can prevent being an issue or is it something I'm just better off not trying to deal with?

> 3. The /home partition (which holds all the files) should be bigger than the / partition, unless you have very few files and plan on installing a lot of programs.

In general I've found that most of my *real* data files are not that big, since they consist of (open)office documents, text files (actually, LaTeX files  said:**
> 4. Always back up your work, even if you think you know what you're doing.
Isn't forgetting this step a sure sign that you *don't*? ;-)

I was wondering: is there a way to easily and effectively copy the NTFS partition to another computer, so that if an accident occurs it can be directly copied back to the disk?  For various reasons it would be tricky to do a complete reinstall of XP and applications, otherwise I'd be tempted to just back up data, wipe the drive, and do a whole clean install of XP and Ubuntu together.

> Otherwise, your plan looks good.
:-D

Thanks very much for all the advice, and for the useful link!

Best wishes,

       -- Joe

---

### Post by WebDrake on 2005-11-23
[QUOTE=tomski]i'll see if i can find the links to these tools and edit this post (if wanted)[/QUOTE]

Hi Tomski,

Any info is welcome so please do add what you can. :-)

With regards to the setup, all that is *really* important is,

(i) I have an XP Pro install with space for a reasonable number of applications, and the partition can't be written to by Linux;

(ii) I have a (K)Ubuntu install with space for a reasonable number of applications, and the partition can't be written to by Windows;

(iii) I have a common space, with read/write access from both OS's, to store files and also profiles for common applications like Firefox, Thunderbird and OpenOffice.org.

With regard to the file system for the Linux OS partition, I'm pretty open-minded about whether it should be ext3, XFS, ReiserFS, whatever, because I don't really know much about what distinguishes them... ;-)  However, fast number crunching performance is important if that makes any difference.

---

### Post by aysiu on 2005-11-23
[QUOTE=WebDrake]Let's clarify to make sure I completely understand---the home/ directory is to Linux what the "Documents and Settings" folder is to Windows, right?  A directory containing user configuration info and also documents.[/quote] Yes, it is the equivalent of Documents and Settings, which also includes My Documents. And for some people, My Documents is huge!

> 
So, with this in mind, wouldn't it be best to simply set up the home/ partition as FAT32, to be read from both Linux and Windows?  Or are there good security reasons why I shouldn't do that, and should have a separate partition for shared files? /home cannot be set up as FAT32. It has to be a Linux native format (Ext3 or Reiserfs). You can read and write files in FAT32 from Linux, but storing your config files there is a bad idea.

You can, however--if you're planning to store your larger files on the shared FAT32 partition--make the /home partition quite small, as it would otherwise hold only configuration files.

> 
To what extent do you think the Windows/ext2 issue is a serious problem?  Is it something which regular maintenance can prevent being an issue or is it something I'm just better off not trying to deal with? You're better off sticking to FAT32. It's the only format that can be read from and written to *reliably* by both Linux and Windows.

> 
I was wondering: is there a way to easily and effectively copy the NTFS partition to another computer, so that if an accident occurs it can be directly copied back to the disk?  For various reasons it would be tricky to do a complete reinstall of XP and applications, otherwise I'd be tempted to just back up data, wipe the drive, and do a whole clean install of XP and Ubuntu together. I think there are programs like this. Ghost-something-or-other.

---

### Post by WebDrake on 2005-11-24
> **aysiu]Yes, it is the equivalent of Documents and Settings, which also includes My Documents. And for some people, My Documents is huge![/quote]
Yes, I've seen my brother's computer...  said:**
> You can, however--if you're planning to store your larger files on the shared FAT32 partition--make the /home partition quite small, as it would otherwise hold only configuration files.
OK, great.  That's what I'll do then.

There are a couple of things I don't fully understand about the instructions at [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) ....  Let's suppose that I am using the Ububtu + NTFS dual boot option.

Aside from the 10GB NTFS partition and the 10GB FAT32 partition, in these instructions only one ext3 partition is created---a primary partition---along with a swap partition.  Does this cover both root/ and home/ and all other things that could be used?  Is this the best way to do things, or is this just a compromise here because of small disk size (30GB)?  I had the impression it was preferable to create a separate logical partition for home/ and possibly other directories too.

Also, I take it the name /media/windows/ given to the mounted FAT32 partition is arbitrary---I can call it whatever I like, right? ;-)

Lastly, it's noted, "It's not wise for security reasons to leave your other partitions mounted all the time."  Can you clarify a bit?  Which partitions and why?

Many thanks for all this kind assistance, anyway. :KS

---

### Post by Irony on 2005-11-24
The instructions at [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) has you choosing the automatic partitioning to free space which creates a swap partition and the ubuntu partition which holds everything (including home directory).

I haven't created a separate home directory before but I'd guess its easy enough to do after you've finished the install. Assuming you've created an extra ext3 partition during install you would then presumably copy the home directory's entire contents including hidden folders to the extra partition and then configure some file to link to it. I'd guess with this set-up your ubuntu partition would only be a few gigabytes whilst the home partition would be quite large.

You can name the windows folder whatever you like. You would then have to mount windows in it.

[I]sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
sudo umount /media/windows/[/I]

To get a partition list;

*sudo fdisk -*l

---

### Post by WebDrake on 2005-11-24
> I haven't created a separate home directory before but I'd guess its easy enough to do after you've finished the install.
I suppose what I'm thinking of is: does it make any difference when you want to install a new Linux distro, e.g. when Dapper Drake gets released?  What I mean is, would having home/ located in a separate partition mean time spent backing up data files (because then only root/ would get wiped)?  Or am I just misunderstanding the Linux install process? :rolleyes: 

As it happens, I think all my data files will be in a separate partition from home/ anyway, so it probably doesn't make much difference. ;-)

Thanks for the advice!

---

### Post by aysiu on 2005-11-24
[QUOTE=WebDrake]I suppose what I'm thinking of is: does it make any difference when you want to install a new Linux distro, e.g. when Dapper Drake gets released?  What I mean is, would having home/ located in a separate partition mean time spent backing up data files (because then only root/ would get wiped)?  Or am I just misunderstanding the Linux install process? :rolleyes: 

As it happens, I think all my data files will be in a separate partition from home/ anyway, so it probably doesn't make much difference. ;-)

Thanks for the advice![/QUOTE] Where are your data files living? If they're on their own separate partition (say, a FAT32 partition you share with Windows), they also won't be reformatted unless you select that partition to be reformatted.

In other words, your data is always safe as long as...

1. They live on a separate partition from the system files
2. You aren't careless enough to accidentally reformat that separate partition when reinstalling

---

### Post by WebDrake on 2005-11-24
[QUOTE=aysiu]Where are your data files living?[/quote]

Wires are getting crossed here, I'm afraid, between what I intend to do on my laptop, and my more general questions about aspects of Linux I don't properly understand... :rolleyes: 

Let's forget my actual laptop for now, since I think I have a pretty good idea of what needs to be done with it.  What I'm asking is: is there good reason, for a single-user machine, to have a separate partition for the home/ directory (and possibly others)?

I was under the impression that this was a good idea because, in the event of installing a new distro, you just wipe the / partition where the main OS is, and the files on home/ get left alone except for perhaps some modification to the config files stored there.

But in the example link you posted to me earlier, the demo shows the creation of just one single ext3 partition to host the whole Ubuntu install---OS, the user's personal files, the works.

.... So ... in a general sense (not related to my specific install plan), what's the lowdown on this?  I have the impression that on a many-user system such as the ones I interact with at university, there are very good (probably essential) reasons to have home/ and various other directories stored in their own partitions (security reasons, ease of use on a many-node network, ...).  But what about a single-user machine?

And, in the event of installing a new distro, is it necessary to *reformat* the whole / partition (which would be a powerful argument for making home/ separate), or is that just necessary for the first ever install of a Linux OS?

Many thanks,

     -- Joe

---

### Post by aysiu on 2005-11-24
[QUOTE=WebDrake]What I'm asking is: is there good reason, for a single-user machine, to have a separate partition for the home/ directory (and possibly others)?

I was under the impression that this was a good idea because, in the event of installing a new distro, you just wipe the / partition where the main OS is, and the files on home/ get left alone except for perhaps some modification to the config files stored there.[/quote] Yes, this is a good idea for the very reason you stated, particularly if you're new (seeing as how you're more likely to experiment with something and accidentally screw up your system).

> 
But in the example link you posted to me earlier, the demo shows the creation of just one single ext3 partition to host the whole Ubuntu install---OS, the user's personal files, the works. This is another option. I use this because I don't mind redoing my settings for a clean install. I back up my files and reinstall--for me, it's fun to redo the settings and preferences again. For others, it's a pain.

> 
.... So ... in a general sense (not related to my specific install plan), what's the lowdown on this?  I have the impression that on a many-user system such as the ones I interact with at university, there are very good (probably essential) reasons to have home/ and various other directories stored in their own partitions (security reasons, ease of use on a many-node network, ...).  But what about a single-user machine? Even for a single-user machine, it's a good idea to have a separate /home partition because that holds the single user's preferences and settings.

> 
And, in the event of installing a new distro, is it necessary to *reformat* the whole / partition (which would be a powerful argument for making home/ separate), or is that just necessary for the first ever install of a Linux OS? Another Linux distro is an entirely new operating system. They're both using the same Linux kernel, but the entire operating system is different. You'd have to reinstall.

---

