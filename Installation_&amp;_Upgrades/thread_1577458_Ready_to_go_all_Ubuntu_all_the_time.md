---
title: "Ready to go all Ubuntu all the time"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by S. Vaden Blue on 2010-09-18
I have been using ubuntu in a dual-boot situation with Windows Vista for about a week now and I love it. How do I go about allocating the rest of my system resources to ubuntu without performing a re-install? Is there any way to free up the Windows allocated partition and allocate that to ubuntu without messing up my system? Any help would be greatly appreciated. BTW, the initial install ran beautifully, if that's of any consequence here.

---

### Post by goodolandy on 2010-09-18
I'm no Linux expert but I believe you would need to first move/re-create the boot loader on your Linux ext4 partition then use something like GParted to blow away the Windows partition and expand the ext4 partition.

Again, I'm no Linux expert so you will want to verify the above first by doing some Google searching.

---

### Post by maestrobwh1 on 2010-09-18
My suggestion as a Linux user since 2002: I would not wipe out your Vista installation.  There are huge benefits to having two OS's on a machine (if one gets crippled, you have another).  That being said, it is doable to do what you are asking, but be sure you really want to rid yourself of the Vista partition.

My suggestion if you are really sure you want to follow through with modifying your disk and OS setup, boot using the live CD (or usb you created).

Make sure you have an internet connection:

open a terminal and do 

```
sudo apt-get update && sudo apt-get install gparted
``` (or partitionmanager for kde)

launch gparted from the menu 

Do what you need to do with the program, knowing that you could possibly  wipe out your data from your entire disk or make your machine unbootable from the hard disk (outside chance but still possible).

You could just shrink the NTFS Vista partition and you should not have a problem just rebooting, but if you REMOVE the partition and allocate it to the Ubuntu partition (thus making it sda1), grub in the master boot record will not seek files in the proper partition SO:

DO NOT REBOOT YET!

Open a terminal and:

```
sudo blkid -c /dev/null
```

This will give you a list of what partitions you now have, I will assume that the Ubuntu partition is dev/sda1 and formatted as ext4.

Make yourself root user by issuing "sudo su," and chroot into your disk's Ubuntu partition:

```
sudo su
mkdir /mnt/sda1
mount -t ext4 /dev/sda1 /mnt/sda1
mount -o bind /proc /mnt/sda1/proc
mount -o bind /sys /mnt/sda1/sys
mount -o bind /dev /mnt/sda1/dev
mount -o bind /dev/pts /mnt/sda1/dev/pts
chroot /mnt/sda1 /bin/bash
dpkg-reconfigure grub-pc
```

What the above does: it has you log into the disk as root and allows you to issue commands as if you were running from the hard disk, and when you dpkg-reconfigure grub-pc, it reconfigures grub in the MBR and recreates /boot/grub/grub.cfg from the point of view of your hard disk.

You could have also used some grub commands from the live cd, but the chroot method is a bit more fool proof.

You should now be able to reboot.  If you can't, don't say I didn't advise you to either keep things they way they are, or at the most, use the live cd and gparted to shrink the NTFS Vista partition and enlarge your Ubuntu partition.

If you were a seasoned Linux user, I would tell you to go ahead and wipe Windows clean from your drive if you see no value in having it.  I see value in having XP reside as the first small partition in my hard drive.

Then again, you could just reinstall Ubuntu to the entire drive if you mess things up to the point where you can't boot.

---

### Post by wilee-nilee on 2010-09-18
Is this a wubi install?

I also agree with at the least since I assume you have a licensed Vista that you keep it or if you have a install dvd, and the key then your okay, to wipe it. But I'm concerned here that we confirm that it is a real dual boot which would of been a install from a booted Ubuntu cd.

---

### Post by goodolandy on 2010-09-19
@ maestrobwh1: As someone who wants to eventually get rid of his windows partition, I just want to say thank you for the detail step.

I do have one question, if someone were to keep the main partition as you suggest but blow away everything accessible (not hidden) then shrink the partition, how much space would need to be left for Grub?

Don't worry I do have other machines in the house I can use if something were to happen to my machine, running either XP, Ubuntu or Xubuntu.

---

### Post by S. Vaden Blue on 2010-09-19
OK. So there is still some free space left on the Vista side that I would like to devote to ubuntu. How do I go about doing this? I do see the advantages to keeping both OS, but I want to devote more to Ubuntu than Vista.

