---
title: "Borked up a Gutsy dual-boot install. Need help."
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by bg1256 on 2007-10-28
I have been dual-booting my desktop since Dapper, and I finally got a nice, fast download of the Gutsy CD today.

I was going to do a clean install of Gusty after making some adjustments to my partition table.

So, I booted up the Livd CD, deleted my former /home and / partitions and attempted to make two new partitions out of the old space. Gparted saw my windows partition at this point, and all seemed to be going according to plan.

However, I did not like the changes that I was about to make, so I undid the changes and had the following partition table:

Windows sda1 50 GB

unallocated space 199 GB

swap 1 GB


Strangely, though, Gparted suddenly unmounted my windows volume, and I have not been able to get it to "see" it again.  I have dl'd the gparted live cd and tried that way.  I have downloaded the super grub disk to erase Grub and make windows the only OS again. But nothing seems to work.

When I attempt to set up a partition table using the Live CD or any other method, it only recognizes my entire disc as unallocated space.

I do not want to start from scratch with windows; I would like to leave that where it is and use the remaining 200 GB's for Ubuntu.

Is there any method I can use to mount my Windows drive while using the Live CD?  Would that help me get through the installation without compromising the Windows partition?

Thanks!

Edit: it occurs to me that I might be able to do this from within my windows OS - that is currently working. However, as of now, Windows is not even seeing the unallocated space. Is there a way to make Windows recognize it? If there is, I could simply format it as NTFS and then reformat it using the Live CD... just a thought.

---

### Post by Herman on 2007-10-29
Hello bg1256,
You asked,
> Is there any method I can use to mount my Windows drive while using the Live CD? Would that help me get through the installation without compromising the Windows partition?
 First, you should not be making any changes to mounted file systems (partitions). Always unmount file systems before doing any work on them. 
I wouldn't recommend performing a Ubuntu installation with your Windows file system mounted at all. I can't imagine how it would help and it even might 'bork' it worse.

The only reason you might want to mount them is if you want to copy files to or from them, for example to make a backup. It is a good idea to ALWAYS make a backup of all your files, or if that's not possible, at least all of your most important ones that you can before touching you hard disk with any disk partitioner. 
If you can still boot Windows, then boot it and bacck up your files.
If you can't boot Windows, you can use the Ubuntu Live CD for that, here is a link to my page about that, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm"). 
Try reading that a little first and give it a try, I'm not sure if it will work or not, but if you can, the first job should be to rescue your files, you may be able to back up to a USB disk or another computer connected by an ethernet connection, (unless of course you already have made a full back-up).
If you try mounting and you can't, skip it and proceed to the next step, and keep your fingers crossed.

That out of the way, I am pleased to read that you have downloaded GParted LiveCD because that has TestDisk in it, which you should be able to use to fix your partition table.
Here's my link about that, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")  Using TestDisk to Recover from partitioning disasters demonstrated
              [CENTER](Edited on Friday the 13th!)
[LEFT]
I hope those two links will be explained well enough already for you to understand without too much trouble, but please feel welcome to ask any questions you may have and I or someone here will try to help you as best we can.

Good luck with it, I think TestDisk will fix it for you.
Regards, Herman
[/LEFT]
[/CENTER]

---

### Post by bg1256 on 2007-10-29
Thanks for the information and linking to the TestDisk page.

The first thing I am going to try to do (Based on info from a Windows-genius friend of mine) is to boot into XP and see if I can use the disk utilities there to recover the unallocated space and merge it with my existing partition.

If I can do that, it seems that the Live CD would recognize the entire ntfs partition. If it does, I can simply resize and go from there like normal.

Does that sound like it would work? I won't get back to that machine until later tonight (8-9 hours).

---

### Post by Herman on 2007-10-29
Well I have had a bad experience one time with Windows XP's disk management utilities and Linux experts say never to touch any hard disk with them that you want to use for Linux.

I have had good experiences with GParted and TestDisk, which are compatible with both Windows and Linux. I have used GParted since the alpha 3 version and never had a problem with it. I have used TestDisk to successfully recover an operating system of my own and all it's data even after new operating systems had been installed in the disk, (but at a different start point to the one that was rescued, so the vital file system start blocks didn't happen to get over-written). TestDisk found and recovered it even after it had been deleted for well over a year.
I have also helped someone else recover a deleted Windows XP already, that was why I made the web page about that.

Do as you like though.
I guess it's a matter of opinion whether you want to put your faith in Windows or Linux software. It's up to you. I know which one I trust the most.

As long as you have your data backed up it doesn't really matter anyway, you can always just set a new disk label and re-install from scratch if you need to.

Good luck no matter what you decide. :)

Regards, Herman  :)

---

### Post by bg1256 on 2007-10-29
Thanks for your help, Herman.

I bookmarked the links for future use, but for now, I'm going ahead with a complete reformat.  The only thing I'll have to do is reinstall my games.  It will take time, but I haven't lost data at least.

I think I must have messed with something in Windows as well, because I cannot connect to teh internet from that computer anymore.  Ah well.  Live and learn.  I'll never make that mistake again.

---

### Post by Herman on 2007-10-29
Okay. 
A good clean re-install always does Windows a lot of good anyway, I suppose. I used to re-install Windows a lot when I used to use it. It's just time consuming, that's all. If you know how to back it up and restore it you can get everything back exactly like it was before only better.

Hey, if you want, just out of curiosity, if you have time and you don't mind, can you do '[FONT=Bitstream Vera Sans Mono]sudo dd if=/dev/hda count=1 | hexdump -C'?
[/FONT]```
sudo dd if=/dev/hda count=1 | hexdump -C
```Where: hda is your first hard disk (IDE), replace with sda if you have a SATA disk.
It might be interesting if you can post a copy of the output from that command here. That should show you a look at your MBR in hexadecimal form and if someone has time they might be able to decode it and see what exactly is wrong with it. (Just for fun).

These days it's normally safe and simple to do pretty much anything we like with partition editing programs.  A little spec of dirt on the lens of an optical drive is all it takes to cause a partitioning disaster though.
I'm not sure, but I also suspect that different partition editors might have slightly different ways of working out the fake disc geometry of certain hard disks too.
Fortunately, partition table problems a rare nowadays, but it's still a good rule to make a backup before using any disc partitioner.  Chances are it'll never happen to you again though. I wouldn't let it put me off doing what I want if I were you. Just take the proper precautions and even if the worst happens, nothing can really hurt you.

[FONT=Bitstream Vera Sans Mono] Regards, Herman  :)
[/FONT]

---

