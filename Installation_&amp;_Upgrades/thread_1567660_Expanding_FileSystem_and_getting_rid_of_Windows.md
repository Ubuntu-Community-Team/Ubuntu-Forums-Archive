---
title: "Expanding /FileSystem and getting rid of Windows"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by M_Mynaardt on 2010-09-04
Hi there!  Two things, of course, but they're related...

I have two dual boot machines; a desktop and a netbook.  Each have XP and Ubuntu.  I'm just wondering if anyone can tell me how:

1. how can I expand /FileSystem from whatever it is now
   (on an NTFS machine)?

2. later, when I am absolutely positive my valuable data 
   is backed up (at least twice); Can I make my computer an all-Ubuntu
   machine and keep my current Ubuntu desktop as is.

I'm sure these are easy, easy-peasy, for someone out there.  But I would like to give Windows the old heave-ho, but I don't want to do that until I'm sure my data is all safely backed up...

Thanks, all!

---

### Post by Herman on 2010-09-04
You'll need another hard disk or some other media to move all your files to and like you said, probably another one for a backup would be recommended.
Empty all the files out of your Windows NTFS partitions, and also empty most of the files out of Ubuntu.
When you're certain you have all the files you want, go ahead and delete Windows.

Now you'll have a Ubuntu partition somewhere in the middle of your hard drive, and you'll want to move it to the start of your hard drive. It's not easy to 'move' the start point of a Linux file system. 
You can do it with GParted, running in a Live CD, but it takes a long time.  
I you want to use a dd command and make a backup (snapshot) of your operating system as it is now, you can resize the partition (which is now empty of files), with GParted as small as you can and use a dd command to copy it to a file.
Then, you delete the partition from where it is now. You can make an new partition at the start of the hard disk with GParted and use another dd command to restore the operating system from your backup file. 
You can keep the backup file (snapshot) for possible future use. 
Using dd commands is faster than using GParted to 'move' the partition, unless you set GParted to do that overnight while you sleep, plus you have the added bonus of the operating system 'snapshot' file that you can keep.
GParted is safer for those who are not comfortable or confident with using the dd command. 

An alternative method is to use GParted to simply copy and paste the resized (as small as possible) partition around on your hard disk until it is where you want it. In the old days that used to be complicated because the partition number was important, but now that we use UUID numbers in /etc/fstab and in GRUB, you will not need to worry about anything if the partition number gets changed. Just copy the partition with GParted and paste it to the start of your hard drive.

You will probably need to re-install GRUB, so before you do anything make sure you make a GRUB Rescue Disk to reboot with. [How To make Your Own ]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")[GRUB2 Boot CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM") - use grub-mkrescue.

When you are done, resize your partition to occupy the entire disc or whatever portion of it you want.
Then put back all the files you want.

Yet another good way to do things would be to wait until you're ready to install a newer version of Ubuntu and install it in your Windows partition, overwriting Windows. That would be the lazy man's way to do things since all the work will be taken care of by the Ubuntu installer. You won't need to re-install GRUB or do anything very much. Then move your files from your old (present) Ubuntu into the newer one when it and you are ready. Ubuntu is a very easy operating system to backup and restore, or to transfer files and setting from one Ubuntu to another, (to 'walk' yourself forward).
That method would be recommended if you have an older version of Ubuntu like Karmic Koala or older, and you would benefit from upgrading to the current version, ( Lucid Lynx at the time of this post).

There are many more ways you can do it, but those are a few ideas I can think of that I have used myself in the past. If you decide on one of those possible ways to do things and you would like more details, post again and ask for more info and I or someone else here will be able to advise you as needed.

---

### Post by M_Mynaardt on 2010-09-04
> **Herman said:**
> 
You'll need another hard disk or some other media to move all your files to and like you said, probably another one for a backup would be recommended.

etcetera, etcetera...


Okay, thanks, that gives me some idea of what to do.

If I tried another install of Ubuntu (I have version 10.04) from scratch; would that keep the Ubuntu that's already there prim and proper like?

---

