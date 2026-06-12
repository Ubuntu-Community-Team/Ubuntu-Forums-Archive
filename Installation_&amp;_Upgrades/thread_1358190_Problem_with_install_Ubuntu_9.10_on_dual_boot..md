---
title: "Problem with install Ubuntu 9.10 on dual boot."
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Iwillsurvive on 2009-12-18
Want to install Ubuntu 9.10  want to use seperate partition when the partition manager comes up I get the partition as  what file

Fat 16, Fat32 Ext2 file system, ntfs etc. do not know what file system to partion as.

Do want to use side by side install method because once partion is made it is undoable..

I tried the install in windows but got a error message after install was done. Not sure if it is because I am using Win XP 32 bit and trying to install Ubuntu 64 bit or because I have
Virtual box and Ubuntu 32 bit on C: drive.

I prefer seperated partitions anyway.  What File system is Ubuntu partioned as?







                                              Sign

                                               Iwillsurvive

---

### Post by gs777 on 2009-12-18
You should use ext3, or ext4 as root partion for ubuntu.

---

### Post by guvnr on 2009-12-18
ext4.

even better, create at least one other and in the dropdown that gives a bunch of folder options, choose ..

/home

.. then you can always keep your data safe if there's a problem down the road (next time you choose the same partition again for /home BUT just don't click the format option)

you know, partitioning is pretty key.  if it's an important machine it's worth googling up on that.  here's a start ...

