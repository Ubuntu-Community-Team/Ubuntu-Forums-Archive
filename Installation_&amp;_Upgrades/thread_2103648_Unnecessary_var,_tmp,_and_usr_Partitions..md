---
title: "Unnecessary var, tmp, and usr Partitions."
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by BlinkinCat on 2013-01-10
Hi all,

I have been reading the progress of the following thread with interest.
[http://ubuntuforums.org/showthread.php?t=2103607](http://ubuntuforums.org/showthread.php?t=2103607)

I am in the situation whereby after reading some of the available documentation, I inadvertently created my 12.04.1 installation with var, tmp, and usr partitions thinking I was doing the right thing. Everything is working fine, however I have been toying with the idea of starting again. Things to be considered -

Is it really worthwhile to change it now it has been done this way ?
I fear that I may mess up the process of changing the partitions either by Gparted of with the Partitioning tool. I assume Gparted would be the logical choice - If I chose that option would have any problems with the procedure - What would I actually do ?

At the EOL of Xubuntu 12.04 I may have to make a decision to change things around however at the moment I am really tempted to leave it as it is, but I am open to any suggestions.

Edit: Does it matter that I have / before /boot ? 

Cheers and thanks - :)

---

### Post by JKyleOKC on 2013-01-10
> **BlinkinCat said:**
> Hi all,

