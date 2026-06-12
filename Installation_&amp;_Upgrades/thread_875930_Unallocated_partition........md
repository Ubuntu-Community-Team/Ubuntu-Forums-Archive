---
title: "Unallocated partition.......?"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by Annigma on 2008-07-31
Hi :)

I 'lost' my Ubuntu Feisty Fawn a few months ago when I tried to install some dodgy RAM I'd bought. :cry: I decided to leave it till Hardy came out and I'd sorted my old (as in age: still got same old machine) PC out. I've just bought a 'Hardy Heron' live CD and took a look at it last night.

The Gparted app. just shows my whole HD as 149GB unallocated space.. I've tried rebooting a couple of times in slightly different ways, but it still shows the same. :confused:

XP tells me that I've got 6 partitions still: which is about right from when I had the dual boot going. I downloaded 'PC Wizard 2008' to help me try and read the 'whole' space, but sadly, it tells me even less than XP... :shock:

Basically, around half the HD is allocated to 3 'recognized' partitions C:, D:, and E: which account for approx. 80GB.

XP shows that there are 3 more separate partitions but only tells me that they are 1.39 GB, 40.98 GB and 1.86GB. These obviously 'were'(?) my Ubuntu partitions, but I can't work out how to see/read/recover/reuse them... :rolleyes:

I think the dodgy RAM must've damaged the small partition which contained info. telling GNOME/GRUB? to start up or something, but I don't really know.. *shrug*

I'm happy with my XP partitions (FAT, FAT32, and NTFS), but I'd really like to put Ubuntu back on the other 'space'..

Advice greatly appreciated.

---

### Post by RuleMaker on 2008-07-31
This is too confusing, please try to be more clear, write down which partitions you should have and which partitions you see in gparted.
If you see less partitions than you should it might be because allocated space is always grouped in one, well lets say "partition".

---

### Post by Annigma on 2008-07-31
Thanks for replying. I'll try to be more clear.

My HD has 3 readable/recognized partitions: C, D and E. D and E are fine. One has XP on it and is NTFS, the other is used for documents and such and is FAT32. I forget what C was for but it's got a firewall boot.ini file in it and a few text files but is otherwise empty.. it's FAT.

These three account for approximately half of my HD capacity.

The other 3 partitions I'm not sure about. They were used for Feisty Fawn successfully, and now I can't access them. If I look at the properties of my HD in Device Manager it shows C, D and E normally, but the other three it just shows the (nameless) volumes and their capacities. I thought I may be able to see them with the live CD, but it just shows the whole HDD as 149GB of unallocated space. Most of the options in Gparted are greyed out for me.. I saw a screenshot earlier which looks just like how Gparted looks like on my machine. I'll try and find it again.

I want to reclaim the ubuntu partitions and use them again, but I seem unable to do anything with Gparted.

Hope that's clearer.

EDIT: Found that link. [This]("http://ubuntuforums.org/showthread.php?t=657584&highlight=unallocated") is what Gparted looks like on my machine.

---

### Post by Annigma on 2008-08-01
Well I found a little program called Testdisk and was careful not to do anything but analyse.... till I got a bit impatient and allowed it to do 'something' to my boot partition.. oops. Now there seeems to be only about 2 gigs of anything on my HD.. can't load windows.. Ubuntu still 'sees' mostly unallocates space, apart from the ~2 GB that Testdisk kindly 'fixed' for me.. :oops:

Gladly, just before I made this monumental 'male-chicken-up' I downloaded Acronis True Image 10 and copied the image of my main drive to my Maxtor external HD. Not quite sure how I'll turn that back into a workable system, but I will.. after much reading, tearing out of hair and general stressing! :lol:

This looks like my own personal error diary thread, but that's okay. At least I can keep track of myself!

:biggrin:

---

### Post by Pumalite on 2008-08-01
Get Gparted Live CD. Burn the iso to disk and boot from it. Delete everything in your drive and make new partitions as you need them. You will need a first partition at the beginning of the drive for your Windows image formatted ntfs.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by Annigma on 2008-08-02
Thank you. I'm still at the 'hoping to recover' stage at the moment, but I'll take a look at that.

---

### Post by Herman on 2008-08-02
There are very good illustrated instructions about how to use TestDisk in TestDisk's own web site, [COLOR=#C0C0C0][TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk")[/COLOR]
I also have illustrated a couple of my own experiences with the use of TestDisk to help those of us who aren't experienced with it yet, here, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").
In my opinion, TestDisk is the best program for fixing your partition table, I have had very good results every time I have used TestDisk.

Regards, Herman :)

---

### Post by Annigma on 2008-08-02
Thanks Herman. That (yours I think) was the site I used to 'break' things :P

I guess it's my fault for not following it properly, but it did say that if I was trying to overwrite any data it would come up in red telling me so: it didn't, so I executed it and.. POOF :(

Anyway, I've somehow managed to add testdisk using Synaptic - I'm using the Live Hardy CD which is the only thing I can get to work atm (I could have used XP to reinstall windows but I want to try and fix my mistakes if possible).

It's searched for partitions and is showing me my six partitions, all of which have 'D' in front of them... :eek:

Am I being paranoid in not wanting to show exactly what my partitions are/where they are/what they're called etc..? If so, I'll try and put a screenie up of what it's showing, to see if that helps anyone to help me...

:)