[HOW-TO Install/ Partition Ubuntu 9.10 [ KARMIC KOALA BIBLE #4] - GUVNR](http://guvnr.com/pc/karmic-install-tutorial/)

one other tip .. if you want a Wins dual boot, install windows first, then Linux, to preserve that grub menu thing that pops up when you boot, offering OS choice.  there are workarounds but this is easier.

---

### Post by Iwillsurvive on 2009-12-18
Thanks for the link.


I am recieving this error

No Root File System Defined
Please correct this from the partitioning menu

the partition I wanted to use is Ntfs tried to partition it put  in Ext4  Mount point /home Recieved Error above.  
Tried to delete and partion over still recieved error above

I used Ext4 Mount point /Home in 
every scenario possible and still recieved same error code.

What could be  wrong ?

---

### Post by darkod on 2009-12-18
> **Iwillsurvive said:**
> Thanks for the link.


I am recieving this error

No Root File System Defined
Please correct this from the partitioning menu

the partition I wanted to use is Ntfs tried to partition it put  in Ext4  Mount point /home Recieved Error above.  
Tried to delete and partion over still recieved error above

I used Ext4 Mount point /Home in 
every scenario possible and still recieved same error code.

What could be  wrong ?

You can NOT use ntfs partition for ubuntu. And also have in mind that any change you make to the partitions in the installer are not executed until the install actually starts after step 7. Sometimes this can lead to confusion.
That's why the best thing is NOT TO CREATE partitions for linux from within windows because it can only create them as ntfs. You need to have the space unallocated, not belonging to any partition.
When using manual partitioning during the install it should allow you to delete that ntfs partition and create your ubuntu partitions in that unallocated space as logical partitions.
Also, it seems you are trying to continue with only /home defined, that why the error no root file system defined.
You need a minimum of 2 partitions, / (root) and swap. / is like C: in windows, the system partition.
/home is not necessary but it can help if reinstalling later, you can keep all your personal data and settings on /home.
So, either delete the ntfs partition and then when installing ubuntu tell it to use Largest Available Free space, in this situation it will create / and swap for you.
Or create them manually if you want separate /home partition, but you need to create 3 partitions, /, /home and swap, not just /home.

---

### Post by guvnr on 2009-12-18
yes Iwillsurvive, do get it together!

I have to say, I remember clearly, frankly, how darn scary that partitioner looks the first time or three, but darkod makes a key point about there being no changes until stage 7.  You can cancel and redo if your installation summary looks somehow wrong.

Definitely a tip for the installer package developers to consider a big splash screen or something explaining that clearly .. maybe the installer does, have used it about 5/6 times this week, can't remember tho!  An explanatory video would be even better, to pop up at partitioner stage.  Now that is noob-friendly.

But don't be put off.  Just be aware.

Right, 2 things:-

[B]1. Plan, have a partition strategy (and clarify the process with examples)
[/B][URL="http://guvnr.com/pc/ubuntu-partition-planning/"]
Plan Hard Drive Partition Strategy [KARMIC KOALA BIBLE #3][/URL]           

[B]2. Do it
[/B]
[HOW-TO Install/Partition Ubuntu 9.10 [KARMIC KOALA BIBLE #4]]("http://guvnr.com/pc/karmic-install-tutorial/")       

And here are the 2 extracts from those guides that you need to read .. the originals are much clearer because the extensive styling I use emphasizes key points and is missing here; there are handy external links; this text is simply lifted and is not properly formatted to read like this; so less chance of a cock up from the original.  Then again, here you go anyhow.  If you're still lacking confidence, I would suggest you read more guides or of course ask more q's.  But really here is the real deal.   Best of luck.  Don't blame me!

[B]1. Plan.
[/B]
[B]Dividing the Hard Drive: Food for Thought
[/B]
Pre-OS-install, mapping out data/system demands for optimal disk segmentation saves headaches down the road. Here's a heads-up to help.

You don't have to, but it is a mighty good idea to put pen to paper, ring-fencing the departmental demands you will have on your overall hard disk, or disks.

For instance, you may require space for:-

    * a boot manager (the first thing on the disk, a few mB)
    * the Karmic Koala operating system
    * your personal documents and settings, which generally are housed in your /home directory
    * another operating system
    * and maybe another again
    * a downloads location
    * a location for your music collection
    * another for your movies
    * and another for pics
    * maybe one for websites/special projects
    * a place for backup, else an image of all the above, ideally on a separate hard drive
    * swap (RAM overflow)
    * you get the idea!

How you divvy up the drive is a personal thing, but split it up you will, easily enough, the key partitions being created during the installation process, else prior to that if you use a tool like GParted.

The only must is for any operating systems to be separated, as should the swap file. Furthermore, backup should be in its own location, ideally not just on a separate partition but on an independent hard drive. It is recommendable also to separate user data, housed in the /home folder, to its own partition.
What is a Partition?

Think of your hard drive as a very solid building. Impermeable walls separate the rooms, or partitions, each with their own purposes. If you set fire to one room, the others will be unnaffected.

It is due to the risk of total disk failure (the building collapses!) that you should store backup on a separate volume altogether.
What is SWAP?

If you run out of RAM, a small slice of your disk is called to temporarily take the slack. With Windows, they call that virtual memory.

At it's barest, IMHO, your partition plan should comprise:-

    * the Karmic Koala operating system
    * another operating system (if you want another)
    * your personal documents and settings (/home) to include all personal media
    * backup, but on a separate hard drive
    * swap (RAM overflow)

.. so, of the primary or only hard drive, you have partitions for each of those sections, with backup on another disk. OK, you don't have another disk and really don't want to buy one? This is not good advice, but you can have backup on another partition on the same drive too, or risk all and don't even backup (that is terrible advice!)

Alternatively, the barest possible would look like this:-

    * the Karmic Koala operating system, including your /home directory
    * another operating system (only if you want another)
    * swap (RAM overflow)

.. so that's two partitions, plus one for each subsequent OS.

If you are considering your first future-proof multi-partition setup, and really want to get it right, I suggest you Google a lot. If you want to share docs between, say, Windows and Linux, there are methods to allow you to do that too, so Google again. (For any Windows system, your personal docs should be on a separate partition too, especially as the damn thing always breaks).
Should I Install a Linux System Before Windows?

To save headaches, no. When Linux installs, it recognises other operating systems and allows you to boot to a choice of those on disk. Windows is less usefully inclined. Install Windows first, then Karmic.
What if I want Karmic as my First Partition?

Good call! In that case, rather than using Ubuntu's Partition Manager to resize and/or segment your disk, download and run GParted from boot. (It's better than anything else I've tried, including Acronis' Disk Director and Partition Magic.) You can resize and even move your Windows' partition, although that can (rarely) lead to you having to reinstall Windows as well.

My advice:-

    * plan your pie
    * back up from existing Windows
    * using GParted, format the entire drive and partition as required
    * install Windows on the second partition, then Linux on the first

But. That's an opinion, and there are many others! Google it to gauge what works for you because there is no right nor wrong, just sometimes poor planning or bad luck.
How Much Space To Allow For Each Partition

Hmmn, for your docs, at least, how long is a piece of string? Then again, so far as Ubuntu is concerned, they say:-

"The [operating system] takes between 3-4gB hard drive space, and 8-10gB will be needed to run comfortably."

.. That doesn't take into account much in the way of personal documents and media, nor additional software installations, so allow for that on top.

Regarding the Linux SWAP size, the jury is permanently out, but it is generally reckoned you should allow for a separate partition of two to three times your hardware's RAM size. I've got 2gB RAM in this laptop, for example, and 4gB SWAP. Is that naughty? Dunno, but it works.
OMG! Just Give Me a Solution, Guv!!

I know, for noobs and even intermediates, this is the hardest bit. That's only because you don't want to cock things up or have to redo. Almost certainly, if you research a bit, you won't cock up, and you won't redo for a good long while. Stay chilled. Have a cup of tea!

Here is a partition suggestion, but merely a suggestion, that allows for Windows (begrudgingly) and backup on a separate disk. It's not ideal, just a basic idea. Like I say, it's a personal thing, and a step that should take you longer to consider than anything else in this guide:-
Partition     gB     File system     Purpose     Notes
1     25     Ext4     Karmic system     
2     30     ntfs     Windows system     begrudgingly!
3     100     Ext4     /home - docs     
4     50     ntfs     Windows docs     can be used by Linux
5     4ish     swap     swap     is shared between Linux systems

If you have extra space, divide it between your Windows and Linux docs partitions, or consider adding additional partitions for a rainy day, else those mp3s.

Then, on a separate drive, divide in two:-
1     big!     Ext4     Linux docs backup     
2     big!     ntfs     Windows data backup     
Allow for Virtual Operating Systems with VirtualBox

One last consideration. In this guide, for those that want to emulate other systems such as Windows or other Linux systems, I'll show you how to add and configure VirtualBox in the imaginatively titled Part 25 - Emulate Virtual OSes with VirtualBox.

In fact, using VirtualBox, you can realistically have a 100% Linux box with a copy of Windows, or whatever system, sitting pretty within.

If you think you may want that option, read Part 25 now so you can best prepare for the extra bulk of those operating systems it allows you to virtualize.

For instance, if you'll be wanting a virtual Windows 7, plus another for, say, OpenSUSE, allow for an extra 25gB for each (to include a bunch of programmes plus rattle space) in your /home directory. Then again, these virtual OSes, undeveloped, will be much smaller at around 10gB each. Just be aware and plan ahead for whatever eventualities are likely to affect you and your biz.


[B]2. Do it!  (Just the Partitioner section of the install process, up till first login.)
[/B]

[B]      OMG! Partitioner .. that's a scary word.
[/B]
      Here's where you divvy up your hard disk/s and, of the installation process, this is where you are most likely scratching your head or, if you have an existing operating system you want to continue to work, you may feel a little concern! Well, we'll just have to get it right then, won't we ;)

      You are provided up to three choices, depending on what's already on the disk:-
          o Install them side by side, choosing between them at startup
          o Erase and use the entire disk
          o Specify partitions manually (advanced)
      Install them side by side, choosing between them at startup

      You're offerred this option if you already have one or more operating system/s on the drive.

      Select this and up pops a box labelled Write previous changes to disk and continue and, if you click Yes (DON'T, yet at least), Ubuntu manages a default configuration to preserve existing operating systems while allocating space from their partitions for Karmic. One Ext4 partition is created for Karmic and another, a swap partition, for swap. If you already have a swap partition (for an existing Linux operating system), that will be used also by Karmic and only the Ext4 partition is created.

      Personally, I don't like this method because it changes existing partitions automatically and I prefer to do that manually, so I know exactly what is going on. Also, I prefer to set up at least one further partition, for my data - /home, and this option doesn't allow for that.

      Then again, it's pretty safe (there is a rare risk of problems with existing operating systems) is faster and is less hassle.
      Erase and use the entire disk

      Clearly the easiest option. Will wipe the disk bare, creating a small SWAP partition and using the rest for Karmic. Again, it will not create a separate partition for data. Not my choice, again.
      Specify partitions manually (advanced)

      OK. This is the best of Ubuntu's options. You have control. And you are paying attention, right?!

      Check the box, click OK (or was that Forward? One of the two.) and Ubuntu again scans your disk (or disks if you have a multi-disk PC).

      The Prepare Disks page opens and you see clearly charted the layout of your disk or disks, together with a partition summary below.

      Study that chart and partition summary carefully, with your partition plan to hand. What, you don't have a partition plan? Oh dear, you've missed a step .. arguably the most important step in the installation process! Go back to Part 3, Plan Hard Drive Partition Strategy, have a think, then come back here.

      Right. You need to take your strategy and compare it with the chart and partition summary on the Prepare Disks page. Basically, you need to consider where on that disk to put what partitions.

      Let's say you've got a typical disk, unchanged from factory install, which comprises one big Windows C drive. Simple, you can shrink it from either end and, with all that freed up space, create whatever new partitions you need.

      Then again, you may have the C, but with a D - maybe your old Windows data drive - alongside. In that case, you could shrink C from the end nearest D, and shrink D from the end nearest C, creating a gap in the middle and, in there, plop in Karmic.

      Alternatively (or as well) you could shrink the far end of the drive, furthest away from your first partition, and have another/some of Karmic's partitions go there. Bear in mind though, just as the innermost part of a wheel spins faster than the outer edge, so the first partition runs faster than the last so, ideally, you'd have your key operating system on the first partition. The swap can be last, at the slow end of the disk, particularly if you have plenty of RAM.
      Some More Partitioning Tips

      Partitions for Music etc Add as many partitions as you want, leaving the mount point (see below) blank. Karmic reads most filesystems. Ext4 is recommended but, for Windows to read the partition, make it ntfs and then partition can be shared between Karmic and Windows.

      Allowing for Windows If you plan to add a Windows system on one of your partitions at a later date, give that an ntfs file system.

      Safeguard /home Allocate this to a partition on a secondary drive and it allows for future upgrades.

      Secure backup folder This should ideally be on a separate drive.

      You get the picture, there are options to consider. The most important one is, did you back up your data, just in case you are somehow unlucky.

      Using this advanced manual method and with your mapped out plan to hand, here are the functions at your disposal to create your ideal setup:-

      New partition table Deletes your existing partitions and everything in them. Choose this is you want to wipe your disk and build a new partition structure entirely. To add a new partition to your new table, click on free space and then on Add.
      Add To utilise, click on free space, then Add. Up pops a box needing some detail:-
          o Select size Clearly the size to make the slice.
          o Use as For Karmic, choose Ext4 for all partitions except for your swap, which requires a swap file system.
          o Mount point What the partition is for. The first available space should be for / (the root of Karmic's system), the next partition for /home (your data), then whatever else you want before the last partition for your swap.

      Click OK to reserve the partition. To add further partitions, click on free space again and repeat as before.
          o Revert If you make a mistake, go back a step.
          o Change To use, click on the partition to change. Up pops a box and you can, for example, change the partition size. You can also change the filesystem, for example, from that of Windows (ntfs, fat32 ..) to that of Linux (Ext4 is best).
      Primary or Logical?

      Doesn't matter. For technical reasons you can only have 4 primary partitions. If you want more partitions, just create three primary's and then create the rest as logical.
      Why Not Use gParted?

      Why not indeed? I do, but more likely I would do so for a complete disk format and new partition table. But Ubuntu's Partition Manager is basically the same anyway and is more user-friendly.

      But sure .. you could set up all your partitions with gParted and then, on installing Ubuntu and coming to the Partition Manager, simply allocate your gParted-created, Karmic-targetted partitions to the new operating system.

    * With your disk space allocated, click Forward.
    * On the Personal Identification screen, add the basic details and click Forward.
    * There's an installation summary on the Ready to install screen ..
    * And an Advanced tab. Most importantly, you can add a network proxy if you like.
    * Back on the Ready to install screen, click Install.
    * Go make a cup of tea.
    * Your partitions will be formatted and Ubuntu installed. I guess you knew that.
    * When the Installation Complete dialogue box pops up, click Restart now.
    * When prompted, remove the disk from the tray and click 'Enter' to reboot.

NB I've noticed that, at least with the final release candidate installation disks, after this stage the computer can hang (likely it's a lack of empathy between the kernel and my HP laptop). If that happens, just do the technical thing: hold dwon the power button, force a shutdown and restart. The good news was that was the only problem I had with the installation process.

    * Up pops Karmic's shiny new login screen (after the boot manager if you have a dual boot machine). Do.

---

### Post by Iwillsurvive on 2009-12-18
Thank you 
i have installed with the side by side method for now its Great 
Guvnr and will try to get it istalled on a seperate partition later.








                                                  Sign

                                                   Iwillsurvive

---

### Post by avtolle on 2009-12-18
If you installed side by side,I believe (never done it myself) that you have separate partitions.

---

### Post by guvnr on 2009-12-19
cool beans Iwillsurvive .. you do indeed have 2 separate partitions by the sound of it.

enjoy m8

---