I have been reading the progress of the following thread with interest.
[http://ubuntuforums.org/showthread.php?t=2103607](http://ubuntuforums.org/showthread.php?t=2103607)

I am in the situation whereby after reading some of the available documentation, I inadvertently created my 12.04.1 installation with var, tmp, and usr partitions thinking I was doing the right thing. Everything is working fine, however I have been toying with the idea of starting again. Things to be considered -

Is it really worthwhile to change it now it has been done this way ?I wouldn't bother. The only disadvantage to your present setup is simply that you may have mis-estimated the amount of space to allocate to each partition, so you could run out of disk space unexpectedly. By having all of them share the main "/" partition the system will, in effect, rob Peter to pay Paul when it needs to.

The var partition is the one most likely to fill, since that's where all the log files are stored. If you run into a situation that creates multiple GB of log data, /var may not be large enough to hold it. Next most likely to give a problem is /tmp. The /usr partition doesn't usually change in size very much, unless you keep adding new software to the system without getting rid of obsolete stuff.
> **BlinkinCat said:**
> 
I fear that I may mess up the process of changing the partitions either by Gparted of with the Partitioning tool. I assume Gparted would be the logical choice - If I chose that option would have any problems with the procedure - What would I actually do ?
I'll leave this question for OldFred or another poster more expert than I am at re-partitioning to answer. 
> **BlinkinCat said:**
> At the EOL of Xubuntu 12.04 I may have to make a decision to change things around however at the moment I am really tempted to leave it as it is, but I am open to any suggestions.I'll be interested in others' comments, too. My systems are always set up with just three partitionsL "/", "swap", and "/home." I give 10 GiB to /, RAM size plus 10% to swap, and the rest of the disk no matter its size to /home. My current boxes both have 500-GB drives but one of them dual-boots with Win7 (just in case I ever need it; I don't use it as a rule) so its drive is effectively only about 220 GiB.

---

### Post by BlinkinCat on 2013-01-10
Hi Jim,

Thank you for your assurance - at this stage I am thinking that a change may absolutely have to be made 2 1/4 years from now. I also run Unity and Gnome shell and figure I may have to make a critical choice at that time as 12.04 Unity will still have a considerable time to run to EOL. At this stage I am enjoying Xubuntu but decisions will have to be made at that time.

I appreciate your input Jim and have taken note of it. - :P

---

### Post by BlinkinCat on 2013-01-10
Hi again,

I have thought of another scenario. As the time period into the EOL is relatively early, perhaps any changes would be better made sooner rather than later. Therefore if I was to back up the system (rather crudely in my case via thumb drives) could I wipe the HD clean via Disk Utility and reformat partition to MBR. Is it possible to do this by firstly un-mounting the drive and then Formatting.
Does Gparted do the same thing ? I am not sure how this is achieved.

Any help would be appreciated.

---

### Post by CharlesA on 2013-01-10
If you want to redo the allocation, you should be able to copy the stuff from /usr, /var and /tmp to your home directory, unmount those partitions, then copy the files back in (using sudo rsync -a or sudo cp -a) and then comment out the lines for those mounts in fstab.

After you mess with fstab and make sure the system boots ok, expand the / partition and you should be good.

It sounds more complicated than it is, but I have not actually done it in practice.

However, if you do it that way, you would not need to reinstall. I would suggest running the commands from a livecd, so the OS isn't running while you are messing with stuff.

---

### Post by BlinkinCat on 2013-01-10
Hi Charles,

I had to go out for 20 minutes or so and have only just now got back.

You are dealing with a very unskilled operator here Charles - Your directions have confused me some-what. From what I understand I need to copy the contents of each partition to cd ?
Could you give me the commands for one ?
Secondly could you give me the command for copying the file back in for one example ?
Thirdly I have never dealt with fstab before - could you kindly enlighten me ?

I apologize for being such a pain Charles - you can see my knowledge is very limited. If you can guide me further I will be extremely grateful.

Nevertheless, I would prefer to tackle the problem this way, as I will be learning something and the alternative would mean  losing over 330 GiB Videos.

Edit - I have attempted to learn more about fstab via the "Introduction to fstab" but find it difficult to understand practical examples.

Step 1. 
  mv /usr cd  ?
              mv /var cd ?
              mv /tmp cd ?

Step 2.
Unmount each partition ?

Step 3 ?

Step 4 ?

---

### Post by CharlesA on 2013-01-11
No, not like that. You'd want to copy anything in those folders to another place such as your home directory and then mess with fstab.

First off, let's get a idea of what your disk looks like. Run these and post the output:

```
sudo blkid -c /dev/null
sudo fdisk -l
df -h
```

---

### Post by BlinkinCat on 2013-01-11
Sorry for the delay Charles, but no doubt we will catch up again - Thanks very much for your help.

```

geoff@ABC:~$ sudo blkid -c /dev/null
[sudo] password for geoff: 
/dev/sda1: UUID="a50390f0-0910-48db-9941-89a0ab7ffa29" TYPE="ext4" 
/dev/sda2: UUID="3ac4709e-9e4d-4a5b-9da5-d88f78e35402" TYPE="ext4" 
/dev/sda3: UUID="6d64bcaf-c555-400b-b8bc-7516d0b3fdf3" TYPE="ext4" 
/dev/sda5: UUID="51c8465d-0f8c-407a-9c0c-11c610aaea6b" TYPE="ext4" 
/dev/sda6: UUID="f5707e5c-41a3-4e55-97aa-ea5f48f75767" TYPE="ext4" 
/dev/sda7: UUID="2c358f65-b1aa-42ba-9a87-8985d86d5266" TYPE="swap" 
/dev/sda8: UUID="aa2e6274-590d-4e9a-a199-d9aef3b38637" TYPE="ext4" 
geoff@ABC:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    19533823     9765888   83  Linux
/dev/sda2   *    19533824    20512767      489472   83  Linux
/dev/sda3        20512768    36141055     7814144   83  Linux
/dev/sda4        36143102  1953523711   958690305    5  Extended
/dev/sda5        36143104    43956223     3906560   83  Linux
/dev/sda6        43958272    63492095     9766912   83  Linux
/dev/sda7        63494144    79120383     7813120   82  Linux swap / Solaris
/dev/sda8        79122432  1644865535   782871552   83  Linux
geoff@ABC:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       9.2G  1.3G  7.6G  14% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           775M  876K  774M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  160K  1.9G   1% /run/shm
/dev/sda6       9.2G  150M  8.6G   2% /tmp
/dev/sda2       463M  147M  293M  34% /boot
/dev/sda8       735G  337G  362G  49% /home
/dev/sda3       7.4G  3.3G  3.8G  47% /usr
/dev/sda5       3.7G  731M  2.8G  21% /var
geoff@ABC:~$ 

```

---

### Post by Pjotr123 on 2013-01-11
I advise a clean reinstall. With only a partition for / and a partition for swap. Further partitions are, in my opinion, a needless complication. I even advise against the false security of a separate /home:
[https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-)
(item 15, right column)

That's the most economical way to use the space on a hard drive, in my opinion. You don't lose much to the swap partition, because that only needs to be a littlle bigger than the size of your RAM. :)

---

### Post by BlinkinCat on 2013-01-11
> **Pjotr123 said:**
> I advise a clean reinstall. With only a partition for / and a partition for swap. Further partitions are, in my opinion, a needless complication. I even advise against the false security of a separate /home:
[https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-)
(item 15, right column)

That's the most economical way to use the space on a hard drive, in my opinion. You don't lose much to the swap partition, because that only needs to be a littlle bigger than the size of your RAM. :)

Hi and thanks for your input Pjotr123,

My main requirement for having a /home partition was for the retention of a reasonable number of video files. I am not sure of how to go about a fresh install and to retain those files. If I can get rid of /usr, /var and /tmp I will be happy.

Cheers - :p

---

### Post by dino99 on 2013-01-11
i'm always surprised by these new users, having read here and there but mostly outside ubuntu wikis, non standard and/or outdated (very outdated) procedures.
Why they does not follow the default howto proposed by the installer ? that's a mystery  ;)

---

### Post by BlinkinCat on 2013-01-11
> **dino99 said:**
> i'm always surprised by these new users, having read here and there but mostly outside ubuntu wikis, non standard and/or outdated (very outdated) procedures.
Why they does not follow the default howto proposed by the installer ? that's a mystery  ;)