EDIT: I think I 'just' need to change the D's to *,P,L,or E's but I'm too scared to.. plus, I'm not sure which.. I think I had 3 Primaries, one of which was the *boot, the other two being XP and Linux..? then the others were L's... but... *shrug*. The cylinders look 'right' to my untrained eye (one ends 23, the next starts 24 for example..) but I'm kind of scrabbling around in the dark really..

---

### Post by Annigma on 2008-08-02
[IMG]http://www.pix8.net/pro/pic.php?u=192330YvJo&i=1110824[/IMG]

:confused: :cry:

---

### Post by Annigma on 2008-08-02
[IMG]http://www.pix8.net/pro/pic.php?u=192330YvJo&i=1110823[/IMG]

They're all D's disappearing off the left side of the page next to the partition types.

---

### Post by Annigma on 2008-08-02
Figured it out :D

---

### Post by Herman on 2008-08-02
> Thanks Herman. That (yours I think) was the site I used to 'break' things :P
I guess it's my fault for not following it properly, but it did say that if I was trying to overwrite any data it would come up in red telling me so: it didn't, so I executed it and.. POOF :sad:Thank you for your comments, I'll take a look over that page and think about how I can try to explain what to do more clearly and try to make it easier to understand for other people in the future. It's rare to have partition table problems, so most people using TestDisk will be using it for the first time. Trying to learn how to use a program we're not familiar with can add extra stress to an already stressful situation.
> Figured it out :grin::) Okay, that's good. I am just waking up... (sipping coffee). Sorry I missed the opportunity to help you earlier. 
Congratulations for working it out yourself! Well done! :guitar:

---

### Post by Annigma on 2008-08-19
Hi again :)

I wanted to post this a while back but there seemed to be something wrong with pix8, the image storage I used. The pix8 homepage has changed now and advertises payment subscription. Strangely enough, I seem unable to upload images to my free account now..:rolleyes:

Anyway, I would like to have another go at installing Ubuntu, even though my OH keeps saying, "If it ain't broke, don't fix it" but don't fancy the results I had last time..

Here's what testdisk came out like last time I tried it:

[[IMG]http://img516.imageshack.us/img516/8017/testdiskdeepsearchfl1.th.jpg[/IMG]](http://img516.imageshack.us/my.php?image=testdiskdeepsearchfl1.jpg)

I would greatly appreciate any help with getting my dual boot back..

Thanks in advance.

---

### Post by Herman on 2008-08-25
:) I'm not really sure what you're asking. I think I understand that you have successfully repaired your partition table with TestDisk and recovered you old Feisty Fawn and you are asking if it's safe to wipe out Feisty Fawn and install Ubuntu 8.10 in it's place.

You really shouldn't be anything to worry about if you have a backup of all your data. 

I'm not certain how partition tables get corrupted, but I have a suspicion it's more likely to happen when we keep changing partition editors. 
I always prefer to stick with good Parted based partitioners and I never have any problems. Parted, QTParted, GParted, Partman, and Parted Magic are all good Parted based partitioning programs.

Just always make a backup of all your data before editing your partition table. :)

Regards, Herman :)

---

### Post by Annigma on 2008-08-27
No, I don't have any form of Linux running at all. I've got XP back and it's all fine and dandy, but Ubuntu doesn't seem to be there at all.. I certainly don't know how to run it if it is. Although, testdisk looks like it can 'see' it, but it looks deleted..? I don't really understand it; that's my problem.

The only partition editor I've used is the one that was on the Feisty Fawn CD, which seemed to do a grand job back then. 

Maybe I'll try running the Hardy CD again and see what it does.

Thanks for your reply :)

---

### Post by Herman on 2008-08-27
:) Just undelete it then.
Read the sign; 
> Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted                       
Keys A: add partition, L: load backup, T: change type, P: list files,
            Enter: to continue:) So you just scroll down, highlight your Ubuntu partitions and mark then with an 'L', including your swap areas too.

You might also need to re-select some of your other partitions.
You will probably need your Windows recovery and Windows partitions to be primary, because Windows isn't able to boot in a logical partition easily, so make sure those are marked 'P'.
Data partitions can either be marked with a 'P' or and 'L', but an 'L' is probably better. We can only have three primary partitions plus a number of logical partitions or four primary partitions and no more. Therefore the other partitions can be logical ones, that should be the easiest way to go.

If you had files in Feisty, you will be able to recover them all after you restore the partition with TestDisk.
You can even recover just one partition temporarily just to rescue files and then delete it again and restore other partitions instead if you need to because of partition table limitations.
I recommend Hardy Heron, it's much better than Feisty. If you didn't have any files to recover, or if your files are all backed up, then don't bother recovering Feisty, just install Hardy.  :)

---

