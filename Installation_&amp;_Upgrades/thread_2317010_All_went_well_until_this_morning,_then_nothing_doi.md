---
title: "All went well until this morning, then nothing doing"
date: 2016-03-12
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2016-03-12
Here is the setup on this computer:

sda is 120 GiB SSD:
sda1 is a 1G file (partition? see gparted screenshot below) and I have no idea what it is unless it is just something that the SSD needs and it set up. Anyone know?
sda2 is Ubuntu Fall-back already long ago installed with / and  /home on same partition

Thursday night, I installed 14.04 (Ubuntu Mate) onto sda3. Used UM off and on all day yesterday adding browsers and customizing to my preferences, including setting the HDD to go into hibernation after 2 hours of inactivity. The latter just before going toes up last night.

This morning, I attempted to wake up the computer, but it would not come to life. When I tried to reboot, it gave an error message about not finding sdb1 (where /home is installed). (sdb is a 1T HDD divided into two EXT4 partitions) ((sdb is a 1T HDD divided into two EXT4 partitions) (sdb is a 1T HDD divided into two EXT4 partitions) sdb is a 1T HDD divided into two EXT4 partitions) 

Then tried to install UM again, but this time both system and home into sda4 with the idea of being able to examine sda3 Also attempted to set up a 1
G /boot and a 2G swap. But it will not install. ????

One of the things that may be wrong is that I do not remember any choice of primary or logical partitions on Thursday night. If I should have made a choice of  logical during that install, I do not remember doing it. But the fact that the whole thing ran like a champ yesterday gives me cause to doubt that this was the problem in the that first install of UM day before yesterday.

Ran the live CD version, gparted did not show the HDD at all. If it went pear-shaped, this would only be the second HDD failure of my life. But I find it very co-incidental that all was fine until I chose the hibernate option under power saving, then the next time I tried to use the computer, the HDD did not seem to be there. Could these be related and the HDD is just taking a siesta? If so, how do I tell it that it is springtime?

And if nothing to do with hibernation, does anyone have an idea what the problem is? Any info I can provide (and if involves CLI, code will be very much appreciated)

[ATTACH=CONFIG]267783[/ATTACH]

---

### Post by grahammechanical on 2016-03-12
I would just like to clarify something to avoid distraction.

I think that sda has GPT (GUID partition table) and not MSDOS partitioning. And therefore there is no need for Extended and Logical partitions because with GPT we do not have a 4 primary partition layout. You are showing 7 partitions without an extended partition to put the extra 3 partitions in as logical partitions.

Furthermore, GPT is backwards compatible with a motherboard BIOS boot system even though GPT is part of the UEFI boot system specification. But when we install Linux on to a GPT partitioned disk with a BIOS boot system we need a bios boot partition and the installer will create one for us. If it is a UEFI boot system then there will be a efi boot partition.

How much RAM does this machine have? If we are going to hibernate then the swap partition needs to be greater than the RAM size because the data in RAM is stored in the swap partition.

My advice would be to seek advice to fix the original problem and forget about the failed new attempt to install Ubuntu Mint. That is only a distraction. Or to seek advice as to how to overcome the failure to install Ubuntu Mint a second time.

Choose which problem you want advice on. At the moment there are two problems.

Regards.

---

### Post by Odyssey1942 on 2016-03-12
Graham, Thanks for yours and for the clarification regarding partitions.

The computer, which has 8 Gigs RAM, is probably 3 or 4 years old. I tend to keep lots of old hardware aroung, and will buy a new mobo and chip, then pick around for the rest of the parts.I assume that the only parts that matter with respect to your guidance are mobo/cpu. Is there a way to interrogate hardware to find manufacture dates? 

Also how does one know if it is BIOS or UEFI?

No problem about focus. I did not specify a swap partition, only a system and a home. I intended to do so, but when I got into something else, I got into a muddle trying to create swap and boot. So I just took the easy path which may, or may not, account for my problem.

BTW, I am pretty sure that the 23.28GiB "unallocated" partition showing between sda3 and sda4 was /home yesterday. But for sure it was EXT4.

So how to figure out what went wrong with the first Ubuntu Mate installed Thursday? Does the above tell you what I did wrong with respect to the HDD disappearing? If not, what else would be helpful?

Not making a swap partition may have caused the problem, but if it did, why doesn't gparted show the HDD when I boot up the live CD?

So, for Graham or anyone, any ideas about the missing HDD and failure to boot?

---

### Post by Odyssey1942 on 2016-03-13
Lacking any progress on the immediate previous post, I need to move on to get this matter concluded so I can get back to work.

I seem to have made a complete mess of the SSD, and am not making any progress as to what went wrong, so at this point I want to start over with my first install of Ubuntu Mate (beginning at sda3). I want to leave sda1 and sda2 alone

Here is my plan:

/boot (As I understand it, a boot partition is desireable but do not know what size it needs to be)