I guess that it is a pity that there remains so much literature surrounding Ubuntu that clouds the issue. I can not even quote where I obtained the information now, but it seemed to make sense at the time.  It sure is embarrassing to come out in public when you wish to do something about rectifying the situation. 

Cheers - :p

---

### Post by Pjotr123 on 2013-01-11
> **BlinkinCat said:**
> It sure is embarrassing to come out in public when you wish to do something about rectifying the situation.

No need for embarrassment; we all experiment and make mistakes in the process. Experimenting is part of the fun of Linux. :)

In my opinion a separate /home is useless, because for real safety you need an *external* backup of your valuable files anyway. On an external medium, like an external USB hard disk.

Two partitions (one for / and one for swap) is the Ubuntu default, which in my opinion is a very sensible choice of the Ubuntu developers :)

---

### Post by BlinkinCat on 2013-01-11
> **Pjotr123 said:**
> No need for embarrassment; we all experiment and make mistakes in the process. Experimenting is part of the fun of Linux. :)

In my opinion a separate /home is useless, because for real safety you need an *external* backup of your valuable files anyway. On an external medium, like an external USB hard disk.

Two partitions (one for / and one for swap) is the Ubuntu default, which in my opinion is a very sensible choice of the Ubuntu developers :)

Do I not also need a /boot partition ?  - :)

---

### Post by dino99 on 2013-01-11
> **BlinkinCat said:**
> Do I not also need a /boot partition ?  - :)

comments:

do i need a /home partition ?
despite the post above, i should always answer: yes , even if backing (time to time) on an external device is also a good choice. But saying that /home partition is quite useless, is not the expected answer.

do i need a /boot ?
at first glance : no , but you will need one with some new config (gpt/uefi). So if you are concerned, then google around "ubuntu grub /boot"

---

### Post by BlinkinCat on 2013-01-11
> **dino99 said:**
> comments:

do i need a /home partition ?
despite the post above, i should always answer: yes , even if backing (time to time) on an external device is also a good choice. But saying that /home partition is quite useless, is not the expected answer.

do i need a /boot ?
at first glance : no , but you will need one with some new config (gpt/uefi). So if you are concerned, then google around "ubuntu grub /boot"

Thanks for your input dino99 - you have been of assistance. For this old man, sometimes it is difficult to come to the right conclusion. I would like to search out some books that would help me with the various aspects of linux.

Cheers - :p

---

### Post by Pjotr123 on 2013-01-11
> **BlinkinCat said:**
> Do I not also need a /boot partition ?  - :)

Highly unlikely. I suggest you try first without one; if you can boot, you're allright. :)

---

### Post by BlinkinCat on 2013-01-11
> **Pjotr123 said:**
> Highly unlikely. I suggest you try first without one; if you can boot, you're allright. :)

Thanks Pjotr123 - I will take what you say onboard, however as I was relying on CharlesA to get rid of /usr, /var and /tmp I will wait to get further input from him. Even in the short discussions on this thread we have differing viewpoints, which only tend to confuse matters to me. It seems with all of the available documentation there are still issues of non-standardization. I am leaning towards reducing the partitions by three, If I can achieve that I believe I will be content - but time will tell.

Thanks to dino99 also.

Cheers - :)

---

### Post by Pjotr123 on 2013-01-11
> **BlinkinCat said:**
> Even in the short discussions on this thread we have differing viewpoints, which only tend to confuse matters to me. It seems with all of the available documentation there are still issues of non-standardization.
Often there are many ways to achieve a goal, neither of which is wrong.... As in this case. You can choose the one you like best. :)

Personally, I tend to favour the way that I think is the most simple. Simple systems are the most reliable and bother-free in the long run, is my experience...

---

### Post by BlinkinCat on 2013-01-11
> **Pjotr123 said:**
> Often there are many ways to achieve a goal, neither of which is wrong.... As in this case. You can choose the one you like best. :)

Personally, I tend to favour the way that I think is the most simple. Simple systems are the most reliable and bother-free in the long run, is my experience...

Thanks very much for your input Pjotr123  -  :p

---

### Post by CharlesA on 2013-01-11
> **Pjotr123 said:**
> Often there are many ways to achieve a goal, neither of which is wrong.... As in this case. You can choose the one you like best. :)

Personally, I tend to favour the way that I think is the most simple. Simple systems are the most reliable and bother-free in the long run, is my experience...

What they said. ;)

> **BlinkinCat said:**
> Thanks Pjotr123 - I will take what you say onboard, however as I was relying on CharlesA to get rid of /usr, /var and /tmp I will wait to get further input from him. Even in the short discussions on this thread we have differing viewpoints, which only tend to confuse matters to me. It seems with all of the available documentation there are still issues of non-standardization. I am leaning towards reducing the partitions by three, If I can achieve that I believe I will be content - but time will tell.

Thanks to dino99 also.

Cheers - :)

