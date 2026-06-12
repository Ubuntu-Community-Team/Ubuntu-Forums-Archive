---
title: "flawed installation instructions result lost my laptop"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by davidU on 2005-07-04
Hello all
I did read the postings before I wrote this, but couldn't find anything I could relate to my situation right now.

Just for the record, I have hated MS OSes since 3.1, and XP has got to be the worst so far. So believe me, I have read up on Linux distros for a number of years and always came to the conclusion that the install instructions tend towards gibberish for anyone who does not already understand unix speak and there is a strong possibilty that at the end of it all, you will not have an OS.  I have a degree in Information Systems (not Unix unfortunately).

At last I discovered Knoppix boot CD, and then Ubuntu.  At last convinced by the smooth installation and the clean interface, I decided to install a dual boot of Ubuntu with XP on my new laptop.

I read numerous installation documents before and during installation, both from the install CD ROM Version 5.04 for Intel x86 and posting here and on Wikki.  This turned into a nightmare trip to wonderland without even a rabbit to guide me as the instructions often omit to mention pages of information that are presented to the user.  The user is presented with screens unmentioned and options undreamed of at numerous points during the install.  This is very unnerving.

I chose the Expert mode as recommended for dual-boot, but the part that failed was attempting to place Grub bootloader anywhere else but the primary partition.
I was using the correct path dev/hda6, as this was accepted by Lilo after Grub refused numerous times.

Well you can guess what happened, after hours of brain draining deciphering geek speak into plain English and wondering WTF later, I have no operating system on the laptop, either Linux or Windows.  What I do have at boot time is a cryptic message about as useful as any I ever read under MS Windows.
After indentifying the processor, the network card and attempting DHCP, I get

Quote: PXE-M0F Exiting PXE ROM
Operating system not found.

This may have something to do with my choice of kernel.  I feel I must have chosen the wrong one of the three offered.  As there was no mention of which one to choose in any instructions I read,  I opted for the linux-Image 2.6 10.05-386.
Perhaps I should have chosen i386 or the other one ?
How is one supposed to know which to chose ?

Anyways the install didn't work, so I did it again but wasn't offered a choice of kernel this time, and the same result.

Having decided that by now I must have lost my XP OS on the primary partition, I went through the whole procedure again, this time using the default install option.  The XP partition was still there though, so I chose the ext2 partition I had made earlier for the Ubuntu install, completed everything tickety boo, BUT, still no operating systems.

Maybe someone can help, but if it turns into another brain agony over what the hell the writer is talking about I will have no other choice but to re install MS XP, simply because I can.

As I said earlier, I'm not stupid, just trained in MS Windows to degree level.  I can follow instructions when they are complete, but when great chunks are missing, well, this is where Linux is going to fail when competing with MS, and it's a crying shame.

Hopefully some kind soul will assist me in getting my laptop back, even without XP, Ubuntu on it's own will do fine, 'though I'd rather have the dual boot as this is the first time I've had a legal copy of MS software, and a device with a big enough hard drive to support dual booting. 

regards

David Urmston

---

### Post by brim4brim on 2005-07-04
I have no idea what your talking about.  I installed it alongside windows no problem using the standard install.  At least I assume thats what it was I just hit enter to start installation.

I previously reduced the size of my windows partition by about 20 GB.  Linux found the free space and installed itself there and automatically configured Grub for me.

Your trying to do things that are essentially not recommended unless you know what your doing.  In Xp trying to anything other than what they want immediately fails with similar consequences.  Why not just use the normal installation.  For me it just worked and I've installed about 5 different distro's on laptops without any problems and I had no experience with partitioning when I started.

---

### Post by davidU on 2005-07-04
[QUOTE=brim4brim]I have no idea what your talking about.  I installed it alongside windows no problem using the standard install.  At least I assume thats what it was I just hit enter to start installation.

I previously reduced the size of my windows partition by about 20 GB.  Linux found the free space and installed itself there and automatically configured Grub for me.

