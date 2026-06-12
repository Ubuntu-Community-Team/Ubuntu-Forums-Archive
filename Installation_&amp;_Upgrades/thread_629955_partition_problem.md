---
title: "partition problem"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by lesemi on 2007-12-02
i have made a little error in my install -  and i'm not prepared to go through the whole re-install process.
i have installed gutsy - latest release - and partioned the drive to keep winxp as a secondary boot -  i need xp from time to time for apps not supported in linux.

i thought i kept 20gigs for win - however i must have screwed something up and i'm left with 100 gigs for win and 20 for linux.. i use linux 99.9% of the time.  How can i repartition the ntfs drive to shrink to 20 gigs and not affect the install.

partitions are as follows:

any help?

---

### Post by merlinus on 2007-12-02
gparted live cd may help:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by daengbo on 2007-12-02
gparted in in the Ubuntu live CD which you used for the installation. If it's not in the live CD, you can install it:

sudo aptitude update
sudo aptitude install gparted
sudo gparted

The process will take several steps, because you can't just grow a partition backwards. As always, before doing anything with your partitions, back up your data (and your partition table, if you're paranoid)!
Unmount all partitions on the HDD before starting.
1) Resize the Windows XP partition to 20GB.
2) Copy the Linux partition to the empty space
3) Delete the old Linux partition
4) Grow the new Linux partition to fill the space.
GParted often has problems with auto-mounting new patitions in Gnome, so you'll need to unmount them as you go along, probably several times.

Once you are finished, you aren't finished. You'll still need to edit the /boot/grub/menu.lst and /etc/fstab files to correspond to your new partition names / UUIDs.

You should be able to boot into the new system. If partition get hosed (which sometimes happens), clean install and restore from backups.

Best of luck!

Daeng

---

### Post by merlinus on 2007-12-02
As per my first post, I highly recommend gparted live cd for doing this.  You will not have to mount or unmount anything, and you will be able to resize the partitions from either the left or right using your mouse.

Backing up important data beforehand is vital.

---

### Post by lesemi on 2007-12-14
Thanks for the reply
i will try the live CD tonight.

---