This will be.. interesting. I found this: [http://outhereinthefield.wordpress.com/2008/02/02/moving-usr-var-to-another-partition/](http://outhereinthefield.wordpress.com/2008/02/02/moving-usr-var-to-another-partition/)

But I do not know if it will be all that helpful.

I would recommend doing the next part from a livecd instead of a running system, so there is nothing writing to the partitions while you move things around. It would also be a good idea to backup the stuff in /home because messing with partitions isn't foolproof.

Once you have booted off the livecd, run these commands from a terminal:

```
cd && mkdir root tmp boot usr var

# Mount /
sudo mount -t ext4 UUID=a50390f0-0910-48db-9941-89a0ab7ffa29 ~/root

# Mount /tmp
sudo mount -t ext4 UUID=f5707e5c-41a3-4e55-97aa-ea5f48f75767 ~/tmp

# Mount /boot
sudo mount -t ext4 UUID=3ac4709e-9e4d-4a5b-9da5-d88f78e35402 ~/boot

# Mount /usr
sudo mount -t ext4 UUID=6d64bcaf-c555-400b-b8bc-7516d0b3fdf3 ~/usr

# Mount /var
sudo mount -t ext4 UUID=51c8465d-0f8c-407a-9c0c-11c610aaea6b ~/var
```

Verify with df -h and/or blkid:
```
df -h "should" look like this:

/dev/sda1       9.2G  1.3G  7.6G  14% /home/ubuntu/root
/dev/sda6       9.2G  150M  8.6G   2% /home/ubuntu/tmp
/dev/sda2       463M  147M  293M  34% /home/ubuntu/boot
/dev/sda3       7.4G  3.3G  3.8G  47% /home/ubuntu/usr
/dev/sda5       3.7G  731M  2.8G  21% /home/ubuntu/var
```

Once you have verified that is right, proceed with the copy - I added the dry-run switch so you can verify the copy will work before actually doing it for real.

```
# Copy
sudo rsync -ai --dry-run ~/tmp ~/root/
sudo rsync -ai --dry-run ~/boot ~/root/
sudo rsync -ai --dry-run ~/usr ~/root/
sudo rsync -ai --dry-run ~/var ~/root/
```

Verify with ls

Comment out the lines that are mounting /tmp, /boot, /usr and /var in fstab:

```
nano /home/ubuntu/root/etc/fstab
```

unmount everything and you should be good to go to reboot.

---

### Post by forkandles on 2013-01-11
> I would like to search out some books that would help me with the various aspects of Linux.


Personally I would not bother buying books on Linux, which are usually written for a very broad audience and they are frequently not up-to-date with current develoments. I suggest that you borrow one or two from the library, or from Linux-using friends. Save your cash for some hardware. 

In my opinion it is much easier (and cheaper) to use online tutorials and forums such as UF to access the **specific area or problem you need to target.**

These are just a few:

Guide to Ubuntu 12.04:
[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)

Command line:
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Package management with APT:
[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto)

---

### Post by BlinkinCat on 2013-01-11
Hi Charles, I really appreciate your help, - :)

I will back up as much as I can.

I am a little confused about "how I Unmount everything"

Could you give me an example please ?

Edit - For Example, would I Unmount / like this ?

sudo umount -t ext4 UUID=a50390f0-0910-48db-9941-89a0ab7ffa29 ~/root

Also, how do I operate the "dry-run" switch ?

---

### Post by jbeiter on 2013-01-11
I'm old school unix and would still put var and perhaps tmp on their own partitions.

The only reason I would suggest redoing it is if you did not put /home on it's own partition.

Keeping your home directory on a unique partition will let you get through many upgrades of ubuntu without loosing your stuff. I've had the same physical home directory since version 9 and I have never "upgraded".. I've always formatted the system partitions.

---

### Post by BlinkinCat on 2013-01-11
> **jbeiter said:**
> I'm old school unix and would still put var and perhaps tmp on their own partitions.

The only reason I would suggest redoing it is if you did not put /home on it's own partition.

Keeping your home directory on a unique partition will let you get through many upgrades of ubuntu without loosing your stuff. I've had the same physical home directory since version 9 and I have never "upgraded".. I've always formatted the system partitions.

Thanks for your comments jbeiter - to be honest I am a little confused about the right way to go although it seems the majority these days favour a trimmer system. I haven't started the alteration yet, until I get my questions answered by CharlesA. I am definitely retaining /home.

Cheers - :p

Edit - Thanks to forkandles for his links too! They look great!

---

### Post by CharlesA on 2013-01-11
> **BlinkinCat said:**
> Hi Charles, I really appreciate your help, - :)

I will back up as much as I can.

I am a little confused about "how I Unmount everything"

Could you give me an example please ?

Edit - For Example, would I Unmount / like this ?

sudo umount -t ext4 UUID=a50390f0-0910-48db-9941-89a0ab7ffa29 ~/root

sudo umount /path/to/mountpoint, so it would look like this when you are done:

```
sudo umount /home/ubuntu/tmp
sudo umount /home/ubuntu/boot
sudo umount /home/ubuntu/usr
sudo umount /home/ubuntu/var
```