Your trying to do things that are essentially not recommended unless you know what your doing.  In Xp trying to anything other than what they want immediately fails with similar consequences.  Why not just use the normal installation.  For me it just worked and I've installed about 5 different distro's on laptops without any problems and I had no experience with partitioning when I started.[/QUOTE]
 Sorry, you've lost me already.

What did I do wrong ?

I made three partitions using Partition Magic 7.  I folowed instructions on the ubuntu install CD, where they matched to what I saw on the screen - everything went fine, except the Grub not going to the MBR - which I read is the correct way to NOT lose my XP install.

Please clarify what you think I did wrong

reagrds

David

---

### Post by mingus on 2005-07-04
*. . . the part that failed was attempting to place Grub bootloader anywhere else but the primary partition.  I was using the correct path dev/hda6, as this was accepted by Lilo after Grub refused numerous times.*

The default for grub is not the primary partition (actually, there can be more than one primary, I assume you mean the "active" or the first primary), it is the MBR.  Expert install provides the choice to specify a location for either Grub or LILO.  The correct path is hda6?  That puts the loader in the boot sector of that partition.  Almost for sure you installed the loader to hda1, and this is why you have a problem (see below).

*Operating system not found.*

You have not lost the OS, unless the partition itself or the partition table is corrupted, and no reason for that to have happened.  This errors occurs when the BIOS calls the MBR and it cannot find the boot sector.  It can occur with a Windows-type MBR when the active partition has been changed from the first primary on the disk, as W$ is hardcoded to look there.  If grub had been installed to the MBR, you would probably be getting "GRUB . . ." and then a hang.  Boot from W2K/XP install media, get into the Recovery console, and then do >fixboot to restore the system partition boot sector.  The command >fixmbr will restore XP's special MBR.  If this doesn't boot XP, create a system partition boot floppy; there is an easy-to-follow KB article @MS - it is just ntldr, ntdetect.com, and boot.ini.  This is effectively the boot sector.  You can boot from it straight into XP.

[I]I opted for the linux-Image 2.6 10.05-386.
Perhaps I should have chosen i386 or the other one ?[/I]

This is the same kernel.

---

### Post by davidU on 2005-07-04
> **mingus]*. . . the part that failed was attempting to place Grub bootloader anywhere else but the primary partition.  I was using the correct path dev/hda6, as this was accepted by Lilo after Grub refused numerous times.*

The default for grub is not the primary partition (actually, there can be more than one primary, I assume you mean the "active" or the first primary), it is the MBR.  Expert install provides the choice to specify a location for either Grub or LILO.  The correct path is hda6?  That puts the loader in the boot sector of that partition.  Almost for sure you installed the loader to hda1, and this is why you have a problem (see below).

*Operating system not found.*

You have not lost the OS, unless the partition itself or the partition table is corrupted, and no reason for that to have happened.  This errors occurs when the BIOS calls the MBR and it cannot find the boot sector.  It can occur with a Windows-type MBR when the active partition has been changed from the first primary on the disk, as W$ is hardcoded to look there.  If grub had been installed to the MBR, you would probably be getting "GRUB . . ." and then a hang.  Boot from W2K/XP install media, get into the Recovery console, and then do >fixboot to restore the system partition boot sector.  The command >fixmbr will restore XP's special MBR.  If this doesn't boot XP, create a system partition boot floppy said:**
> I opted for the linux-Image 2.6 10.05-386.
Perhaps I should have chosen i386 or the other one ?[/I]

This is the same kernel.
 thanks for your help regarding the XP recovery disks Mingus, I don;t have a floppy in the laptop.  I suppose the Toshiba install CD will do the trick.  Though I am new to XP and hate it 'cos the developers moved and hidden things again and I can't even burn a f***ing CD ROM on these machines anymore, I have to use an older Windows 2000 machine.

At least I didn't use the worng kernel !
What is the difference between the 3 options given ?

When given the option where to place Grub, I tried to place it other than the MBR (Sorry my mistake, not the primary partition as I said earlier, I meant the MBR) but it didn't accept the location I typed .... /dev/hda6 - which is one of four partitions, 1 created specially for the Linux boot and formatted as ext2, 1 for the swap and 1 for the data-share.

