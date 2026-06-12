---
title: "Dual-boot partition when there's C: and D: already"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by nickthedart on 2006-10-14
Hello,
  I've used Linux/Ubuntu before but now want to for the first time set up dual boot with Windows. I'm clueless about partitioning.

My Acer Aspire 3634 came with its 80Gb disk divided already into 2 35Gb partitions - C:\ or "Acer" containing Windows, and D:\ or "AcerData", currently empty . Presumably the other 10Gb is used somewhere else.

My question is what will happen if I let Ubuntu installer resize the Windows partition automatically? I don't want to just try it for fear of breaking something or ending up with it configured unhelpfully and not easy to get out of it.

If Ubuntu "resizes the Windows partition", does that mean -
1. Ubuntu resizes C: and squeezes Ubuntu in there too, leaving two OSs in 35Gb with another 35Gb left unhelpfully empty on D:  ?
or
2. Ubuntu tries to resize the whole disk, messing up Windows' idea of C: and D: and confusing Windows when it tries to start up?
or
3 Something else. ;-)

I'm trying to do this the simplest way possible since trying to learn about partitioning all at once seems like it could lead to errors , breaking Windows etc.

Any helpful info from people who've dealt with a similar situation?

Thanks a lot
Nick

PS This seems like a FAQ but I couldn't find a FAQ about it.

---

### Post by Sef on 2006-10-14
I know there is an option for using an empty partition.  I would use that one. Never have tried it as I manually partition my hard drive.