> Also, how do I operate the "dry-run" switch ?

You can run a dry-run first, where it will tell you what it will do, but not actually copy anything, when you are sure it looks right, you can remove -dry-run and it will copy everything where you tell it to.

I would unmount everything except ~/root and run df -h to make sure everything copied ok before unmounting it. Be sure to edit fstab before you unmount /root ;)

---

### Post by JKyleOKC on 2013-01-11
> **Pjotr123 said:**
> In my opinion a separate /home is useless, because for real safety you need an *external* backup of your valuable files anyway. On an external medium, like an external USB hard disk.Obviously from my earlier post in this thread I disagree that a separate /home is useless, but I don't consider it to be in any way associated with "real safety." My purpose for having it is to permit me to do a (semi)clean install of a new long-term-support version every few years without having to copy dozens of gigabytes of virtual machine files back from backups.

Since BlinkinCat has not dozens, but hundreds, of GB of video files there, that's adequate reason for him to keep one also.

For safety, nothing can replace an external backup, but for such a large partition flash drives aren't really practical. Only an external hard drive, at least as large as the one in the main machine, will do. It can connect via USB and if reformatted to a Linux file system such as ext4 will do a great job. From the store, such drives are usually formatted as NTFS to be compatible with Windows, and this system won't preserve all Linux file attributes -- but even without reformatting, the drive can hold your data including video safe...

---

### Post by BlinkinCat on 2013-01-11
> **CharlesA said:**
> sudo umount /path/to/mountpoint, so it would look like this when you are done:

```
sudo umount /home/ubuntu/tmp
sudo umount /home/ubuntu/boot
sudo umount /home/ubuntu/usr
sudo umount /home/ubuntu/var
```You can run a dry-run first, where it will tell you what it will do, but not actually copy anything, when you are sure it looks right, you can remove -dry-run and it will copy everything where you tell it to.

I would unmount everything except ~/root and run df -h to make sure everything copied ok before unmounting it. Be sure to edit fstab before you unmount /root ;)

Thanks Charles - that helps a lot - I will be taking the plunge shortly - ;)

---

### Post by CharlesA on 2013-01-11
> **JKyleOKC said:**
> Since BlinkinCat has not dozens, but hundreds, of GB of video files there, that's adequate reason for him to keep one also.

For safety, nothing can replace an external backup, but for such a large partition flash drives aren't really practical. Only an external hard drive, at least as large as the one in the main machine, will do. It can connect via USB and if reformatted to a Linux file system such as ext4 will do a great job. From the store, such drives are usually formatted as NTFS to be compatible with Windows, and this system won't preserve all Linux file attributes -- but even without reformatting, the drive can hold your data including video safe...

+1. I have my server backed up to external media daily/monthly as well as to the cloud, so I have an offsite backup.

However, I only back up my RAID array, not my home directory because I store anything important on the RAID array. ;)

> **BlinkinCat said:**
> Thanks Charles - that helps a lot - I will be taking the plunge shortly - ;)

Good luck!

---

### Post by BlinkinCat on 2013-01-11
Hi again Charles,

One more thing - do I unmount root like sudo umount /home/ubuntu/root ?

It has become a little confusing to read with all the spread out posts -:)

With kind regards BlinkinCat.

---

### Post by CharlesA on 2013-01-11
Yes.

Reboot and it should come up ok.

If not, you can boot off the livecd and we can go from there.

---

### Post by arpanaut on 2013-01-11
Purely personal opinion here!
But until you have what you consider important and cannot afford to lose, backed up to external media, I would tread softly here.
Re-partitioning can and does go wrong, one little slip in command line syntax, power failure, or system lock up could leave you very sorry.

Once you get those partitions moved back into / (root) things are going to get tight for space there and you will probably need to add the unallocated space from /boot and /usr into the root part. another step with possible failure.  
Now all of this may go as planned, but it may not...  on a production, can't loose system are you prepared for the consequences?

Just some food for thought.

---

### Post by BlinkinCat on 2013-01-11
> **CharlesA said:**
> Yes.

Reboot and it should come up ok.

If not, you can boot off the livecd and we can go from there.

Thanks for that Charles and as your quote says -

"today is a solution"

---

### Post by CharlesA on 2013-01-11
> **arpanaut said:**
> Purely personal opinion here!
But until you have what you consider important and cannot afford to lose, backed up to external media, I would tread softly here.
Re-partitioning can and does go wrong, one little slip in command line syntax, power failure, or system lock up could leave you very sorry.

Agreed. I think they should have around 2-4GB of wiggle room after everything is moved over, but I would definitely back up everything in /home up before messing with partitions.

> Once you get those partitions moved back into / (root) things are going to get tight for space there and you will probably need to add the unallocated space from /boot and /usr into the root part. another step with possible failure.  
Now all of this may go as planned, but it may not...  on a production, can't loose system are you prepared for the consequences?

Indeed. See above ^.

---