Because Grub didn't want to play, I used Lilo which gave more details as to the location and accepted the path (as above).  I don't see how I used the MBR for Grub when I went to such a lot of trouble to make sure that I didn't.

regards  David

---

### Post by WildTangent on 2005-07-04
i think what you might have done is overwrite your XP installation with the linux installation.

-Wild

---

### Post by davidU on 2005-07-04
[QUOTE=WildTangent]i think what you might have done is overwrite your XP installation with the linux installation.

-Wild[/QUOTE]
 It doesn't ssurprise me.  The install instructions aren't clear as I said in my original post.
First time I shouldn't have done what you suggest because I chose the "expert" install and nselected the partition to install Linux and formatted it as ext2.  As I said, Grub wouldn't accept any path of the paths I typed, giving me error messages that I can't remember, each time.  That is why I went to the Lilo boot loader which correctly indentified all the pertitions, allowing me to type "/dev/hda6".  
I do not think this is the primary active partition !  
Or am I mistaken here ?

In frustration, I next chose the "default" install, However, I was still presented with an option of where to install Ubuntu, so I chose the ext2 partition again, even allowing Grub to install in the MBR this time.
Surely I would have a Linux OS at boot time, even if I did lose the XP OS ?

regards

David

---

### Post by davidU on 2005-07-04
> **mingus]*. . . the part that failed was attempting to place Grub bootloader anywhere else but the primary partition.  I was using the correct path dev/hda6, as this was accepted by Lilo after Grub refused numerous times.*

The default for grub is not the primary partition (actually, there can be more than one primary, I assume you mean the "active" or the first primary), it is the MBR.  Expert install provides the choice to specify a location for either Grub or LILO.  The correct path is hda6?  That puts the loader in the boot sector of that partition.  Almost for sure you installed the loader to hda1, and this is why you have a problem (see below).

*Operating system not found.*

You have not lost the OS, unless the partition itself or the partition table is corrupted, and no reason for that to have happened.  This errors occurs when the BIOS calls the MBR and it cannot find the boot sector.  It can occur with a Windows-type MBR when the active partition has been changed from the first primary on the disk, as W$ is hardcoded to look there.  If grub had been installed to the MBR, you would probably be getting "GRUB . . ." and then a hang.  Boot from W2K/XP install media, get into the Recovery console, and then do >fixboot to restore the system partition boot sector.  The command >fixmbr will restore XP's special MBR.  If this doesn't boot XP, create a system partition boot floppy said:**
> I opted for the linux-Image 2.6 10.05-386.
Perhaps I should have chosen i386 or the other one ?[/I]

This is the same kernel.
 PS, I haven't got a clue of how to get into the Recovery Consul on XP Home.
I tried the Toshiba recovery CD but this only allows me to re-install XP, over writing everything.
No way to get to Command prompt as far as I can see without a floppy drive.

regards

David

---

### Post by mingus on 2005-07-04
*I suppose the Toshiba install CD will do the trick.*

Check this out first, it may not.  Recovery CD's are usually intended to restore the system to its orig state, not to do repairs.  Most will reformat the disk.

*I have to use an older Windows 2000 machine.*

W2K install media will work, too.

*/dev/hda6 - which is one of four partitions, 1 created specially for the Linux boot and formatted as ext2, 1 for the swap and 1 for the data-share.*

This is good.  We may need this if the other fixes don't work.

*I don't see how I used the MBR for Grub when I went to such a lot of trouble to make sure that I didn't.*

No, I was saying that it appears you did *not* install grub to the MBR.  Good.  But as I recall, other than something very serious wrong with the disk, the only way to blow out the boot sector is to write another loader to the system partition, which is hda1.  In any event, go to the MS support site with the "operating system not found" and you'll find several causes for this.  I think >fixboot is what you need, and then >fixmbr.

---

### Post by davidU on 2005-07-04
[QUOTE=mingus]*I suppose the Toshiba install CD will do the trick.*

Check this out first, it may not.  Recovery CD's are usually intended to restore the system to its orig state, not to do repairs.  Most will reformat the disk.