### Post by Wayno-san on 2007-12-15
So how did it go?  Every time I tried to do any kind of resizing on my Linux partitions I ended up with A TON (I mean hours worth) of fsck errors, which, after I fix, do not allow the system to boot into up.  :(  The last time I replaced all the fstab UUIDs to /dev/**** prior to the resize and it still hosed the system.  Just dumps into busybox during boot.... :(   Let me know if you figure out the proper way to do this because I see having to have to do it again sometime in the future.

---

### Post by Herman on 2007-12-15
> Every time I tried to do any kind of resizing on my Linux partitions I ended up with A TON (I mean hours worth) of fsck errors, which, after I fix, do not allow the system to boot into up. :sad: The last time I replaced all the fstab UUIDs to /dev/**** prior to the resize and it still hosed the system. Just dumps into busybox during boot.... :sad: That's not normal, what are *you* doing? If you're not using GParted then you should be.
If you are using GParted already then you should run a few checks on your hard disk to make sure your hard disk isn't on the way out.
Or maybe if you tell us what you're doing and what exact error messages you are getting, (or even as well as you can remember), someone here can help you with a few tips and pointers.

GParted now supports 'moving' and resizing Linux partitions either 'forwards or backwards', like merlinus said, and has had that feature for quite a long time now, we don't really have to copy and paste these days.

... unless we're an expert and we're in a hurry; the 'move' function is quite slow, experienced users might find copying and pasting quicker.
One way is to do as daengbo already explained, that's the fastest way.

Another way is a little slower but easier for most people. You can copy the Linux partition and paste it somewhere temporary and delete the original. Then copy the temporary one and paste it where you really want it to end up and it will be given the same partition number as the original again. Then delete yout temporary copy and resize your new partition to fill the available free sppace. You still might need to edit /etc/fstab with the new UUID numbers,... but wait! I seem to remember that GParted copies the old UUID number to the new copy of the partition and gives the original copy the new UUID number. Just check to see if I'm right about that, but I think so. In that case you would just be able to boot again as normal, without needing to edit any files at all. :)

Regards, Herman :)

---

### Post by daengbo on 2007-12-15
Herman,

Thanks for the info about GParted. I don't use it often and not seriously in several yers. I didn't know that it now has the ability to grow backward. Hmmm.

---

### Post by Wayno-san on 2007-12-15
Hi Herman, 
I used Paragon Partition Manager to first backup (copy) the linux partitions to another drive (with resize).  I think they sometimes refer to resize by different names but it basically allows you to back up a large partition onto a smaller space by not copying the empty portion.

Then I used Paragon again to resize the partition.  I didn't move them to different areas of the drive so the partition assignments should have not changed, but just to be safe, I edited the FSTAB to use /dev/*** instead of UUID a couple of reboots prior to making the backup to ensure that everything was still working as it should before the resize.  After the resize, when I tried to boot Linux, I ended up getting a fail during the boot process stating that fsck needs to be run manually.  Then I ran a "fsck -y", which in a couple of instances finished within 10 minutes, and in others took all night and eventually I just aborted and reinstalled.  The instances where it finished quickly I rebooted and upon boot, got dumped into busybox with an (initramfs) prompt.  At this point I was not able to find any information on how to proceed.  There doesn't seem to be much info on how to troubleshoot a linux system if this happens.  I checked the 'net, linux books in the library and the bookstores, and found nothing.  

I do not know if Linux keeps a boot log anywhere, but from my notes I think this was the last thing to scroll across the screen:

```

mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init

```

At this point I used the backup partition and copied it back over to the original location... same errors.  :(

I doubt the HD is the problem since it works fine otherwise.... it's just during these resize episodes that I experience these errors.

---

### Post by Herman on 2007-12-15
:) Hello Wayno-san,
> After the resize, when I tried to boot Linux, I ended up getting a fail during the boot process stating that fsck needs to be run manually. Then I ran a "fsck -y", which in a couple of instances finished within 10 minutes, and in others took all night and eventually I just aborted and reinstalled. The instances where it finished quickly I rebooted and upon boot, got dumped into busybox with an (initramfs) prompt. At this point I was not able to find any information on how to proceed. There doesn't seem to be much info on how to troubleshoot a linux system if this happens. I checked the 'net, linux books in the library and the bookstores, and found nothing. 
 Alright Wanyo-san, let's see if we can fix this. 
You are using the same program, 'fsck', as most people do use, however, most people don't realize that the fsck program is really a program that runs other file system checking programs. It's really great for general purpose use, especially when we need something that can be run automatically by the operating system on boot-up, or by our average users when things are going okay anyway.
When we really need a decent file system check we need to run the file system checker specific for our file system, it will be the same as the one that that fsck runs, but when we run it ourselves directly, we are able to give it much more specific and useful options.

The best way to run a file system check is from a LiveCD so that the file system to be checked is not mounted. You can also run a file system check from an operating system in another hard disk or in another partition providing the file system you want to check is unmounted first.

The file system which is most popular with Ubuntu users is ext3 and the file system checking program for that is called 'e2fsck'.

Here is a combination of options I like that will fix most of your ext2 or ext3 problems, (it's the same one GParted Live CD would run for you if you were using GParted LiveCD).
> sudo e2fsck -C0 -f -v /dev/hda2Where: /dev/hda2 is your ext2 or ext3 file system partition, you should check your partition numbers first with 'sudo fdisk -lu' or similar command, or by looking with GParted partition editor, and change the command as necessary.

Try copying that command and pasting it into a terminal and running it! :)
That should fix your problems! :)

If you use [GParted -- LiveCD]("http://gparted.sourceforge.net/") you can run the same command if you right-click on your partition and  select 'check' from the right-click menu. Then click 'apply', and confirm.

I don't know anything about the partitioning program you are using but it doesn't seem to be working very well at all for Linux file systems. 
[GParted -- LiveCD]("http://gparted.sourceforge.net/") is free and it is only a small download. It is fully compatible with both Linux and other operating systems and can do everything that we need. You should try [GParted -- LivceCD]("http://gparted.sourceforge.net/").

GParted is also in the Ubuntu LiveCD and can also be installed in Ubuntu after it is installed to hard disk.
GParted, QTParted, Partman and LibParted are all recommendable.

[GParted -- LiveCD]("http://gparted.sourceforge.net/") doesn't copy partitions to another hard disk, or at least it wouldn't for me last time I tried it. [GParted -- LiveCD]("http://gparted.sourceforge.net/") has some other programs  that come with it that you can use though, like Partimage and Clonezilla that you could use for that instead, or use the 'dd' command. 
(You need the special version of GParted it you want Clonezilla).

Another e2fsck command combination you might use if the first command still doesn't do it would be this one, 
```
sudo e2fsck -f -v -y /dev/hda2
```Where: /dev/hda2 is your ext2 or ext3 file system partition, you should check your partition numbers first with 'sudo fdisk -lu' or similar command, or by looking with GParted partition editor, and change the command as necessary.

That command is for when your problems are a little more serious, and  it may result in some files being moved to your 'lost + found' directory.
You should make a back-up before running that command and read this, [SIZE=-1][www.oreilly.com/catalog/morelnxsvrhks/chapter/hack  96.pdf]("http://www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf")

Another  useful  command if you want to check to see if your hard disk is on its way out is this one, 'sudo badblocks', [/SIZE]                     Here's a great link from 'Tips For Linux Explorers', about this: [Bad Blocks]("http://www.brunolinux.com/04-The_File_System/Bad_Blocks.html")

If you get feedback from running that command then run 
> sudo e2fsck -c -c -k -v /dev/hda2 And make a complete back-up right away, and start shopping for a new hard disk.

Regards, Herman :)

---

### Post by Wayno-san on 2007-12-15
Thanks Herman, 
I'll try GParted LIVE next time... I actually have it burned and ready to go.  But it looks like I'll have to go with a different program to back up the partition since you stated I would not be able to copy the partition to another drive.  Maybe I'll create a couple of partitions and install linux on them and try to move them around for practice.... right now I do not have that warm-and-fuzzy feeling you get when you have your system backed up and you know that it will work if and when you need it.

---

### Post by Herman on 2007-12-15
You'll really like GParted when you start using it, either from your Ubuntu Live CD,  installed in Ubuntu or in [GParted -- LiveCD]("http://gparted.sourceforge.net/").

You can use Partimage to make a compressed back up copy of your  operating system and store that on another drive, That's what I do.  Partimage is one of the programs that comes included with GParted LiveCD, and you can install it in Ubuntu as well. 
I normally empty my data out first and back that up separately, so backing up the operating system, settings and software doesn't take so long. (Compressing it takes a while). Aysiu has a good how-to on TestDisk here, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage").

Regards, Herman :)

---