### Post by BlinkinCat on 2013-01-11
> **CharlesA said:**
> Agreed. I think they should have around 2-4GB of wiggle room after everything is moved over, but I would definitely back up everything in /home up before messing with partitions.

Well gentlemen, I may then be wise to get a proper backup of home before I proceed.
Other than around 300 movies, my data has been rather small. I have until now been content to do 2 flashdrive backups a month.

Even the movies I believe I would be prepared to lose, however I will proceed to ask questions on the General Help Forum about the possibility of obtaining a back up. I don't even know if it is a practical proposition to backup around 330 GiB movies (time wise)
I only have a 250GiB External HD at this stage. - Would have to purchase another one.  

Regards - :p

---

### Post by CharlesA on 2013-01-11
> **BlinkinCat said:**
> Even the movies I believe I would be prepared to lose, however I will proceed to ask questions on the General Help Forum about the possibility of obtaining a back up. I don't even know if it is a practical proposition to backup around 330 GiB movies (time wise)
I only have a 250GiB External HD at this stage. - Would have to purchase another one.

How much time it would take would depend on the type of external drive. USB 3 vs USB2, mainly. Even that amount of data over USB2 wouldn't take too long, at least according to [this calculator]("http://techinternets.com/copy_calc").

As far as the price of getting a 500GB external, if it isn't too much (and it probably is), it would be an investment in a backup plan for the future. ;)

---

### Post by BlinkinCat on 2013-01-11
> **CharlesA said:**
> How much time it would take would depend on the type of external drive. USB 3 vs USB2, mainly. Even that amount of data over USB2 wouldn't take too long, at least according to [this calculator]("http://techinternets.com/copy_calc").

As far as the price of getting a 500GB external, if it isn't too much (and it probably is), it would be an investment in a backup plan for the future. ;)

Those calculator figures look really good. I may well take the plunge and purchase a 500GiB Unit today. I am a real dummy regarding backup programs so I will venture with a thread on the General Purpose Forum. Thanks again Charles - :p

---

### Post by CharlesA on 2013-01-11
> **BlinkinCat said:**
> Those calculator figures look really good. I may well take the plunge and purchase a 500GiB Unit today. I am a real dummy regarding backup programs so I will venture with a thread on the General Purpose Forum. Thanks again Charles - :p
That would be a good idea. There are numerous programs to backup your data. I've been using rsync for local backups and CrashPlan for backups to the cloud, but CrashPlan can do local backups too.

It might not be "free" but I have not had any problems with it yet.

---

### Post by dino99 on 2013-01-11
have you checked if your ISP have free space for you ? (mine have, in case i need)

---

### Post by CharlesA on 2013-01-11
> **dino99 said:**
> have you checked if your ISP have free space for you ? (mine have, in case i need)

+1. I checked my ISP and they only offered 7GB of online storage, which is why I went with CrashPlan+. Granted cloud storage with CrashPlan isn't free, you can store backups offsite at a friend's place for free, so they offer multiple methods of backing up your data. ;)

---

### Post by BlinkinCat on 2013-01-11
> **dino99 said:**
> have you checked if your ISP have free space for you ? (mine have, in case i need)

No I haven't at this stage. I have been reading up a little on Grsync, but I am not afraid to admit it is all double-dutch to me. After I do a little more reading, I will get to that General Purpose Forum - I guess at this stage that rushing into it defeats the purpose. - I will still be able to come back to this thread once my backups are sorted out :p

Edit - I have just found out that my ISP offers a service up to 300 GiB at $15 a month. It is possible that may be the way to go - I can readily trim the excess of movies down to that level. It may be the way to go - thanks for putting me on to it dino99 - I am very pleased at what may be a positive outcome.

Further Edit - Options only for PC or Mac - Rethink required

Further Edit - I will mark this thread as Solved for now until such time that I have sorted my Backups out. At that stage I will reopen this thread. I anticipate this could take a number of days or a number of weeks.

---

### Post by BlinkinCat on 2013-01-13
Hi Charles,

Yet more questions -

The comment in #21  "verify with ls"

Do I verify after each dry run ? or - after all dry runs verified O.K. ?

What will ls actually show ? Have run in terminal but not sure where relevant.

Edit : Will df -h in #26 show similar figures to that in #21 ? (or less I presume)  

I expect to be tackling this in about 3 days.

Many Thanks - :D

---

### Post by CharlesA on 2013-01-13
You will need to remote --dry-run in order to copy the files.

After the files have been copied, you can verify they are there with ls:

```
ls ~/root/var/
```

sda1 should show around 6GB used once everything has been copied.

---

### Post by BlinkinCat on 2013-01-13
Hi Charles,

Thanks very much for that - As I am busy for a few days I will temporarily mark the thread as "Solved" until such time that I get back to to it.

Regards - :p

---

### Post by CharlesA on 2013-01-14
Works for me.

I'll be around. ;)

---

### Post by BlinkinCat on 2013-01-16
Hi Charles,