*I have to use an older Windows 2000 machine.*

W2K install media will work, too.

*/dev/hda6 - which is one of four partitions, 1 created specially for the Linux boot and formatted as ext2, 1 for the swap and 1 for the data-share.*

This is good.  We may need this if the other fixes don't work.

*I don't see how I used the MBR for Grub when I went to such a lot of trouble to make sure that I didn't.*

No, I was saying that it appears you did *not* install grub to the MBR.  Good.  But as I recall, other than something very serious wrong with the disk, the only way to blow out the boot sector is to write another loader to the system partition, which is hda1.  In any event, go to the MS support site with the "operating system not found" and you'll find several causes for this.  I think >fixboot is what you need, and then >fixmbr.[/QUOTE]
 Thanks again Mingus,
   however, fixes are a bit late as I lost my rag and used the Toshiba recovery disk, reformatted the hard drive and re install the OS, sod the apps.
 
To my surprise, I discovered that the primary partition has a volume label "data-share" which I thought I had placed on partition 4, not partition 1 !

Anyway, I'm so tired now I am going to have to call it a day, and wait for another oportunity to start again. In the meantime I'll have to do without my laptop.

PS.
where do I type the commands you write ? 
I have no way of getting to the Command prompt on the laptop as it doesn't have a floppy drive.

You wouldn't think I had a BSc in this stuff would you.  The Uni skipped over all this practical stuff, assuming we already knew all about it I presume, then rammed me full obsolete knowledge about pre XP applications.

regards

david

---

### Post by mingus on 2005-07-05
[QUOTE=davidU]
where do I type the commands you write ? 
I have no way of getting to the Command prompt on the laptop as it doesn't have a floppy drive.
[/QUOTE]

Given that you have already reformatted, this is moot now, isn't it?

I double-checked the error message, and it looks like your system's problem is (was) with the MBR *or* you inadvertently marked another partition active (W$ can only boot from the first primary).  The error is from the BIOS.  Here is the explanation and various fixes:

[http://support.microsoft.com/default.aspx?scid=kb;en-us;321626](http://support.microsoft.com/default.aspx?scid=kb;en-us;321626)

So the repair is a simple >fixmbr or to use fdisk to reassign the active flag.  Unfortunately, you've been twice bit by MS and Toshiba.  MS no longer permits oem's to deliver installable W$ media; your system's  license only allows for recovery media and a copy of i386 on the disk (service packs, installs, etc.)  Toshiba bites you by not including a floppy.  You could have replaced the MBR with a W98/ME/DOS bootable floppy running FDISK.  The only solutions I can think of, aside from getting a copy of W2K/XP CD media, would be to burn a boot loader to CD (this can be done with grub or you could use download Smart Boot Manager) which would then boot XP, and then you could install the Recovery Console from the \i386 folder.  It would be wise to install this given how you've been hamstrung by MS and Toshiba.

[http://support.microsoft.com/default.aspx?scid=kb;en-us;307654](http://support.microsoft.com/default.aspx?scid=kb;en-us;307654)

---

### Post by davidU on 2005-07-06
Hi Mingus,
          thanks for your reply, yesterday. Sorry it's taken me so long to get back, that's just the way it is around here.

The link to the MS KB re: Recovery Consul is very helpful, the other (?).  

What I think I did wrong was - to neglect to put the two OS primary partitions within the first 2 Gb of the Hard Drive. There is a 1,024 cylinder limitation which I was unaware of, and is most likely why my install failed.

Now I'm stuck as the XP partition has nearly 4 Gb used already and I have not installed any 3rd party apps except Sophos and Sygate. 
I can't see how I can make it smaller without killing it, again ?

I'm using Parition Magic 7.

I've read and re read the blurb about the 2Gb barrier- 1,024 cylinder limitation, and can't see how to get around this issue. 

Why is my XP install so huge anyway ?

regards

---

### Post by mingus on 2005-07-06
*The link to the MS KB re: Recovery Consul is very helpful, the other (?).  *

One link explains the different causes to the "OS not found" error msg.  The other how to install and use Recovery Console.

*There is a 1,024 cylinder limitation which I was unaware of, and is most likely why my install failed.*

Maybe, maybe not.  Check the BIOS setup to see if the full capacity is recognized.  PartitionMagic 8 (don't know about 7) will in its graphical display show where cylinder 1024 is.  If your BIOS has an LBA option, that may overcome it.  Or, the syntax "#grub-install --force-lba /dev/hda" will do that.

*I can't see how I can make it smaller without killing it, again ?*

Back it up, repartition, restore.

*Why is my XP install so huge anyway ?*

No idea.  The XP install permits specifying a partition size.  If your installation was created by the Toshiba recovery CD, then the size is probably hard-coded.

---

### Post by DancingSun on 2005-07-06
I also recently installed a dual boot XP/Ubuntu configuration.

I did so successfully without any problems. XP was installed first.

I've been able to use just the 5.04 installation CD to do all the necessary work, no partition magic.  I just pop in the CD, bootup, use the manual partition option, resize ntfs partition, create linux partitions, and install away.

I kept the ntfs partition as the active boot partition, and installed GRUB on the MBR.

BTW, 4GB for XP install sounds about right.

---

### Post by Lax D Unit on 2005-07-07
ok well im tired from work and my eyes hurt so i wont read all the other posts to see what they have said but. judgeing from what you have said i have had the same problem. only mine was trying to config debian.....dont even wanna go into it. any ways if ur still haveing problems and if no one has psted this already. put in your xp boot disk, or install disk. they should be the same. boot from your cd drive. now when you run it run the windows config opp. this should bring up a dos like screen. then type help and find the abreviated code for fixing the MBR. this should do the trick. see on my comp instead of it saying OS not found. it typed out probly 1000 sevens and zeros and said error. anyways good luck hope what i said works

---

### Post by davidU on 2005-07-07
Hi Mingus,
   my BIOS does not have any mention of LBA.
The BIOS screen and options are extremely bare with not a mention of the size of the hard drive or the number of cylinders, sectors, etc. providing only it's model name and serial number.
Also the Toshiba documentation on BIOS is pretty slim, revolving almost exclusively around setting passwords.
Toshiba recovery disk gives no option for getting to a Command Prompt.

My next probelm arises using Partition Magic v7.

I shrunk the C: drive to 5 Gb. This went OK.
Created a new Ext2 - primary partition. This went OK.
Created a partition for Swap.  This went NOT OK.
Problem being that Partition Magic inserts the swap before Linux.

Create a data share partiton. This went NOT OK. Partition Magic insists on putting the new partition  before the Linux partition, again pushing the Linux partition away from the first 8Gb.

I've got all confused again now and I am very tempted to install Ubuntu on it's own as I am dizzy reading all the docs and still coming up skunked.  Especially when I get conflicting instructions, like I read in the Ubuntu docs that it needs to be a primary partition, then Partition Magic says it recommends putting it in a Logical partition.

It certainly doesn't help when wise guys write in saying that they had no problems doing the dual boot.  One day, computer developers may realise that just 'cos they had no problem doesn't mean the problem lies with the User, and not the software or the instructions.  I scored 'A's' for my modules on HCI and Professional Issues, so I know when I am harvesting the bugs that skilled folks tend to ignore.

Why can't someone write definitive instructions for doing these tasks, there would be many more folks switching to Linux.

Again Mingus, thanks for your assistance, I've learned quite a bit from this forum.
I will try one more time with the dual boot, if this fails I'll try a pure Ubuntu laptop and see how I get on.

Regards DavidU

---

### Post by DancingSun on 2005-07-07
I don't think the 1024 cylinder limitation is your problem.  In the BIOS, does it display the correct HDD size?  What about when you had XP working, did it display the correct size?  How old is your laptop?

If your HDD size was detected correctly, then you shouldn't have the 1024 cylinder limitation problem.

Most likely is that when GRUB wrote to the MBR, something went wrong.  Perhaps the NTFS partition was not set as the bootup partition.

You mentioned running Partition Magic again, so I'm assuming you have XP back up and working.  If so, try just using the Ubuntu install disc to do the resizing and partitioning.  There are posts about using Partition Magic creating Linux partitions that caused problems, so it might be worth a try.  Like I mentioned before, keep NTFS as the boot partition.  If you have the installer automatically allocate the Linux partitions, it will mark the Linux partition as the boot partition.  In that case, manually re-enable the NTFS partition as the boot partition.

If there are any install screens that confuse you, try writing the descriptions down, and cancel the install and post the info, here.  That way we may be able to clear things up for you before you proceed further.

---

### Post by mingus on 2005-07-07
*my BIOS does not have any mention of LBA . . . The BIOS screen and options are extremely bare with not a mention of the size of the hard drive or the number of cylinders, sectors, etc. providing only it's model name and serial number . . . Toshiba recovery disk gives no option for getting to a Command Prompt*

As stated previously, manufacturers are no longer permitted by MS to deliver installable W$ media, only an OEM image which returns the system to its original state.  Perhaps Toshiba locked up the BIOS to protect the end-user.  In any event, system backup and recovery has always been left to the user on PC's.  MS has never supported a method of changing partitions other than reformatting.  But then, you already know this.

*My next probelm arises using Partition Magic v7 . . . NOT OK . . . NOT OK . . .*

Dunno, I have done this and a zillion variations with no problem.  You may be running into a PM safety constraint.  There are many diff config alts that would work, even with the 1024 limitation:  Just put XP's system partition followed by Ubuntu's /boot partition at the front of the disk.  Simple.

*It certainly doesn't help when wise guys write in saying that they had no problems doing the dual boot.  One day, computer developers may realise that just 'cos they had no problem doesn't mean the problem lies with the User, and not the software or the instructions.  Why can't someone write definitive instructions for doing these tasks, there would be many more folks switching to Linux.*

*I scored 'A's' for my modules on HCI and Professional Issues, so I know when I am harvesting the bugs that skilled folks tend to ignore.*

Right!  Software engineers are careless idiots writing buggy code and sloppy misleading documentation; they haven't a clue (nor do they care) about real end-users!  If only they had the insights of a real IT education!  And to think I've been paid real money for all these years of such malfeasance; wow!  You've voiced some fairly harsh criticisms, and you're certainly entitled to your opinion, but - no offense intended - your posts indicate that there are issues at work here other than lousy engineering.

Might be better to stick with Windows.

---

### Post by DancingSun on 2005-07-07
[QUOTE=davidU]I read in the Ubuntu docs that it needs to be a primary partition, then Partition Magic says it recommends putting it in a Logical partition.[/QUOTE]
Your Linux "/" partition needs to be primary.

On my dual boot setup, I have NTFS and the EXT3 Linux "/" partitions set as primary.

BTW, I am a brand new Linux user, I have the AMD64 version of Ubuntu on my computer for about a week, so far so good, although there are many places where installing and setting up things can be improved.  I agree the documentations are pretty bad, and in many cases, conficts with each other.  This is definitely Ubuntu's weakest link.

---

### Post by davidU on 2006-04-04
Thanks to everyone who posted
regards
DavidU

---

### Post by hashimoto on 2006-04-04
[QUOTE=davidU]...
After indentifying the processor, the network card and attempting DHCP, I get

Quote: PXE-M0F Exiting PXE ROM
Operating system not found.
...
regards

David Urmston[/QUOTE]

Don't know what you have done, but: PXE = Preboot Execution Environment 

"Etherboot and PXE are two pieces of software that allow one to boot a workstation over a network." as a quick googlling reveals.

---

### Post by davidU on 2006-04-04
[QUOTE=hashimoto]Don't know what you have done, but: PXE = Preboot Execution Environment 

"Etherboot and PXE are two pieces of software that allow one to boot a workstation over a network." as a quick googlling reveals.[/QUOTE]

I think you just resolved the mystery.  
I was not intending that such to happen. At the time everything was turning out wrong. It's a pity I had the problem a year ago. 
I've recently done a complete Ubuntu install to save wasting any more time and it's gone OK/ish.

thanks for your post.

---