---

### Post by wilee-nilee on 2010-09-19
> **S. Vaden Blue said:**
> OK. So there is still some free space left on the Vista side that I would like to devote to ubuntu. How do I go about doing this? I do see the advantages to keeping both OS, but I want to devote more to Ubuntu than Vista.

So are we to assume here you have to be more specific. What has been done, maybe a screenshot of gparted you know.
[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

---

### Post by S. Vaden Blue on 2010-09-19
Here is the Gparted screenshot.
[ATTACH]170013[/ATTACH]

You can see what it is that I want to do. I want to shrink the Vista partition and grow the ubuntu to the left.

---

### Post by wilee-nilee on 2010-09-19
So Windows to run efficiently, like any OS really needs to have a certain amount of unused space probably around 30% or so. I see that Vista has a bit of information on it, Your at about 50% used and free right now. How much of that can you just transfer to Ubuntu. You know stuff like music, pictures, general cross compatible stuff.

---

### Post by S. Vaden Blue on 2010-09-19
I was thinking about devoting atleast 50 GB of the Vista free space to ubuntu but I'm not really sure what is possible. I have never dealt with this kind of thing but I am eager to learn. I do know that I am thoroughly enjoying Ubuntu and I want to devote more resources to that. If it's of any consequence, the 2 GB unallocated space is all Vista would allot using the Disk Management utility in Windows.

---

### Post by wilee-nilee on 2010-09-19
> **S. Vaden Blue said:**
> I was thinking about devoting atleast 50 GB of the Vista free space to ubuntu but I'm not really sure what is possible. I have never dealt with this kind of thing but I am eager to learn. I do know that I am thoroughly enjoying Ubuntu and I want to devote more resources to that. If it's of any consequence, the **2 GB unallocated **space is all Vista would allot using the Disk Management utility in Windows.

If your referencing sda1 that is your boot remove that and you will have a nice Vista doorstop. Be very specific now that you can see gparted as to what partition your talking about, ie=sda1 I don't want to miss something and make a mistake.

The best way to transfer that stuff really would be to a external HD for a backup to begin with, or open Vista from Ubuntu and copy and paste from Vista but don't remove it from Ubuntu if you want to get it out of Vista for resizing remove it from Vista.  Be careful about trying to copy and paste to big a chunk at a time, not sure the rules in this area but, I think you probably get the gist of this part.

Do you have a install DVD for Vista?

**I missed the 2 gig space** between sda2 and sda3, to be honest that is something that can be taken care of after you get everything adjusted and decide what you want to do.

---

### Post by S. Vaden Blue on 2010-09-19
It isn't sda1. It is the unallocated(grey) in the middle to which I was referring. It's actually 2.63 GB. That is what Vista allowed when using the shrink utility. I'm admittedly lost here.

---

### Post by S. Vaden Blue on 2010-09-19
I am lost because it looks like there is available space in spades for shrinking the Vista partition without transferring any files. I'll get it if you'll just bear with me.

---

### Post by S. Vaden Blue on 2010-09-19
I have a windows partitioning utility (EASEUS Partition Manager) that will allow me to resize the Vista partition creating the desired amount of unallocated space. Once I have made this space available, is it possible to grow the Ubuntu partition using the unallocated space?

---

### Post by wilee-nilee on 2010-09-19
> **S. Vaden Blue said:**
> I am lost because it looks like there is available space in spades for shrinking the Vista partition without transferring any files. I'll get it if you'll just bear with me.

Yes there is 50% free; but for Vista to run with any normal speed you want to keep about a 30% free. That is why I ask if you can transfer to Ubuntu or a external.

It is alright to be lost but if we get this done you will know the path to OS enlightenment grasshopper, in the end.;) We all start somewhere so it is all good.

So do you have Vista install disc, and the key for activation? This is important to know, in case something goes wrong. Not likely to happen but a hard copy of all your OS is the best insurance you can have along with a back up of the stuff you can't lose.

I'm very familiar with doing all of this and so are many others on line so you have good company on the forums. Some of us will do things a little differently but the end result is usually okay.

Now some people like to have a separate home partition for Ubuntu, so that you can upgrade and keep the stuff in home separate. I don't use this method, so I can't really help you there; but if this also sounds like something you might want we will get the right people in on this endeavor.

---