I have started to reduce the partitions but thought I may double check with you first.

1. df -h looks only slightly different than original.
2. Does the first dry run look O.K. to you before I proceed ?

```

/dev/sda1       9.3G  1.4G  7.6G  15% /home/xubuntu/root
/dev/sda6       9.3G  269M  8.6G   3% /home/xubuntu/tmp
/dev/sda2       475M  159M  293M  36% /home/xubuntu/boot
/dev/sda3       7.5G  3.4G  3.8G  48% /home/xubuntu/usr
/dev/sda5       3.8G  764M  2.8G  22% /home/xubuntu/var

``````

ubuntu@xubuntu:~$ sudo rsync -ai --dry-run ~/tmp ~/root/
.d..tp..... tmp/
>f+++++++++ tmp/tmpv1GlGK
>f+++++++++ tmp/unity_support_test.0
cd+++++++++ tmp/.ICE-unix/
cS+++++++++ tmp/.ICE-unix/1645
cd+++++++++ tmp/.X11-unix/
cd+++++++++ tmp/at-spi2/
cS+++++++++ tmp/at-spi2/socket-1229-1804289383
cd+++++++++ tmp/lost+found/
cd+++++++++ tmp/pulse-2L9K88eMlGn7/
cd+++++++++ tmp/pulse-CcctT9RwKSB1/
cd+++++++++ tmp/pulse-PKdhtXMmr18n/

```Thanks - :)

---

### Post by CharlesA on 2013-01-16
Take out --dry-run, as that just tells you what it would do, instead of actually doing anything. ;)

```
sudo rsync -ai ~/tmp ~/root/
sudo rsync -ai ~/tmp ~/root/
sudo rsync -ai ~/boot ~/root/
sudo rsync -ai ~/usr ~/root/
sudo rsync -ai ~/var ~/root/
```

---

### Post by BlinkinCat on 2013-01-16
> **CharlesA said:**
> Take out --dry-run, as that just tells you what it would do, instead of actually doing anything. ;)

```
sudo rsync -ai ~/tmp ~/root/
sudo rsync -ai ~/tmp ~/root/
sudo rsync -ai ~/boot ~/root/
sudo rsync -ai ~/usr ~/root/
sudo rsync -ai ~/var ~/root/
```

lol yes Charles, I will do that - it was just that I couldn't understand all the figures and whether I should go ahead or not. (Which I will do now)

Thanks - :p

---

### Post by BlinkinCat on 2013-01-16
Hi Charles,

In #21 you say to verify with ls

Is this O.K. ?[

```

xubuntu@xubuntu:~$ ls ~/root/var/
backups  crash  lib    lock  lost+found  opt  spool
cache    games  local  log   mail        run  tmp
xubuntu@xubuntu:~$ 

```

---

### Post by CharlesA on 2013-01-16
Looks good.

Be sure to check each of the folders you copied and you should be good to go.

---

### Post by BlinkinCat on 2013-01-16
> **CharlesA said:**
> Looks good.

Be sure to check each of the folders you copied and you should be good to go.

Thats good Charles - when I saw "crash" I panicked - will finish off now.

Cheers - :p

---

### Post by BlinkinCat on 2013-01-16
Hi Charles,

Problem when I pressed enter to save 

error writing /home/xubuntu/root/etc/fstab

permission denied.

---

### Post by CharlesA on 2013-01-16
Did you use sudo?

```
sudo nano ~/root/etc/fstab
```

---

### Post by BlinkinCat on 2013-01-16
> **CharlesA said:**
> Did you use sudo?

```
sudo nano ~/root/etc/fstab
```

lol No - what a clown I am.

Thanks Charles - :lolflag:

---

### Post by BlinkinCat on 2013-01-16
Here's what it looks like before I unmount root.

```

xubuntu@xubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.9G  201M  1.7G  11% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           775M  892K  774M   1% /run
/dev/sr0        696M  696M     0 100% /cdrom
/dev/loop0      661M  661M     0 100% /rofs
tmpfs           1.9G   16K  1.9G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            1.9G   88K  1.9G   1% /run/shm
/dev/sda6       9.3G  269M  8.6G   3% /media/f5707e5c-41a3-4e55-97aa-ea5f48f75767
/dev/sda1       9.3G  5.2G  3.7G  59% /home/xubuntu/root
xubuntu@xubuntu:~$ 


```

Edit - Is that O.K. ?

---

### Post by BlinkinCat on 2013-01-16
> **CharlesA said:**
> Did you use sudo?

```
sudo nano ~/root/etc/fstab
```

Actually what I did use in the end was - 

```

sudo nano/home/xubuntu/root/etc/fstab

```I hope I didn't mess anything up -

---

### Post by BlinkinCat on 2013-01-16
To my untrained eyes I appear to have lost /home.

If so, would an option be to reformat drive while I am operating "live" ?

If I could wipe the disc completely that would be O.K.
I would prefer to set /, swap and /home freshly if possible.
I would need directions about how to do it however.

Still happy but sorry I have taken up so much of your time Charles. - :p

Edit - Maybe I am mistaken but GParted seems to indicate sda8 (home) still there - oh I am so confused. Haven't yet Unmounted root.

---

### Post by CharlesA on 2013-01-16
You just haven't mounted /home on the livecd, so it won't show up.

The df results look right too.

---

### Post by BlinkinCat on 2013-01-16
> **CharlesA said:**
> You just haven't mounted /home on the livecd, so it won't show up.

The df results look right too.

Thanks Charles - I am a panic merchant - I will now umount root.

It'll take me awhile to reboot - I spent about 1 1/2 hours fiddling with the boot device. I trust it won't take as long resetting it to boot off hd - ;)