For an excellent tutorial on dual booting, [click here.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by nickthedart on 2006-10-14
Sef,
  Thanks for the info. I think I might bite the bullet and learn all about manaul partitioning, trying not to break Windows in the process.
Nick

---

### Post by Sef on 2006-10-14
To dual boot, check out this tutorial on [dual booting.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by louieb on 2006-10-14
Where did you get your partition information? 
I would be interested in what it shows when in XP you right click on my computer > manage > disk management. If that shows you indeed have 10 gig of contiguous space unused somewhere That is more that enough by 3 times for a Ubuntu install. If I remember right there is an option to have the installer use the largest free space. If that option is available use it and it should leave your windows partitions alone. I say should but I have never used it. If it were me I would use the manual partitioning. You can at least look at the screen and try it out without actually changing your  hard drive.   	

I don't like changing partition size.  If you feel brave and have done a backup or don't have any important data on the drive, choose the manual partitioning. That way you can shrink your D. You said it did not have anything in it. At the bottom of the partitioning screen there is a note to create two  partitions. One for the install and one for swap. You are in luck because you are allowed to create up to four primary partitions on a hard drive.   And I don't want to try and explain extended and logical partitions.
So at this point use the free space to create two primary partitions. 
One for swap 1\2 gig to a gig is plenty.
One for the install aka / aka root partition. Just use the rest 4 gig min.  
Now is the time of truth. You haven't done anything yet. If it look alright apply the changes and go on with the install.  if not just cancel out and think about it some more. or just blow it off.

---

### Post by Herman on 2006-10-14
> My Acer Aspire 3634 came with its 80Gb disk divided already into 2 35Gb partitions - C:\ or "Acer" containing Windows, and D:\ or "AcerData", currently empty . Presumably the other 10Gb is used somewhere else. If a hard disk manufacturer is selling a hard disk that has a capacity of 80000000000 bytes, they figure 1000 bytes as a kilobyte, 1000 kilobytes as a megabyte, and 1000 megabytes as a gigabyte.  So 80000000000 /1000/1000/1000 = 80 GB. 

Once the hard disk is ready to be partitioned in your computer, it shrinks!

Well, not really, but according to most disk partitioning software, one kilobyte is actually 1024 bytes, one megabyte is 1024 kilogytes, and one gigabyte is 1024 megabytes.
So, in reality, one GB is 1024x1024x1024=1073741824 bytes.

When you divde 80 GB by 10.73741824, you only end up with a 74 1/2 GB drive.
Fdisk shows my 80.0 GB hard disk an 80.0 GB one, but in GParted it's only a 74 1/2 GB hard disk.
That might account for some of your missing GB's, but I don't know what happened to the rest of them.

---

### Post by gn2 on 2006-10-14
> **nickthedart said:**
> Hello,
  I've used Linux/Ubuntu before but now want to for the first time set up dual boot with Windows. I'm clueless about partitioning.

My Acer Aspire 3634 came with its 80Gb disk divided already into 2 35Gb partitions - C:\ or "Acer" containing Windows, and D:\ or "AcerData", currently empty . Presumably the other 10Gb is used somewhere else.

My question is what will happen if I let Ubuntu installer resize the Windows partition automatically? I don't want to just try it for fear of breaking something or ending up with it configured unhelpfully and not easy to get out of it.

If Ubuntu "resizes the Windows partition", does that mean -
1. Ubuntu resizes C: and squeezes Ubuntu in there too, leaving two OSs in 35Gb with another 35Gb left unhelpfully empty on D:  ?
or
2. Ubuntu tries to resize the whole disk, messing up Windows' idea of C: and D: and confusing Windows when it tries to start up?
or
3 Something else. ;-)

I'm trying to do this the simplest way possible since trying to learn about partitioning all at once seems like it could lead to errors , breaking Windows etc.

Any helpful info from people who've dealt with a similar situation?

Thanks a lot
Nick

PS This seems like a FAQ but I couldn't find a FAQ about it.


If you didn't get install CD's, chances are the missing Gb's are a hidden partition with the OS on it.

Many PC suppliers do it this way with the option to create restore discs at first (or subsequent) boot.

I would advise you do not delete it unless you want to pay out for a Windows disc. 

Also if dual booting on one hard drive, I strongly recommend you do not install Grub over the Windows Master Boot Record. Sadly this is the method recommended by many Ubuntu-ers, and it's a potential minefield......

---

### Post by Herman on 2006-10-14
> My Acer Aspire 3634 came with its 80Gb disk divided already into 2 35Gb partitions - C:\ or "Acer" containing Windows, and D:\ or "AcerData", currently empty . Presumably the other 10Gb is used somewhere else.

My question is what will happen if I let Ubuntu installer resize the Windows partition automatically? I don't want to just try it for fear of breaking something or ending up with it configured unhelpfully and not easy to get out of it.

If Ubuntu "resizes the Windows partition", does that mean -
1. Ubuntu resizes C: and squeezes Ubuntu in there too, leaving two OSs in 35Gb with another 35Gb left unhelpfully empty on D:  ?
or
2. Ubuntu tries to resize the whole disk, messing up Windows' idea of C: and D: and confusing Windows when it tries to start up?
or
3 Something else. :wink: If you just let the Ubuntu installer resize the Windows partition automatically, I don't know, I have never done that with the 'Desktop Live/Install CD', I always choose manual partitioning. Here's aysiu's website about the Desktop CD, [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
If it's anything like the equivalent option in the 'Alternate Install CD', then you will still be given an opportunity to set your partition size for Windows manually, which iwill be at least big enough for Windows and all its data. The automatic part is when the installer will automatically partition the remaining free space with one '/' (root) partition plus one swap area, whose size is automatically determined.  That will leave you with both operating systems squeezed into 35 GB, with an empty 35 GB partition left over.

It would be far better for you to select 'Manual Partitioning', and select your 35 GB empty partition and chop between 1/2 and 1.0 GB off for the swap area, format the rest as ext3 for '/' (root), and let the installer go on that. Then you will have Windows on one 35 GB partition, Ubuntu on 34 or so, and 1.0 GB or less swap area. That would be a good partitioning arrangement.

Nowadays, it isn't as important to decide how to apportion our disk partitions anymore. If you need to change their sizes later, you just use the latest GParted LiveCD to do anything you like with your partitions. Link: [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")

Likewise, if you have a Super Grub Disk, grub problems, if they do occur, are much easier to cope with and fix than they used to be. link: [Super Grub Disk : En]("http://adrian15.raulete.net/grub/tiki-index.php")

I have always had single hard disk computers until recently, and I added and extra disk to one just for playing with bootloaders. I have Grub installed to MBR on both disks.  I have never had a grub problem in hundreds of test installs, on several computers. I recommend Grub to everyone. Grub is great! :D   But it's easy to write the Windows bootloader anywhere too, or  [GAG Boot Manager]("http://gag.sourceforge.net/"), or Lilo. Bootloaders are really not a worry. They're fun.   Just use one, then overwrite it with another, use that for a while, over write your MBR with another one...

I mean really...! :-D
here's some information on bootloaders in case you're worried about that, I know I'm certianly not, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm") |  [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") | [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm") | [MBR Page]("http://users.bigpond.net.au/hermanzone/p6.htm") | [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
But, you'll never need to know any of that. Just install Ubuntu and don't worry, have fun! :D

Regards, Herman  :D

---

### Post by gn2 on 2006-10-15
> **Herman said:**
>  Bootloaders are really not a worry. They're fun.   Just use one, then overwrite it with another, use that for a while, over write your MBR with another one...


Obviously you haven't been keeping up with things in the Absolute beginners forum, where there are numerous posts from people having problems of various kinds.

Why recommend trashing someone's Windows install when it just isn't necessary?

Windows on one drive with it's own MBR, Ubuntu & Grub on another drive.

It's the easiest and safest way.

---

### Post by Herman on 2006-10-15
>  Why recommend trashing someone's Windows install when it just isn't necessary? Grub doesn't touch anyone's Windows install. :D

---

### Post by nickthedart on 2006-10-15
Hello guys,
  Thank you all for helpful & intelligent suggestions.

Just to clarify, this £400 (i.e close to bottom end) Acer laptop came with no Windows disc. I just have the recovery disk that the manual instructed to make, and don't really want to have to use it. ;-)

AFAIK it does NOT have 2 disks, just 1 pre-configured into 2 partitions.

The real reason for my tentativeness here is to keep Windows intact. 

(An aside: Yes its not good having to spend time on Ubuntu forum trying to avoid breaking Windows. OTOH we won't convert the world to Linux-only just yet, but we might convert the world to dual-boot if we help Ubuntu co-exist even more peacefully with Windows)

I tried out the installer just now and it didn't actually give an option
to automatically resize the partitions. Just erase whole thing or manually edit. So I went to manual edit, and it said :

                            Used  Free  Flags
/dev/hda1   Fat32   3.90Gb  2.75Gb 1.15Gb -
/dev/hda2 ! Fat32   35Gb      -    -    boot lba
/dev/hda3   Fat32   35Gb    31Mb   35Gb   lba  



I was surprised to see Fat32 as I thought that was on older pre-XP machines. Is the installer confused?

The /dev/hda2 in fact had a warning triangle where I put the ! above.
Is that code for "this is your current boot partition, careful before messing with it" ? or is it "I can't figure out what this is" ?

Can anyone confirm whether its /dev/hda3 or /dev/hda2 , which is the empty one I can put ubuntu on?

Why does it not say how much space is used on /dev/hda2?
What's the difference between boot lba and lba?

Apologies for my cowardly tentative approach to this! Normally I would just experiment with stuff. The problem is the devastating consequences of breaking Windows. One reason I am scared of trying to fix Windows is my complete ignorance in that area as result of spending all my efforts on learning about Linux. ;-)

Cheers
Nick

---

### Post by Herman on 2006-10-15
Well I use all Acer computers myself, and I'm typing to you now on an Acer laptop. But I had already a good knowledge of how to use the Recovery disks and how to back up and re-install Windows and all its installed software and data before I began installing Ubuntu.

Well, actually, the first time I installed Ubuntu it didn't matter, because it was on an older computer in which the Windows 98 install was destroyed anyway, by viruses and malware, and there was no Windows disk. Ubuntu Warty edition completely fixed it and made it run better than it ever did under Windows.

But before I installed Ubuntu in my good computers, (Acer), I knew how to re-install Windows and all data. I think that you would be right to be cautious if you don't feel certain you can restore the computer if something goes wrong. You should probably stick to the LiveCD for a while longer. 

You should be able to find out somehow if your Windows Xp is on FAT32 or NTFS. All my Windows XP Home Editions are on FAT32. It's actually much better for a dual boot computer, as Ubuntu will be able to write directly to your files in Windows. I am pretty sure you just click on 'My Computer', and rightclick 'Drive C', and look at 'Properties' to see see if you have the FAT32 filesystem or not.

Restoring Windows with the Acer Recovery CD is actually very simple. Learning how to back up things like your email in Windows and your files and settings and other things like that are the things that take some learning. There are websites that explain all the steps about how to do that. You should learn how to do that anyway, because sooner or later you will want to re-install Windows when it starts to slow down because it accumulates all kinds of malware and rubbish.
Ironically, once you begin to dual boot, and keep Windows off the internet, you will find that all your scans in Windows will begin to come up clean. Therefore, you will no longer ever need to re-install Windows again. However, you should be proficient enough first to know how to do that before you try to install Linux. Unless you can get help from a freind who can attend.

I'm not too sure what the triangle means in the 'Desktop' GParted installer.I haven't got one of those in my GParted. I think it's a bad sign, I don't like the sounds of it. Can you get a screencap of that with the LiveCD and post it so we can take a look? 
Then someone can probably help you better. It should be easy enough to see which partition is empty by the lack of a colored section, like a bar graph in it representing the area filled with data.

Regards, Herman :D

---

### Post by gn2 on 2006-10-15
> **Herman said:**
> Grub doesn't touch anyone's Windows install. :D

Are you sure? Here's someone who can no longer boot Windows because of Grub problems.
[http://www.ubuntuforums.org/showthread.php?t=277846](http://www.ubuntuforums.org/showthread.php?t=277846)
I would contest that the MBR is part of the Windows install, and Grub will trash it if you follow the recommended Ubuntu dual-boot solution.
Fixmbr doesn't always work.....

Even after the poster gets fixed up, he will continue to have problems every time he has to re-install Windows, or when there's a kernel update.

That's just a ramdom sample, there's plenty more if you look.

Grub on the MBR was worse than any virus I ever had.

---

### Post by nickthedart on 2006-10-15
Herman,
  Ta 4 the reply. I've attached the screenshot of the partition manager screen. Your suggestion to right-click on properties in Windows does confirm that XP thinks its FAT32. XP only mentions the two ~35Gb partitions, not the 3.9GB partition that Ubuntu finds. 
  Yeah I know Acer are a decent make. Its just this was almost their cheapest model so they might've cut a few corners. For example its only really got 448Mb RAM when you consider the graphics card takes 64Mb, and its a crippled Celeron etc.
  Thanks for the reassurance about the recovery CD. Probably I'm irrationally fearful of something that not hard at all to fix. BTW I don't have too many problems with Windows (famous last words) 'cos I've got service pack 2, don't normally log on as administrator, and I use Firefox. I totally agree it all runs better under Linux. However, on Ubuntu, the following don't run out of the box : Watching DVDs, listening to radio over the 'net, burning CDs, running software thats written for Windows (Wine still in an unstable state). Hence the need for dual-boot.
  I'm tempted towards putting Ubuntu on the hda3 which looks like the empty one, and have the recovery disk to hand if it does blow up Windows.
Cheers
Nick

---

### Post by nickthedart on 2006-10-15
gn2 - thanks for your helpful comments too.

Really its dead simple - Windows has partitioned my disk into 3 - a 3.9Gb, and 2 35Gb s. I just want to make sure I stick Ubuntu on the empty D:\ partition and not break Windows, but I can't tell right now which one is which, and am scared by this warning triangle. Herman is probably right. Also maybe breaking Windows and recovering with the disk is good educatin for me anyway and then I could experiment more confidently.... ;-)

---

### Post by gn2 on 2006-10-15
> **nickthedart said:**
> gn2 - thanks for your helpful comments too.

Really its dead simple - Windows has partitioned my disk into 3 - a 3.9Gb, and 2 35Gb s. I just want to make sure I stick Ubuntu on the empty D:\ partition and not break Windows, but I can't tell right now which one is which, and am scared by this warning triangle. Herman is probably right. Also maybe breaking Windows and recovering with the disk is good educatin for me anyway and then I could experiment more confidently.... ;-)

Just be advised that there are potential hazads to running Grub in the MBR.

Just do plenty reading up, and be aware that it doesn't always go smoothly.

The choice is yours...

---

### Post by Herman on 2006-10-15
Well nickthedart,* It looks to me *as if your laptop has Windows squeezed into your hda1 partition, looking at the way that one is almost full of color and the  other two are blank.
I'm not sure about what the triangle means, but I suspect it just means that no mount point has been selected yet for the partition. If you look in here, link: [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html), in the illustration for step 5 of 6, you can see a similar looking triangle, but in a different place, and that's what it means.  It could have something to do with the boot flag being on that partition. If that partition doesn't contain an operating system, I don't know why the boot flag would be on that one though.
Perhaps you should boot Windows again, and go into 'My Computer', and have a look if you have two extra disks showing in there, and open them and check whether they are both empty or not first.
You resize them them each to about half their present size, then make an extended partition for Ubuntu, and install Ubuntu in a logical partition. That should be the safest approach if you're not sure. 

I'm sorry, but it's Monday morning and I'm out of time, I have to go to work now, I'll be back. Read aysiu's website on the installer/partitioner you're planning to use, and read mine for answers about bootloaders. You can back up your MBR or use GAG boot manager, etc, have to run, bye for now, Herman :D

---

### Post by nickthedart on 2006-10-15
Herman - I've now got it working thank you. Your help was awesome. :-) I just needed someone to say that using a Windows recovery disk on an Acer machine wasn't the end of the world, so I plucked up courage and messed about with the partitions.

In fact, the hda2 with the triangle, which is C:\  (Windows is squashed in the tiny partition at the beginning),  wouldn't let me resize it anyway.

So I eventually just resized hda3 down to about 3Gb , leaving 32Gb for Ubuntu. This took a few attempts, for some reason it wouldn't play with FAT32 so in the end I used Ext3 . At one point I had Ubuntu installed with a horribly messed-up partition and "df" saying the disk was 90% full when it wasn't. ;-) But the second install worked fine and now both Windows and Ubuntu work fine via GRUB.

Truly dual-boot is the best of all worlds. All the advantages of Linux without being isolated from the unfortunate people making up the rest of the world.

Your webpages about this are great.

Partitioning is an important subject. I think it could be the biggest stumbling-block for Linux newbies. If they want to go beyond using a live CD but are scared of breaking windows they may well grind to a halt like I did. Ironically its perhaps lack of knowledge about Windows, rather than lack of knowledge about Linux that is the problem here.

---

### Post by Herman on 2006-10-16
Hello nickthedart, I'm happy to read that it all went well for you. Congratulations ! :D

To use the Acer recovery disk, with the ones I have it's just a matter of typing 'y' three times and feeding the computer some CDs and waiting. Then there are lots more CDs for apps. 

Just to clarify, the site I linked you to in my last post was part of aysiu's, here's a link to another part of it that you might find useful now that you have installed Ubuntu okay.  [COLOR=#3333ff][http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) [COLOR=Black]aysiu's site is a big help to anyone, especially those who are new to Ubuntu and Linux.

My own site, [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) is mainly about the old original installer and partitioner, (not the one you used). But I have added a lot of information about bootloaders there as well, and a few other assorted bits and pieces to try to help people. You probably won't need any of that.

I agree with you, partitioning would seem rather a challenge for anyone who has never done it before. It's wise to read up all we can before we do anything. The only way to really learn is to take the plunge though. Well done and welcome to Ubuntu! :D

Regards, Herman :D

[/COLOR] [/COLOR]

---

### Post by eeried on 2006-11-10
nickthedart says
> Watching DVDs, listening to radio over the 'net, burning CDs, not out of the box -> I keep Windows:

Oh this sounds to me as no good reason or reasoning. You can burn CDs out of the box with Ubuntu. Watching DVDs takes seconds (who's fault is it if many DVS are crypted. Some DRM-affected DVDs may not be burned at all even under Windows).
Listening to the radio takes a few seconds -- install Mplayer + mplayer plugin for Mozilla: this works on most radios (not the BBC who demands realplayer10 but why not complain to the BBC?). Using WMP is allowing M$ to put a spy on your computer.

> but we might convert the world to dual-boot if we help Ubuntu co-exist even more peacefully with Windows)
I'd say Windows could make an effort to co-exist with other systems. And I hope people will choose Linux on its own when there's no good reason to keep Windows.

Finally making an effort to use libre software and be free is a good thing. Many people do make an effort to get pirated versions of, or or crack, photoshop and what's not, don't they?

---