### Post by S. Vaden Blue on 2010-09-19
What I do have is a set of disks that I burned when I first purchased the lappy. It includes a rescue and recovery startup disk and a total of 4 product recovery discs. I think this is what you are asking but I am not sure to be honest. It does say on the Lenovo site that the disks will restore the system to it's factory settings. Not sure about the key though.

---

### Post by wilee-nilee on 2010-09-19
> **S. Vaden Blue said:**
> I have a windows partitioning utility (EASEUS Partition Manager) that will allow me to resize the Vista partition creating the desired amount of unallocated space. Once I have made this space available, is it possible to grow the Ubuntu partition using the unallocated space?

I wouldn't use anything to resize Vista but it's disc manager.
[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

Now you can actually download a de-fragger that will get Vista to shrink more then it normally would. Post 6 will tell you the de-fragger.
[http://www.sevenforums.com/general-discussion/68287-cant-shrink-windows-7-partition-anymore.html](http://www.sevenforums.com/general-discussion/68287-cant-shrink-windows-7-partition-anymore.html)

Notice the defragger has to be run on boot and set up that way, it moves everything to the front of the disc including the unmovable files if run correctly. Windows has a file system that puts unmovable files at the end or middle of the disc making it hard to shrink the partition with the on board disc manager.

Try shrinking the Vista with its native device or check the amount you can shrink it by looking at the link and following the instructions to the point where the disc manager tells you how much it can shrink and do it or take a snip of it and post the picture.

---

### Post by wilee-nilee on 2010-09-19
> **S. Vaden Blue said:**
> What I do have is a set of disks that I burned when I first purchased the lappy. It includes a rescue and recovery startup disk and a total of 4 product recovery discs. I think this is what you are asking but I am not sure to be honest. It does say on the Lenovo site that the disks will restore the system to it's factory settings. Not sure about the key though.

Are the 4 product recovery the Lenovo set or the ones you burned. What you burned is the backup of Vista as factory installed probably. 

Windows if you had purchased it not installed has a key to activate, as a legitimate MS product. If you had purchased it this way you would have 30 days to put the key in to make it legit, it would work like normal until that 30 day limit then it would do whatever it is MS does to make sure you put the key in. this is just a explanation of the key reference.

So any OEM recovery=full install discs have a auto key activation, or they provide the key. The disc backup you made, if done correctly and the all burned right reinstalls the factory install and auto activates the key.

Any single recovery disc with less than probably 2,7 gigs or more in disc size, is probably just a bootable disc for repairs, very limited repairs, like reloading the MBR and running a command line chkdsk...etc

---

### Post by rodericke on 2010-09-19
The lappy didn't come with it's own disks. Only the ability to burn the disks. If that's what you mean.

---

### Post by wilee-nilee on 2010-09-19
> **rodericke said:**
> The lappy didn't come with it's own disks. Only the ability to burn the disks. If that's what you mean.

Alright, personally I have never done the backup like this. I have hard copies of a purchase of W7 and the 4 disc XP OEM install for the netbook I have.

If you feel comfortable that the discs you burned are good, then I think we can proceed. Personally I would see if the manufacturer would provide a regular 1 dvd install disc that you can activate. The regular install disc would hopefully be free of the manufacturers additional firmware added to the MS Vista release. 

For example my netbook running the manufacturers set=OEM had 10 extra programs running not even needed. When I installed the straight XP they let me down load it was much faster and just plain ran better. Personally I like W7 better but hardly ever use either except to know how they run for occasions such as this.

My XP OEM set cost a extra 20$ US. My student upgrade to W7 was 25$, and a few extra for a years access to the ISO and .exe download, and a actual dvd purchase total I think was 40$ US.

I have given you a lot of information in this thread so keep asking questions as needed I want you to be set up and happy.;)

---

### Post by wilee-nilee on 2010-09-19
Sorry for another post. I guess really all I'm trying to do is make sure that if needed; say you get a new computer you can reload this lappy with Vista and sell it or use it again if needed. Also if you decided you needed vista again if you decide to wipe it instead; after pulling out the stuff you want to save. You own that MS license, and it is somewhat valuable, in these areas.

---

### Post by rodericke on 2010-09-19
I don't know if this is of any consequence, but I had originally had trouble with the original ubuntu install because everything was allotted to Vista and the Ubuntu Live CD wasn't recognizing the free space. So there were no 'install side-by-side' options or 'use contiguous free space'. I then proceeded to use EASEUS to 'unallocate' some space at which time the Ubuntu install ran beautifully. The EASEUS utility seemed to work great for this purpose. No problems with either OS, at least none to speak of.

---

### Post by wilee-nilee on 2010-09-19
> **rodericke said:**
> I don't know if this is of any consequence, but I had originally had trouble with the original ubuntu install because everything was allotted to Vista and the Ubuntu Live CD wasn't recognizing the free space. So there were no 'install side-by-side' options or 'use contiguous free space'. I then proceeded to use EASEUS to 'unallocate' some space at which time the Ubuntu install ran beautifully. The EASEUS utility seemed to work great for this purpose. No problems with either OS, at least none to speak of.

I think your probably okay doing it this way, but it is really your call. Even if it borked the Vista, so that it wouldn't boot, you have the discs you burned, and you could pull your stuff out using a live Ubuntu CD. And not knowing how old the lappy is you may be able to get a install disc from the manufacturer as well if needed.

Personally I just try to make sure my horse is in front of the cart. You have hardly anything in Ubuntu now, so if it was me I would be hesitant to just jump straight into resizing Vista, but thats just me. The reason being is that a pulling out information from a borked Vista, even if unlikely to happen will be a bit of a process, that could be avoided by putting some of that stuff in Ubuntu first then rebooting Vista and removing the transfered stuff. Then you could shrink it even more. Here is a picture of my gparted W7=sda1 is in a small partition, that I pre-formatted and installed into.
[ATTACH]170023[/ATTACH]

I was able to though using that defragger in the link to get it this small originally, but it was a upgrade from the XP that had to much stuff left over so I did a fresh install, as I had the DVD. The W7 install started out at 160gigs the full HD.

---

### Post by wilee-nilee on 2010-09-19
Additionally, when you go to resize Ubuntu, do it from a live CD, and right click on the swap and turn it off, then expand the external. Then expand the ext4 partition don't have both of those partition resized in one setup. You want to run those individually.

You will probably have to reload the partition after resizing I suspect you will just get a grub error after moving the front end of Ubuntu towards the front of the disc. This is why I asked about the separate home, that unallocated space left over after the shrinking of Vista could be a shared ntfs or another ext4 for home rather then resizing Ubuntu.

Always to if I haven't mentioned reboot any resized OS to make sure it works before doing anything else.

---

### Post by rodericke on 2010-09-19
Thanks for all your help, wilee-nilee. Like the avatar BTW. Anyway, you're right. I'm not going to just jump into resizing Vista. I guess I'm just so excited about Ubuntu that I wanted to go all the way on the first date. Thanks for the much appreciated advice.

---

### Post by wilee-nilee on 2010-09-19
> **rodericke said:**
> Thanks for all your help, wilee-nilee. Like the avatar BTW. Anyway, you're right. I'm not going to just jump into resizing Vista. I guess I'm just so excited about Ubuntu that I wanted to go all the way on the first date. Thanks for the much appreciated advice.

I used to play Jazz professionally, and John Coltrane was my biggest influence amongst others from speed metal to all genres. When I had my game on I could play many of his solos note for note,and was considered to be a equal basically by the world class players I played with. I used to play the all the saxes, flute, clarinet,guitar, piano and fretless electric bass. I miss those days I have such a wide area of interest that it just sort of fell to the wayside when I just wanted to play full on improv multimedia avant garde music, not much of a market or appreciation for it though.

---

### Post by rodericke on 2010-09-19
Okay. What if I wanted to unallocate the space and then do a fresh install of Ubuntu? Would that be easier? I really have nothing on ubuntu at this point. How would I go about that?

---

### Post by wilee-nilee on 2010-09-19
> **rodericke said:**
> Okay. What if I wanted to unallocate the space and then do a fresh install of Ubuntu? Would that be easier? I really have nothing on ubuntu at this point. How would I go about that?

That is a option, you would just boot the live Ubuntu cd, open gparted turn off the swap and delete the swap ext4 then the extended and just have it install to the free space. You can do this without rebooting before installing.

Now if you remove Ubuntu you will lose the Vista boot but if you just install Ubuntu grub will see it and you should be set.

If you remove Ubuntu and for some reason needed to get into vista you would just need to reload the MS bootloader to the MBR; it is easy and I can give you the command and a link to a recovery cd for doing this with Vista.

The resize of Ubuntu would probably take longer then just deleting then reinstalling of Ubuntu, I think your on the right track there.

---