---

### Post by BlinkinCat on 2013-01-16
Hi Charles,

All up and going now  - Your efforts in helping me are very much appreciated.

See attached Gparted screenshot - Am I correct in assuming that sda3, sda5 and sda6 are now a part of / ? Is there any point in fiddling around in Gparted to combine these parts of / together ? or is there no real point ?

When I next choose "other option" in a future fresh install, will all sda3, sda5 and sda6 simply not show up, being included in / ? 

Once again thank you very much Charles - ;)

---

### Post by CharlesA on 2013-01-16
It looks like gparted is reading fstab to determine mountpoints.

You would have to delete those partitions and then resize / to take up the unallocated space. I would recommend doing that from a livecd and be sure you have a good backup (which you do) before trying it.

---

### Post by BlinkinCat on 2013-01-16
Yes I might give it a go in a few days Charles, however I was wondering how you get over the extended partition, or would that take care of itself - or is that expanded in the same way ? 

I have a question too about the Removable Volumes that have just appeared on the Desktop but maybe I'd be better asking that question in "General Help". 

With kind regards - :p

---

### Post by BlinkinCat on 2013-01-16
I just don't understand.

Media/ Mount points have just appeared on Gparted - I was fiddling around with the removable Volumes.

---

### Post by CharlesA on 2013-01-16
> **BlinkinCat said:**
> Yes I might give it a go in a few days Charles, however I was wondering how you get over the extended partition, or would that take care of itself - or is that expanded in the same way ? 

I have a question too about the Removable Volumes that have just appeared on the Desktop but maybe I'd be better asking that question in "General Help". 

With kind regards - :p

Not really sure. You could probably merge sda2 and sda3 into sda1. Then merge sda5 and sda6 into sda8.

Not too sure about sda2 thought, as it looks like it has the boot flag set.. and I don't know if removing that partition would cause the machine not to boot. :|

---

### Post by BlinkinCat on 2013-01-16
> **CharlesA said:**
> Not really sure. You could probably merge sda2 and sda3 into sda1. Then merge sda5 and sda6 into sda8.

Not too sure about sda2 thought, as it looks like it has the boot flag set.. and I don't know if removing that partition would cause the machine not to boot. :|

I think I may leave sda2 alone - maybe just concentrate on sda5 and sda6. Not sure if I can do anything about sda3.

Cheers - :p

Edit - One last scenario - I would be prepared to do it - the question remains - can I reformat the whole disc and start again ? Maybe it is a silly question.

Another question, I wonder what the partitions would look like from a live install (not gparted) - I could have a look without installing if not promising ?

---

### Post by CharlesA on 2013-01-16
> **BlinkinCat said:**
> 
Edit - One last scenario - I would be prepared to do it - the question remains - can I reformat the whole disc and start again ?

As long as you have your home folder backed up, you should be ok if you decide to just redo everything.

---

### Post by BlinkinCat on 2013-01-16
> **CharlesA said:**
> As long as you have your home folder backed up, you should be ok if you decide to just redo everything.

I may venture a look see to see what it looks like. I do feel terrible though Charles as you have done so much for me - it has been a learning curve for which I am grateful.

Thank you very much - :guitar:

---

### Post by CharlesA on 2013-01-16
No problem at all. :)

You learn something new every day!

---

### Post by BlinkinCat on 2013-01-16
Hi Charles,

Well I took the plunge and did a fresh install of xubuntu. This allowed me to delete the sda3, sda5 and sda6 partitions easily. It leaves a 11.5 Gb hole in the middle but maybe I can resize, firstly to Swap and then to /home. What do you think Charles ?

I have now got quite a bit of reworking to the installation but hey, it's all fun isn't it.

Unfortunately though it isn't all fun as I have immediately struck a problem which I will elaborate on in the "General Help" forum, unless I can google an answer first.

Anyway thanks again Charles, and I will now mark this thread as solved. (It took some time though didn't it) - ;)

---

### Post by CharlesA on 2013-01-16
You should be able to either expand the /home partition or the / partition to take up that unallocated space.

An easier thing to do might be to just do a clean install without keeping /home and then copying all your data back from external media.

Keep in mind that anything you haven't backed up firefox settings, etc will be wiped.

---