/swap (I have 8GB RAM and understand that the swap needs to be larger, but don't know how much larger it should be)

/ (I think that 15GB might be enough, but does it needs to be larger?)

/home (for now on the SSD and later when I figure out what is wrong with the HDD, will move it to the HDD. I am thinking 20GB shuld be enough.)

All partitions (sda3 on) can be changed as they are not now in use. I tried to consolidate those partitions but could not figure out how to do it using Something Else.

I am asking for help in sorting out my mess of partitions and in choosing the size and order that the four partitions above should be set up in Something Else?

---

### Post by oldfred on 2016-03-13
Best not to use a /boot partition with most desktop installs, it adds confusion for many new users. It is required with LVM or full drive encryption and may be required with Server installs.

Do not confuse an UEFI boot partition ESP- efi system partition, which is something else entirely.
You show a bios_grub partition for BIOS boot on gpt partitioned drive. Unless you may want to boot in UEFI mode later, you do not have to have a FAT32 partition for the ESP. I normally put both on all new drives, just so I can use drive for UEFI or BIOS in case I want drive on old or new system.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Odyssey1942 on 2016-03-13
Thank you. 

[http://paste.ubuntu.com/15379788/](http://paste.ubuntu.com/15379788/)

Edit: I should have mentioned that I had already tried to reinstall, first reorganizing the partitions, but I am getting pretty much the same results as before the reinstall, so hopefully this will not be too confusing. (Can't stand waiting and have to try something)

---

### Post by oldfred on 2016-03-14
If you are going to use a /boot partition, you must have one for every install, or else you overwrite the boot of a previous install. Major conflicts then happen.

Are you using auto install option? Best to use Something Else and choose previous / (root) that you do not want anymore.
If you want your three installs, you should just use 25GB for / (root) and a shared data partition. If you really only want one install, you can erase all your partitions and start over.

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[h]("http://askubuntu.com/questions/461394/how-to-partition-ssdhdd")

---

### Post by Odyssey1942 on 2016-03-14
Fred, thanks for yours, but I don't understand it. 

As you can see from the screenshot in OP, sda1 uses 985 Mib. I will call this 1GB. I don't have any idea whether this has anything to do with Gpt, UEFI /boot or any of the other things of which you speak. 

sda2 (the Ubuntu 12.04 install from 2 years ago) uses 37.25 GiB, or 40 GB. So a total of 41GB now used that I wish to retain

The SSD is 120GB, leaving 79GB for a new install (but is now broken up into several partitions which I cannot figure out how to consolidate) to use for the following: install Ubuntu Mate 14.04 now using approx 39GB, then in a few months, install UM 16.04 in the remaining 40GB.

I use Something Else. 

I don't know how to use gpt, or whether I can, or what it is for that matter other than it has to do with the number of partitions you can have.

If this is not clear so far, please tell me what else you need to know. If clear enough, I will appreciate specifics on how to clear up the partition mess, following which we can talk about the new install. Thanks again.

---

### Post by Odyssey1942 on 2016-03-14
Well, I fiddled around in Something Else long enough to finally figure out how to remove the unwanted partitions. Simply highlight each and click on the "-" between "+" and "Change". 

So I wound up with 79GB of free space, so the next step is to determine how best to use the space. For the reasons stated in my previous post, I want to use approx 39GB for the new install.

If I understand OldFred's last post, I do not need a boot partition. Please confirm.

I am very confused about whether I need a /swap at all. Any clarification on this anyone cares to add will be appreciated. (I had previously posted to ask whether my use of too small a swap partition may have put my second drive (a HDD) into permanent hibernation, but no one has addressed that issue.) 

I do know that I need a /.

Once I get the new install done, I will move my /home to a second HDD (after sorting that issue out, replacing it if necessary). So is it better to use the whole 39GB for / and /home, or plan for that now and within the 39GB create a smaller partition for / and a larger for /home, say 15 and 24 respectively?

---

### Post by Dennis N on 2016-03-14
Of your 79 gB, I would make a 4 gB swap partition, and then 1/2 the remainder for / partition. The rest is then left alone for a future installation. You don't need a boot partition at all unless you are using disk encryption. As for me, I never make a separate home partition. It's your option to add one, of course. I think it is an inefficient use of disk space. And moving the separate home partition later to another disk sounds like a tricky operation - something I would not attempt.

With several OS installs, I use a separate data partition which can be mounted and used by each installed OS when it is being used (but it is not the home partition). I would always make a swap partition - 4gB is my standard size.  

Observation: Your first partition is way bigger than necessary for the unformatted bios_grub partition (it only needs about 2 mB), but at this point, I would not bother to change it's size.

With gpt, there are no logical and extended partitions - those options will not be available in the installer. 

Good luck with your new installations.

---

### Post by SeijiSensei on 2016-03-14
I find it useful to have a separate /boot partition on machines where I intend to run multiple operating systems or multiple Linux distributions.  Then grub can enumerate them all and provide the menu of options at startup.  Some people have been reporting problems with [/boot becoming full in recent Ubuntu versions]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1054927").  The general consensus here has been that the Ubuntu installer doesn't allocate enough space to /boot when options like encryption are chosen.  There have been instances where upgrades that include a new kernel image did not completely clear out stale images in the /boot partition, so the installer runs out of space.  Running "sudo apt-get autoremove" occasionally, or when prompted by apt-get, help, but sometimes you need to delete the stale images manually.

On any modern machine with drives of 1 TB or greater, allocating 1-2 GB for /boot might be overkill, but it protects against the problem of running out of space.

---

### Post by oldfred on 2016-03-14
I never have had an issue with grub2's os-prober finding all my installs. I do not use /boot.
In fact I have enough installs I turn off os-prober and only add those I want normally.

My partitions. I also allocate a partition just for ISO on each drive, so I can use that to install to the other drive.
And both drives are not fully partitioned, yet. 
I also keep /home inside / (root) but have all data in my /mnt/data partition.

 Oldfred's current partitions Dec 2015

[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by Odyssey1942 on 2016-03-14
Dennis, thanks for the very clear guidance.

I will leave that sda1 alone because I don't want to touch something that I don't understand. More later.
Will not have /boot
I will plan on 4GB for swap

> With several OS installs, I use a separate data partition which can be mounted and used by each installed OS when it is being used (but it is not the home partitionThis is a big "aha" moment for me. I have always equated /home to data and from yours, this isn't the case. Because I will install UM 14.04 now and in a few months, upgrade to UM 16.04, I just want to be able to leave the user data alone and do my upgrades.

Please elaborate on this and explain how you "link" (maybe wrong word, not intending to be precise) to the data.

> With gpt, there are no logical and extended partitions - those options will not be available in the installer. Another point of confusion to me. Because I don't know whether my mobo/cpu were BIOS or UEFI, that there is a gpt could be the problem with my current unsuccessful attempts to install 14.04. How do I know which I  have for sure?

Thanks again.

Edit: SS's and Freds came in while I was writing the above and I didn't see before posting this. Will digest those two now. Thanks.

---

### Post by oldfred on 2016-03-14
I consider the use of a separate /home on HDD and / (root) on SSD easier for a new user. The mounting, ownership & permissions are done automatically when you install.
And if just converting from an older version to a new version, you can just mount the /home during install, but DO NOT format it or you erase all data. With new install of course you have backed it up anyway.

But you really cannot go back to old install as programs will convert data to newer version, but may not work in older version. I just installed 16.04 and my KeepassX encrypted file changed to a new version not compatible with older versions.

But if wanting to use multiple installs, you should not share /home. Then the separate data partition is better and can be mounted in each install. But you have to manually mount it in fstab, set ownership & permissions so you can use it and I like to link folders into /home so make it easy to use. More complicated, but steps are straight forward. For my own use I found repeating the steps with each install repetitive, so saved my history of commands into a bash file. So then I just run that.

Other threads with oldfred's examples of shared data and discussion by others:
 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by Odyssey1942 on 2016-03-14
Hopefully Dennis will reply further in due course with his input, but in the meantime, OldFred said:

> I consider the use of a separate /home on HDD and / (root) on SSD easier for a new user. The mounting, ownership & permissions are done automatically when you install. And if just converting from an older version to a new version, you can just mount the /home during install, but DO NOT format it or you erase all data.Until I can get some assistance on my disappeared HDD (see OP), I do not have a HDD to replace the existing (but invisible) HDD that went pear-shaped, so cannot put /home on the HDD at this time (that is part of the reason I wrote about it in the OP, i.e., to get it solved simultaneously, and to which Graham took exception.)

I don't quite understand "mount the /home during install". Do you mean that during an additional install (different version, distro, upgrade, etc), and using Something Else, you would identify the /home partition on the HDD as the location of /home for that new install, just don't format the partition? It's the word "mount" that I want to better understand. (Also please remember that you are like a post-grad physics teacher talking to a 5th grader (me) and if you could dumb your comments down quite a few notches, I will be able to better understand. Thanks.)

and
> But you really cannot go back to old install as programs will convert data to newer version, but may not work in older version. I just installed 16.04 and my KeepassX encrypted file changed to a new version not compatible with older versions. I only plan to use Ubuntu Mate as it gives me the Gnome 2 type desktop that I value so highly. Would you expect data incompatibility with upgrades to the same distro?

and
> But if wanting to use multiple installs, you should not share /home. Then the separate data partition is better and can be mounted in each install. But you have to manually mount it in fstab, set ownership & permissions so you can use it and I like to link folders into /home so make it easy to use. More complicated, but steps are straight forward. For my own use I found repeating the steps with each install repetitive, so saved my history of commands into a bash file. So then I just run that. You have written about this before. While I understand you generally, I have no idea HOW to do those things. Again the specifics of HOW in 5th grader language please would be very much appreciated. One thing that might be helpful would be to see your script so that I can try to work through it, changing the lines to suit my situation, and showing it to you for critique?

For clarification, I do not intend to use multiple installs, other than to keep a current working install in place so that I have something to use in case of problems with the next install (as the case here). Once I get a new install running satisfactorily, if that ever happens, I will have no further use for the previous install, just the data, so that might inform your reply.

Also, " set ownership & permissions" sets my knees trembling. I have read the man pages multiple times, various discussions, and tutorials, but just cannot get my meager understanding of the general idea into code that results in what I want to accomplish.

Finally for SeijiSensei, thanks again for your very clear and readable posts which I value highly. On the basis that your approach sounds to me like it is more likely "to take care of itself", I am inclined toward utilizing a /boot space of 2GB. (These things appear simple to OldFred, but I fear they are way over my pay grade.

Assuming that you are referring to something like a disk encryption, rather than something like VeraCrypt, I do not contemplate using it. I do use VC, so if your reference includes it, please advise. 

To summarize, I am just trying (now for over two weeks) to get a working install of Ubuntu Mate in place so that I can get back to work. To the extent that what I do now makes the next upgrade go easier, that is very important. Thanks again.

Edit: For anyone: As I understand it, the sda1 is a gpt partition and is in use by this BIOS computer. Is that correct? And it is probably not creating problems with my current unsuccessful attempts to install UM 14.04?

---

### Post by oldfred on 2016-03-14
First gpt(GUID) is not a partition, but an entire partitioning scheme. Old systems used MBR(msdos) as the partitioning scheme. 
I converted to gpt about 5 years ago for all new drives or totally repartitioned/reformatted drives. Part of reason was eventually I knew I would change to UEFI and then had to have gpt.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) 
    

My script, note that you would not want to rm the existing data folders unless you know they are empty or well backed up. I also create several mount points and NFS setup so I can copy data from one Linux system to another. Comments are # or older code, perhaps my other system. Each command if run separately needs sudo. Since script is run with sudo, no sudo require nor recommended on each line.

```
#!/bin/bash
# linkdata2home.sh
# link data partitions to /home for new install

# make mount points for other partitions
echo $USER

# ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi

# for NFS mount of Laptop
# ! not 
if [ ! -d /mnt/data_LT ]; then
     mkdir /mnt/data_LT
fi

# add user script directory
mkdir ~/bin
chmod 755 ~/bin
#gksudo gedit ~/.bashrc
#Add the following to the end of .bashrc and save:
#PATH="$HOME/bin:$PATH"

mkdir /mnt/data
chown $USER:$USER /mnt/data
#The big "X" will also not make files executable unless they were executable to begin with.Morbius1
chmod a+rwX /mnt/data

# edit fstab to add mounts, UUIDs of data partitions do not change, tmpfs mount for SSD
cp /etc/fstab /etc/fstab.backup
#Edit fstab first Need to change from UUID to labels, so it works on both portable & DT
str1="# Entry for /dev/sdb4 :"
str2="UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2  /mnt/data    ext4         noatime               0  2  "
str3="tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0"
fname=/etc/fstab
echo $str1 >> $fname
echo $str2 >> $fname
echo $str3 >> $fname
# Verify no errors in fstab & remount with new mounts
mount -a

# New install so folders are empty, just delete empty folders
# one line versions I just saw, but have not tested, so just comment for now
# rm -r Documents Downloads Music Pictures Videos
rm -rf Documents/
rm -rf Downloads/
rm -rf Music/
rm -rf Pictures/
rm -rf Videos/

# auto link all folders:
#for i in `echo /usr/local/fred/data`;do ln -s $i; done 
# All folders to be linked in /home are in /data as folders
for i in `echo /mnt/data/*`;do ln -s $i; done

#NFS setup
#/mnt/data 10.0.0.0/24(rw,no_root_squash,async)
#/mnt/shared 10.0.0.0/24(rw,no_root_squash,async)
fname_exp=/etc/exports
nfs1="/mnt/data   192.168.0.0/24(rw,no_root_squash,async)"
#nfs2="/mnt/shared 192.168.1.0/24(rw,no_root_squash,async)"
#nfs1="/mnt/data   10.0.0.0/24(rw,no_root_squash,async)"
#nfs2="/mnt/backup 10.0.0.0/24(rw,no_root_squash,async)"
echo $nfs1 >> $fname_exp
echo $nfs2 >> $fname_exp

exit 0

```

---

### Post by Odyssey1942 on 2016-03-14
Yesterday,  I tried to install UM 14.04 with:
2GB swap
15GB system
22GB home

and it failed. I took a screenshot for whatever it might reveal (see below)

The grub menu only shows the 12.04 install but not the 14.04 at all. If I go down the list and click on 12.04 it starts normally, but if I click on "Ubuntu" at the top of the list, it gave these messages 

Quote:
11.466978 ata4 softreset failed (1st FIS failed)
21.457255 ata4 softreset failed (1st FIS failed)
Gave up waiting for root device. Common problem
--Boot arguments (cat/proc/cmdline) 
--Check rootdelay = (did system wait long enough?)
--Check root = (did system wait for right device?)
--Missing modules (cat/proc/modules; ls/dev)
Alert! dev/disk/by-uuid/ (b98f3c1e-8b77-4aae-8ba7-7c1f4f3ef363) does not exist

Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0 - 1Ubuntu1) built-in shell (ash)
Enter 'help' for list of built-in commands
(initramfs)[56.427211] soft reset failed (1st FIS failed)
[61.422347] ata4: soft reset failed (1st FIS failed)
[61.422382] ata4: soft reset failed (1st FIS failed)

Whew! that took a really long time to hand-write, then type out, so if it is not helpful, please will someone please advise, in which case I will not repeat the exercise in future. Thanks.

Hopefully some of this will be helpful in clueing some of you in to what is the install problem?

Edit: Added uuid #

---

### Post by oldfred on 2016-03-14
Best just to post link to new copy of Boot-Repair's summary report. Not sure why you are having all the issues.
What mode is drive set to in UEFI/BIOS? It should be AHCI, not IDE nor RAID.

---

### Post by Odyssey1942 on 2016-03-14
Fred, Is there a way to find mode from within Live CD, preferably in a GUI, or if CLI, code will be appreciated. Or must one intercept a boot up and go into BIOS?

Also what choices might I find that will help me locate mode? I don't see anything in BIOS that mentions mode.

---

### Post by Dennis N on 2016-03-15
> Please elaborate on this and explain how you "link" (maybe wrong word, not intending to be precise) to the data.

A setup example:

```
Setting Up Separate Data Partition

Here is one system - 2 drives, sda is SSD with 2 OS, and sdb is HDD with the data partition:

[dmn@Zotac ~]$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0    80M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0  24.4G  0 part						#OS 1
&#9500;&#9472;sda3   8:3    0   3.9G  0 part [SWAP]
&#9492;&#9472;sda4   8:4    0  24.4G  0 part /						#OS 2
sdb      8:16   1 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   1 117.2G  0 part /mnt/Common-Files

sdb1 is the data partition. To mount it automatically at startup, /etc/fstab in each OS has these lines added at the bottom (the first line is optional - just a comment):

[COLOR="#FF0000"]# Label=Common-Files at /dev/sdb1
UUID=8395cc9b-002c-4af5-9c49-e5908e4ede74 /mnt/Common-Files ext4 defaults 0 2[/COLOR]

To get the UUID used here, run in terminal [COLOR="#FF0000"]ls -l /dev/disk/by-uuid[/COLOR] and look for the line with sdb1:
[COLOR="#FF0000"]lrwxrwxrwx 1 root root 10 Mar 14 20:16 8395cc9b-002c-4af5-9c49-e5908e4ede74 -> ../../sdb1[/COLOR]

You need to change owner on this file system before you can use it:
[COLOR="#FF0000"]sudo chown -R dmn:dmn /mnt/Common-Files[/COLOR]

To have easy access from the file manager window, browse in the file manager to /mnt and set a bookmark (also called a shortcut) on the folder Common-Files. It's called 'Shortcut' in Thunar, 'Bookmark' in Caja (MATE).

```

---

### Post by oldfred on 2016-03-15
When you say mode, do you mean boot mode or UEFI or BIOS.
That is totally controlled in UEFI/BIOS, if you have a newer UEFI based system.
If UEFI, then you have settings for UEFI with Secure boot, UEFI and CSM/BIOS/Legacy.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
Some may call Secure Boot - Windows and not Secure boot - Other.

And separately when you boot install media, UEFI will give two choices, if secure boot is off, or just secure boot UEFI if secure boot is on.
Unless you install in same mode as system is set to boot then you also may have issues.

If just a BIOS system, you only have the choice to boot in BIOS mode.
But you can still use newer gpt partitioning on drive as I have used gpt on my old BIOS system since about 10.10, my old XP long since retired was still on a MBR drive.

What brand/model system? If it came with Windows 8 or later then it is UEFI.

---

### Post by Odyssey1942 on 2016-03-15
Dennis, I am so grateful for this. So clear and straightforward. I read through OldFred's (for whom I have greatest respect) script but did not understand any of it. As soon as I can get U Mate installed, if ever, I will get another HDD (if needed) and try it with a reinstall. I am not making much progress on the install, or getting to the bottom of the HDD problem, but still slugging away. 

One thing I noted, when I was attempting to get the information that OldFred requested, that the date of the BIOS (American Megatrends) on the computer is 1985-2005 so the mobo may be much older that I would have imagined. That date may be misleading since I have already been running Ubuntu 12.04 and for a day had a very responsive install of Ubuntu Mate, but thought it worth mentioning.

Is there a way to get information on the mobo and cpu via GUI or CLI that might be helpful in diagnosing the problem (which may be BIOS/CPU) instead of SDD?

Edit: OldFred's came in while I was writing the above

Fred > When you say mode, do you mean boot mode or UEFI or BIOS. That is what I was asking you. In your previous post,  you asked me to inform you what mode the  drive set to in UEFI/BIOS? I looked in the BIOS, but did not see anything about drive mode.

My computer is BIOS, not UEFI. Thanks

---

### Post by oldfred on 2016-03-15
Yes, if computer is that old then it is only BIOS.
What mode are drives set then? Should be AHCI, not IDE nor RAID.

Have you installed latest version of BIOS from vendor?
How much RAM and what video card?

---

### Post by Odyssey1942 on 2016-03-15
> Yes, if computer is that old then it is only BIOS. Are you determining age from date on BIOS screen? Here are some additional facts about the system:

AMD Athlon II x4 640 cpu
CPUID/MICROCODE: 0F53/0C8
CPU Frequency: 3.00Ghz (200X15)
BIOS ver. AV17.15 042813
RAM:  frequency for DDR 1333  (Unganged mode 64 bit)  [don't remember seeing "unganged" mode before. Is this significant?]
Cache:  2048KB

> What mode are drives set then? Should be AHCI, not IDE nor RAID. Raid mode was set to ENABLED. I changed it to AHCI. ****see edit

> Have you installed latest version of BIOS from vendor? I doubt that the BIOS has ever been updated. If this is important, I will work on it. Any guidance appreciated.

> How much RAM and what video card?8GB RAM and integrated graphics.

I will appreciate your feedback on these details. Thanks.

EDIT: The computer will not boot in AHCI. It resets the boot order to the SSD (which it cannot seem to find) first then the optical drive and when it attempts to boot, it messages
> No Bootable Device, press any key to reset then it hangs. I tried to reset it to IDE also resetting boot order with same result. Now trying to return it to RAID (which was the setting before I changed it to AHCI) and resetting the boot order. As it went through the RAID drive checking it showed the CD/DVD, but still will not boot the Live CD or the 12.04 that it normally shows in grub. Does not come up in grub at all. Help!

---

### Post by oldfred on 2016-03-15
AHCI is required for SSD.

If drive was in RAID mode, it may have RAID meta-data or system want to use that.
       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
Run chkdsk on any NTFS partitions even if they currently work.
Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Odyssey1942 on 2016-03-15
> Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)AFAIK, windows has never been installed on either the SSD or the HDD.

> Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdbIn both cases, it gives message, "Command not found"
> 
Also check BIOS for raid settingsWould this be in done by booting into BIOS? If not how? If so, what am I looking for?

> Run chkdsk on any NTFS partitions even if they currently work.AFAIK there are no NTFS partitions on the SSD and as you know the HDD is invisible at the moment.

> Most of reasons for installer not showing Windows, any partition type error
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)AFAIK, windows has never been installed on either the SSD or the HDD.

---

### Post by oldfred on 2016-03-16
You have to boot into BIOS and make sure drives are in AHCI mode.

You should be able to run the dmraid command.
But may have to install the dmraid.
sudo apt-get install dmraid

Then run the commands above.
I know they wanted to combine all the RAID into one driver and obsolete dmraid. But I still see dmraid as available in 16.04.

---

### Post by Odyssey1942 on 2016-03-16
returned:
> no raid disks and with names: "/dev/sda"
no raid disks and with names: "/dev/sdb"


I will be going out in an hour or so and would like to pick up a new SSD if necessary. Your early further advice will be most appreciated. Thanks

---

### Post by oldfred on 2016-03-16
I just built new system. New motherboard supports the new M.2 form factor.
I was very surprised when I open box for Samsung 850 M.2 drive and this tiny thing about size of flash drive fell out. 

If you have older system, it may not even support standard form factor SATA drives?

---

### Post by Odyssey1942 on 2016-03-16
Fred, again, I have been using this SSD for two years with the install of Ubuntu Fall-back on sda2. Two Thursdays back, I successfully installed Ubuntu Mate 14.04 into sda3. I don't understand your post at all.

---

### Post by oldfred on 2016-03-16
Just commenting on SSD.
If you did not have SSD on AHCI mode in BIOS that may be part of issue.

---

### Post by Odyssey1942 on 2016-03-17
Have tried to install 14.04 several times in AHCI. No cigar.

---

### Post by oldfred on 2016-03-18
My old BIOS system would only boot Windows XP with AHCI off. But Ubuntu worked with it on or off.
So when I got my first SSD and needed AHCI on for trim to work, I had to shut XP down. :)

---

### Post by Dennis N on 2016-03-18
@Odyssey1942;

I recommend you read this SSD White Paper from Samsung. It contains good information on AHCI and RAID straight to the horse's mouth. 

[http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/whitepaper/whitepaper02.html](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/whitepaper/whitepaper02.html)

The link is part 2 of a larger document. Go to the index to see the other sections.

Hope you get your booting problem solved soon. Did you check the UUIDs in your grub menu entry for MATE? There seems to be something amiss there as suggested by post #17.

Good luck with your new O.S. Ubuntu MATE is an excellent choice.

---

### Post by Odyssey1942 on 2016-03-19
I think I am making progress. When I run the UM 14.04 Live CD installer, it shows:
sda1 as before
sda2 12.04 as before
sda3 14.04

But when I boot the computer, I see a list of options, with "Ubuntu" (no other description) at the top. If I click on it, the computer hangs after putting up messages (see #17)

If I drop down to Ubuntu 12.04 (next to bottom selection), 12.04 boots normally.

14.04 just doesn't show up in this list.

Since it seems to be installed in sda3, I conclude that there is a boot or grub problem. Is there a boot repair or grub repair that might best address the above issue?

---

### Post by Dennis N on 2016-03-19
> But when I boot the computer, I see a list of options, with "Ubuntu" (no other description) at the top. If I click on it, the computer hangs after putting up messages (see #17)

The way the installer works is to put an entry for what it just installed at the top, and _any_ Ubuntu variety is named "Ubuntu". So the top entry is the new one and will boot Ubuntu MATE 14.04. If the Ubuntu 12.04 boots, that seems like a good sign, and the problem is isolated to the booting of Ubuntu MATE.

The first thing I would do is examine the UUIDs in the "Ubuntu" grub menu entry. Select the entry, but press 'e' (to edit) and look at the UUID entries. All of them should be the same, and match the UUID of the partition where you installed its root.

Example lines from a grub menu entry - stuff in red (3 entries) should be identical, stuff in blue should also be identical:

	```
set root='[COLOR="#0000CD"]hd0,gpt3[/COLOR]'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=[COLOR="#0000CD"]hd0,gpt3[/COLOR] --hint-efi=[COLOR="#0000CD"]hd0,gpt3[/COLOR] --hint-baremetal=ahci0,gpt3  [COLOR="#FF0000"]8ff3a810-b4e1-465f-b97c-51d433403bf2[/COLOR]
	else
	  search --no-floppy --fs-uuid --set=root [COLOR="#FF0000"]8ff3a810-b4e1-465f-b97c-51d433403bf2[/COLOR]
	fi
	linux /vmlinuz root=UUID=[COLOR="#FF0000"]8ff3a810-b4e1-465f-b97c-51d433403bf2[/COLOR] ro quiet splash $vt_handoff
	initrd /initrd.img
} 
```

Press ESC to abort and get back to the grub menu.

Check UUID of partition you installed to from ls -l /dev/disk/by-uuid. You can do this from 12.04. It should match too.

```
[dmn@Zotac ~]$ ls -l  /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 Mar 19 03:30 8ff3a810-b4e1-465f-b97c-51d433403bf2 -> ../../sda3

```

I don't know what the other messages in post #17 imply.

---

### Post by Odyssey1942 on 2016-03-19
This is weird. Now the Ubuntu at the top boots into 12.04

When I restart and the grub menu comes up and I press "e" with "Ubuntu" highlighted, it is very different from the first code box in yours. First question, since I am not a good typist, is did you capture the screen, or type it out? If the former, how might I do that from the screen I see? I can take a snapshot of any screen with my phone, but I don't know how to get a photo into a post.

To keep this moving along, I will type out what I found:
> set params 'Ubuntu, with Linux 3.8.0-44-generic'

recordfall
gfxmode $linux_gfx_mode
insmode gzio
insmode part_gpt
insmode ext2
set root='(hdo,gpt2)'
search --no-floppy --fs-uuid --set=root 7fff0116-ceaa-46ad-b43e-233b5e359a58
linux /boot/vmlinuz-3.8.0.44-generic root=uuid=7fff0116-ceaa-46ad-b43e-233b5e359a58
initrd /boot/initrd.img-3.8.0-44-generic
so only one instance of hdo,gpt2
only two instances of the uuid, which do match

should there be more?

---

### Post by Dennis N on 2016-03-19
I copied mine out of /boot/grub/grub.cfg which is the file that makes the grub menu, and I only copied the lines from *set root='hd0,gpt3'* to the end of the entry. I extra stuff you don't have in yours is probably because mine is installed in UEFI mode - a bit of additional code.

The only way I know of take a computer screen shot of the menu screen is to use a virtual machine like VirtualBox.

Looking at yours, the UUIDs match, which is good. hd0,gpt2 means grub should boot from disk 0 (the first disk*) and partition 2, or sda2. The remaining question is "Does the UUID of sda2 match the other UUIDs?" 

You can enter a short command to see the UUID of sda2 (in red). It should match the other two. Here's what the command and output look like on my computer:

```
[18:26 dmn ~]$ ls -l /dev/disk/by-uuid | grep sda2
lrwxrwxrwx. 1 root root 10 Mar 19 18:11 [COLOR="#FF0000"]297ecb14-ecb9-4ddb-8331-0f6c6cb9342f[/COLOR] -> ../../sda2

```
If it matches, then that is good - a wrong UUID does not seem to be the problem. 

Unfortunately, that is as far as my knowledge goes. You need one of the Linux experts around here who would understand the meaning of the other error lines you are seeing and hopefully has ideas what should be done.


*grub counts disks starting with 0, and counts partitions starting with 1.

---

### Post by oldfred on 2016-03-20
The Boot-Repair Summary report dumps most of the info you want on boot.
If first entry is now your 12.04, then you installed that version's grub to MBR of drive.

You can only have one grub in MBR as default boot. And once you boot into any install you can install its grub to MBR if desired.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo parted -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by Odyssey1942 on 2016-03-20
Fred, thanks for yours. Will try as you suggested.

In the meantime, here is output from last night grub repair run

[http://paste.ubuntu.com/15431722/]("http://paste.ubuntu.com/15431722/")

for what it might reveal.

Cannot find > #reinstall from working (not liveCD/DVD/USB) system for Ubuntu Mate. Everything seems to be Live CD. Should I try with Ubuntu 15.10 instead of Mate?

Edit: Fred. I have been searching all this time but cannot find either. Please send a link. Thanks

here is output:
> ubuntu-mate@ubuntu-mate:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1034MB  1033MB                     bios_grub
 2      1034MB  41.0GB  40.0GB  ext4               msftdata
 3      41.0GB  120GB   79.0GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: TSSTcorp CDDVDW SH-222BB (scsi)                                    
Disk /dev/sr0: 1159MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      3717kB  6044kB  2327kB               EFI


and
> ubuntu-mate@ubuntu-mate:~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.
ubuntu-mate@ubuntu-mate:~$ sudo grub-install --recheck /dev/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.
ubuntu-mate@ubuntu-mate:~$ sudo update-grub 
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
ubuntu-mate@ubuntu-mate:~$ 


Edit: for Dennis:

> ubuntu-mate@ubuntu-mate:~$ ls -l /dev/disk/by-uuid | grep sda2
lrwxrwxrwx 1 root root 10 Mar 20 15:24 7fff0116-ceaa-46ad-b43e-233b5e359a58 -> ../../sda2
ubuntu-mate@ubuntu-mate:~$ ^C
ubuntu-mate@ubuntu-mate:~$ 

It matches so no uuid problem

Edit: I decided to try to install Ubuntu (regular not Mate) 15.10 Live DVD. It has been installing ever since, i.e. over an hour so I think that something has gone wrong with the install.  At the bottom of the screen it says:
> Creating ext4 file system for / in partition #3 of SCSI (0,0,0) (sda)Doesn't this normally take only take a very few minutes?

I am reluctant to stop the process since it is making significant changes in lots of basic systems.

So how long should I let it run before trying to stop it?

---

### Post by oldfred on 2016-03-20
It looks like the default repair of Boot-Repair chooses the first install it finds.
You have two and it re-installs grub from sda2 into MBR. So it will be first in boot order.

If you want the install in sda3 first in boot order, either boot it and reinstall grub to MBR as posted above or use Boot-Repair's advanced options and choose the 14.04 install and MBR of sda.

You also show a grub installed to sda3's PBR - partition boot sector. That normally should not be done, but space in partition is not used, so not necessary to remove it. Grub2 also does not like to be installed to a PBR for some that used to do that with grub legacy for chain loading. With grub2 chainloading not required, except for Windows.

---

### Post by Dennis N on 2016-03-20
Looking at your most recent paste on post #40, there is no swap partition on sda. Is that intentional?

---

### Post by Odyssey1942 on 2016-03-21
Fred, If you  could send me a download link to the type of install program you recommended, I will appreciate it.

Dennis, I have re-installed so many times that I have stopped creating boot and swap just to cut down on the time. If I can ever get it to install anything into sda3, I will then go back with a boot, swap and new / to have it the way I want it. But I am getting very discouraged about getting anything installed into sda3

---

### Post by Dennis N on 2016-03-21
I once deleted an existing swap partition, and did not edit the fstab of my OS to reflect the new swap partition I made. As a consequence, when I booted the computer, it was pausing 10 sec during boot waiting for the old swap partition before continuing.   

With no swap, you may get a delay when booting up your Ubuntu 12.04, which probably has a swap set up in its fstab. 

Comment on your repeated installs:

After a number of failures I think I would try a different distro to see how that goes. Or try the latest MATE version 15.10, or even MATE 16.04 beta1. I have installed the latter to test it out and like it. You could also just try the side-by-side option in the installer instead of setting up the partitions yourself.

---

### Post by oldfred on 2016-03-21
I normally use grub to directly boot the ISO with its loopmount, bit more advanced.
I have see all these recommended:

       How to create a bootable Ubuntu USB Flash Drive - unetbootin
[URL="https://help.ubuntu.com/community/USB%20Installation%20Media"]https://help.ubuntu.com/community/USB%20Installation%20Media
[/URL]
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

      
 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)
You can use Win32 Disk Imager to install Ubuntu to a USB pendrive from Windows.
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    [URL="https://help.ubuntu.com/community/USB%20Installation%20Media"]
[/URL]

---

### Post by Odyssey1942 on 2016-03-21
Fred, thank you for all that good information on USB installations. I will keep that for future reference.

For now, in post # 39, you said:> #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):

I am asking you for a link to just such a "working (not liveCD/DVD/USB) system" Thanks in advance

---

### Post by oldfred on 2016-03-21
A working system is your install.
If your grub offers dual boot, or 12.04 is at top of menu and 14.04 at bottom of menu, then boot into 14.04 and install its copy of grub to MBR, so next time you boot 14.04 will be at top of menu.
 sudo grub-install /dev/sda

But if from a live installer, you have to mount partition with install & then install to MBR. Easier with Boot-Repair in that case, but you could also use Boot-Repair and its advanced options from any of your working installs.

---

### Post by Odyssey1942 on 2016-03-21
Now a Monday and three weeks and 3 days into my attempt to add Ubuntu Mate to the existing Ubuntu Fall-back 12.04, I see no future in continuing this incredibly frustrating exercise. As you can tell, I am like a bulldog with a bone, but I think there is nothing left of the bone.

So, with reluctance to quit, but being realistic, I would just like to thank all those who have tried to help me through this, especially OldFred, DennisN, SeijiSensei, and grahammechanical (and anyone else who deserves special mention, but I have not remembered). You have really racked your brains to find a solution and I am very grateful for your many suggestions.

Time to replace this SSD with a new one, and put the older one into another older spare machine to get back to later in case I get another case of computer masochism.

Best wishes,
robert

---

### Post by Odyssey1942 on 2016-03-28
Couldn't leave it alone.

I disconnected the ersatz HDD and installed a different SSD. 

Then installed U Mate 14.04 into that SSD. Ran like a champ. Played around with it for awhile to confirm all rosy. In retroAs a result of the great suggestionsspect, if I had been thinking, would have then reconnected the HDD and rebooted, to take this one element at a time in order to isolate what was causing the problem, but did not think of it then.

Leaving the questionable HDD still disconnected, replaced the new SSD with the problem SSD and deleted the existing 1GiB sda1 using gparted in U Mate Live session.

Then deleted all other partitions except sda2 (with 12.04 on it). It did something which I don't understand. It left the old sda1 as an unallocated space of 986MiB and showed the old sda3 and sda4 as a new unallocated space of 73.57GiB. Don't understand why it did not combine them? Is this due to some special properties of that sda1 area?

Installed U Mate 14.04 from live desktop and rebooted. The grub menu came up with "Ubuntu" at the top and Ubuntu 12.04 at the bottom of the list. Selected the top choice and it booted into Ubuntu Mate 14.04 running well.

Then reconnected the ersatz HDD and booted up into the same old problem that I had been looking at for the last 3 weeks. It was the HDD mucking things up. I disconnected it and Ubuntu Mate is running well again.

Thought those who contributed to the eventual solution might be interested in an update. As a result of the great suggestions and education you have all provided, I have lifted my level of confidence enormously and my competence in a few areas a goodly bit. Thanks again.

---

### Post by Dennis N on 2016-03-28
Well, glad to learn this all got sorted out. Now you can make that separate data partition as your next project.

> Then deleted all other partitions except sda2 (with 12.04 on it). It did something which I don't understand. It left the old sda1 as an unallocated space of 986MiB and showed the old sda3 and sda4 as a new unallocated space of 73.57GiB. Don't understand why it did not combine them? Is this due to some special properties of that sda1 area?

When you remove partitons, the disk sectors (each taking a section of the disk's surface) that the partitions were written on are still there on on the disk but now called unallocated space. sda2 uses specific disk sector numbers, and stays on the same sectors. The sectors never move.

simplified example with a 400 sector disk - each sector a little section of the disk surface:

original partitions:

sectors 1-99 used by sda1
sectors 100-199 used by sda2
sectors 200-299 used by sda3
sectors 300-399 used by sda4

when partitions sda1, sda3, sda4 are deleted, sectors 1-99, 200-399 are now unallocated (unused) but still take up the same disk space, divided from each other by sectors 100-199, still in use as sda2 (your 12.04 os)

Good luck with your next project.

---

### Post by Odyssey1942 on 2016-03-28
Dennis, thanks for yours. That is entirely logical and now I understand why it did not consolidate.

Co-incidental that you should post as I am in process of following your very instructions as to data location. I am stuck in my notes of those instructions on the subject: ```
sudo chown -R dnm:dmn /mnt/Common-Files
```Have even read through the man pages, but as usual they might just as well be written in Greek.

From the man pages, I see that dnm:dmn is user:group, but what is dnm? 

In my case in that command line, I should just put my user name in both, i.e., username:username? (this of course assuming that I am the only one who will ever see the files)

Also, FWIIW, the file browser/Places shows the UUID of the device at the very top of its little window when you click on it after mounting, and if you right-click it and choose properties it shows the UUID. You doubtless know that, but for the rest of us CLI-challenged noobs who would otherwise have to look up the command you gave, it is right there in a GUI with one or two clicks

---

### Post by oldfred on 2016-03-28
I use  these command, but they only work on Linux formatted partitions not NTFS nor FAT32.
This example is to reset /home to typical defaults, but I use same permissions & ownership for all my data partitions.
 sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER 

Your example must have had a user whose name was drm?
If you want to know what $USER is:
      
 echo $USER 
And that should just be you, which you can use instead.

---

### Post by Dennis N on 2016-03-28
> From the man pages, I see that dnm:dmn is user:group, but what is dnm?
First, I made a typo in the post (will fix if still possible) - should be dmn:dmn which is my user name and group. 

> In my case in that command line, I should just put my user name in both, i.e., username:username? (this of course assuming that I am the only one who will ever see the files)
Yes, that's it.

> Also, FWIIW, the file browser/Places shows the UUID of the device at the very top of its little window when you click on it after mounting, and if you right-click it and choose properties it shows the UUID.
This is in Ubuntu MATE?

---

### Post by Odyssey1942 on 2016-03-29
Thanks to both.

Fred, is it not the same username that appears before the "@" on the CLI just before where commands are entered?

Dennis, yes Ubuntu Mate. Is it not the same in vanilla Ubuntu?

Also, I have added the two lines (including the remark first line) to fstab, so when I reboot "Common-files" will be mounted.

However, I am at a bit of a loss as how to set up sdb1. Do I make a folder called "Common-files" on sdb1 and create identical data folders to those under /home (at least to the extent that I use the folders, i.e. if I don't use Music on this computer, no need to set up a Music folder on sdb1) and transfer the contents of the backup DVD I made to each respective folder. Or should the top folder have another name? Or what?

And how to tell the U Mate to use "Common-files" instead of /home? Is "Common-files" a term that linux uses or is that one you made up? If the former, then the mount command will take care of that? If the latter, I don't understand why U Mate will start using it instead of the existing /home on sda3?

Apology for my confusion, but as you can see, I am still a noob.

---

### Post by oldfred on 2016-03-29
With Linux you create your own mount point with whatever name makes sense to you. 
I use /mnt/data, but have used /mnt/shared. Some use multiple mounts for different data. 
In Windows you get "D" drive with no description. 

The main part of the forum only supports official "flavors" of Ubuntu. Others are in sub-forums as we are not sure of differences.
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

Several threads with comments on setting up separate data partition.
 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and detail steps in post #4:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Dennis N on 2016-03-29
> Do I make a folder called "Common-files" on sdb1?

If you added the suggested lines in post #20 to fstab, this folder will be created and be there next time you boot the OS. If you browse to /mnt and open it in file manager you will see Common-Files. You should have changed owner and group of this folder as shown in the example of post #20. You can set a bookmark (shortcut) so that it shows in the File Manager side pane and can click on the bookmark to directly access the Common-Files folder. You can add more folders inside Common-Files with whatever names you like to store files which will then be accessible to any other OS on the computer. And you can optionally make additional bookmarks to some of those folders.

I don't make any links from the data folder (Common-Files) to my home folder of the OS. Some like to do that, but I see no reason to. Your choice.

Note: Some may say you need to create the folder mounted in fstab yourself as well as adding the entry. I found that you don't really need to do that with fstab entries. And as pointed out, you don't need to use my name choice for the folder - pick a name of your choosing.

---

### Post by Odyssey1942 on 2016-03-29
"Common-files" is as good as any for me and that will be at least two of us using it.

>  You should have changed owner and group of this folder as shown in the example of post #20Am asking about this to make sure I understand. You said "should have" but I assumed that the folder would need to be set up before I can change owner and group. If that should have read to this effect, no reply needed, but if it is something that I should have already done, will need some guidance.

---

### Post by Dennis N on 2016-03-29
> **Odyssey1942 said:**
> "Common-files" is as good as any for me and that will be at least two of us using it.

Am asking about this to make sure I understand. You said "should have" but I assumed that the folder would need to be set up before I can change owner and group. If that should have read to this effect, no reply needed, but if it is something that I should have already done, will need some guidance.

Yes, you are right. I change the owner and group right after I add the needed lines to fstab and have rebooted. You can then change owner:group with the terminal command. _After_ doing this, you browse to /mnt with the file manager, set a bookmark for the Common-Files folder; you can then open Common-Files, add new folders inside it, save files, make more bookmarks, and so on. You could also make a desktop shortcut(s) for quick access.

You need to repeat the whole process for the other OS (you do have two?) so that when you are using it, you have access to the same data.

---