### Post by Herman on 2010-09-04
> If I tried another install of Ubuntu (I have version 10.04) from  scratch; would that keep the Ubuntu that's already there prim and proper  like?Yes it would. You might delete the Windows partition, maybe with a partition editor like GParted before the installation, or else during the installation using the Ubuntu installer's inbuilt partition editing program. 
Then you can create a new partition in the free space and format it with the ext4 file system or whatever Linux file system you like and install your newer Ubuntu in that partition.
The Ubuntu installer will write your new Ubuntu operating system's GRUB to MBR for you and it will scan your computer and automatically add your existing Ubuntu to your new boot menu.
When you reboot, GRUB will boot your new operating system automatically, or you can scroll down your GRUB menu and pick your current operating system.
Your current Ubuntu operating system will remain exactly as it is.
You are advised to make a backup before using any partition editor just in case anything goes wrong during partitioning, of course. It's relatively rare, but it can happen due to something as simple as a few specks of dust on an optical drive lense or a power fluctuation that happens at a bad time.

There is one minor thing you might want to check though, if the Ubuntu installer reformats the swap area you might like to edit the UUID number for your swap area in /etc/fstab to make sure your current (older) operating system will still be accessing the swap area. Otherwise you may or may not notice a slight reduction in performance, especially if your computer doesn't have a lot of RAM.
Ask if you want help with it and I'll elaborate, otherwise I'll assume you know what to do.

While you have your older Ubuntu running, if you would prefer to have GRUB booting your older (existing) Ubuntu by default, you may run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' and re-install your older Ubuntu's GRUB to MBR with 'sudo grub-install /dev/sda'.
Then your older, established operating system will appear at the top of your GRUB menu to be booted by default and you can scroll down to boot your newer Ubuntu installation.

You can take your time customizing your newer Ubuntu operating system, decorating it how you like and installing all of your favorite programs. 
When you're ready to make the newer Ubuntu your main operating system and move into it, the hidden files in your /home/username folder in your older Ubuntu contain things like your evolution email, addressbook, calendar, contacts, memos and tasks. You'll find this inside your .evolution folder. Other hidden folders may contain settings for a few of your other favorite programs, and you can look for those too.
You can copy the ones you recognize across and paste them into your newer Ubuntu's /home/username directory to overwrite the empty ones that are there.
Then all you need to do would be just move your regular files into it and then you can do what you want with the older Ubuntu installation and the partition it's in.
Either delete it and resize your new installation to fill up the free space, or wait and install an even newer Ubuntu version in that partition. Another new Ubuntu is made every six months, and six months seems to go by quickly enough. :)

---

### Post by M_Mynaardt on 2010-09-05
I just want to see if I understand this, then.  If I try to reinstall Ubuntu afresh; then I'll probably get two different Ubuntus on my computer (effectively): the old one and the new one, right?

And when would the next update be due out?  Sometime in October?

It wouldn't be catastrophic for me if I redid Ubuntu from scratch.  I just need to copy a number of files I made in *MS OneNote* into Open Office ODT files, and that's about it.  So it's not like I'd be losing a lifetime's work sort of thing...

---

### Post by Herman on 2010-09-05
Yes, the next release of Ubuntu is called 'Maverick Meerkat 10.10', the 10.10 representing the year and month it is to be released. Ubuntu is a fast moving operating system that's always under rapid development and is often the first to try out new ideas and new programs. That's one reason why it's nice to have two Ubuntus, one can be your tried and tested, stable one for your main operating system, and the other can be your new operating system for trying out the latest and greatest new software and ideas.

It's not necessary to do things that way, that's just one way to do things.
I think it's a slightly better way than to just have one operating system and 'upgrade' to the new release, although that should work fine, there are always a few people who have difficulties upgrading. 
When we 'walk' our operating systems forwards like this, we should always have at least one operating system for a spare in case anything goes wrong with the other. We can always use a Live CD to fix the installed operating system with if anything goes wrong, but my wife likes being able to just boot into the other so she can keep having fun until I get home, then she gets me to fix whatever's wrong. It saves a lot of stress and time for her.

---

### Post by M_Mynaardt on 2010-09-05
Hi again!

Well!  That number designation makes things easier to figure out!

I just finished putting "mini Ubuntu" on my netbook and gave XP the heave-ho sort of thing, so my netbook is an all Ubuntu machine now.  Took a hell of a long time, though; mostly because when I started to do that, my (_**old**_) wireless router decided it was going to be a temperamental distraction and lock up my modem for a while.

I finally got that all sorted out.

And I've made backups of all my files.  In triplicate!  Having had hard drive failures and virus wipe outs in the past, I'm a teeny-weeny bit paranoid about my data!

I also figured out how to back up all my e-mail some nice too, so that will be a snap to get back up proper for making my computer a lean, mean, all-Linux machine!     :cool:

So within the next couple of days it should be "bye-bye windows" with my desktop.

Thanks for the help and advice, by the way!     :biggrin:

---

