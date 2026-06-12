---
title: "What other file system can I run ubuntu on?"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by Simon Cropper on 2012-05-09
Hi,

I was a happy 10.04 user until I started to get extended periods (1-2 minutes) of time where my system would just freeze. The system did not crash, it only stopped responding for a set period. After much todo and investigation I discovered that the issue was to do with 'iowait' commands maxing out my CPU and the culprit was the system 'journaling' on the disk (discovered using the 'iotop' command). I verified this was the cause by turning journaling off on my main disk using tune2fs and the problem disappeared. On occasion I still have delays as I have left journaling enabled on other disks I use that contain valuable data (for obvious reasons).

Now I have waited for quite a while now for an upgrade to address this issue but after multiple kernal upgrades and moving to 11.10 several months back the problem still persists. 

Considering my original setup was built on ext3 formatted partition and my upgraded system on an ext4 formatted partition, my question is whether it is better, when upgrading to 12.04 to rebuild my system over the top of partitions formatted in ext3 without journaling, or should I turn off journaling on all my ext4 disks or has someone actually addressed this issue in 12.04 and I should enable journaling again on all disks. Of course there is also an option of installing on another disk format, but which? Will linux work well installed on any other disk format (FAT, NTFS, ...).

Anyone have any advice on these issues that might help? I don't wish to rebuild an entire system only to find out the problem is there again (which is what happened when having to move from 10.04 to 11.10; this move was only done as my system had become unusable in a production environment due to these delays).

Cheers Simon

---

### Post by Simon Cropper on 2012-05-16
:confused: bump... I can't believe anyone else hasn't come across this problem!

---

### Post by 2F4U on 2012-05-16
Much depends on what you intend to use the system for. Also, you can have different partitions using different filesystems. For a general usage pattern, I am using ext4. I never upgraded from ext3 to ext4 but instead did a fresh installation.

---

### Post by mörgæs on 2012-05-16
You should be able to find plenty of threads here.

[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

---

### Post by Simon Cropper on 2012-05-16
So I take it from the general comments that other have not had this problem, so there is no specific concern or workaround regarding this problem.

So logic tells me - after reading all the blurb I could find on filesystems and proving that journaling was the problem (done prior to posting to the list) -- the next step is to treat it as a problem.

I will rephrase my question. Considering I have found that ext3 and ext4 has a inherent flaw in the journaling system that causes my system to come to its knees -- what other file system can I run ubuntu on? I run a business and can't have an unreliable filesystem. Does anyone have any experinece running ubuntu on any other disk format?

In regards to new installs -- as stated in my first post. I moved from ext3 to ext4; You can't do this with an upgrade. I did a complete reinstall - new partition, new swap, ext3/ext4, then ubuntu.

---

### Post by sudodus on 2012-05-16
> **Simon Cropper said:**
> So I take it from the general comments that other have not had this problem, so there is no specific concern or workaround regarding this problem.
I have that problem only when I know that I have some heavy read/write task running, for example backup. I definitely recommend that you use journaling. Maybe there is some other problem with your computer (hardware or software), that makes it so slow at times.
> 

So logic tells me - after reading all the blurb I could find on filesystems and proving that journaling was the problem (done prior to posting to the list) -- the next step is to treat it as a problem.

I will rephrase my question. Considering I have found that ext3 and ext4 has a inherent flaw in the journaling system that causes my system to come to its knees -- what other file system can I run ubuntu on? I run a business and can't have an unreliable filesystem. Does anyone have any experinece running ubuntu on any other disk format?

In regards to new installs -- as stated in my first post. I moved from ext3 to ext4; You can't do this with an upgrade. I did a complete reinstall - new partition, new swap, ext3/ext4, then ubuntu.
It is possible to run linux on FAT32, but I would not recommend it. It is not possible to run linux on NTFS (but you can use it as a read/write data partition). And there are other linux file systems that some people prefer. I stayed some extra years with ext3 until I started using ext4, and I am happy with both these file systems.

---

### Post by mastablasta on 2012-05-16
> I have found that ext3 and ext4 has a inherent flaw in the journaling system that causes my system to come to its knees 
 
can you point to a bug report? or is this only in your case? because if it is only in your case logically it would then smethign be wrong with your equipment or install.
 
are we talking about desktop system?
 
 
i too never had a problem with ext4. in fact i believe google uses it on it's servers.
 
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)
 
btrfs has experimental support...

---

### Post by jadtech on 2012-05-16
sound like a hardware issue to me or not your average everyday system I sure never had or seen this issue I have used linux since 96 on at least 12 different  desk tops, lap tops and server set ups ..

---

### Post by SeijiSensei on 2012-05-16
Is this a server?  If so, what is it doing?  Does the problem occur randomly, continuously, or only when certain tasks like backups or other disk-intensive activities are taking place?  Do you have multiple devices/partitions mounted at different locations in the filesystem, or is everything in a single partition?  Usually the most active part of a Linux filesystem, especially on servers, is /var.  Is that mounted separately?  

I, too, haven't seen these problems with ext3 or ext4, and I've used them on a variety of systems over the past decade.

If you want an unjournalled filesystem, use ext2.  Ext3 is basically ext2 with journalling enabled.

OT:
I can't imagine how you could run Ubuntu on a FAT32 filesystem since it doesn't have a POSIX structure.  How would you handle things like permissions?

---

### Post by oldfred on 2012-05-16
I agree that it is not the file system that is the issue. And it would be worth while to review other issues. Some other filesystems may be better for some things but reviews show ext4 as the overall winner.

Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

I cannot say I ever have an issue on my desktop, but my laptop sometimes stalls as I am running 64bit on a system with only 1.5GB of RAM. I do that only to have same version on both, but that is too little RAM for 64 bit normally. Most tasks are ok, but several large tasks at once and system goes to swap and it turns grey for several seconds while trying to write to swap.

You can do like on SSDs and reduce writes, but some changes may increase performance at the cost of reliability.

---

### Post by Cheesemill on 2012-05-16
I have in the past tried using XFS, JFS, and ReiserFS as well as more recently BTRFS.

I always find myself returning to ext4 simply because it has caused me the least problems and has been the most stable. In fact the only one of my machines that doesn't run ext4 is my file server on which I use ZFS (running on Solaris).

---

### Post by Simon Cropper on 2012-05-16
Thanks everyone for the replies.

In response to you questions...

I am running a desktop environment and have seen this problem occur regularly on this platform albeit on 'my machine' although I have heard others complaining about delays occurring (more about this later).

I have two ubuntu servers (one with ext3 and onother ext4) that I manage but have not noted the problem BUT in the absence of being able to log the problem either when it is happening or find any record of it after it occurred it may be prevalent but there is no way of telling.

Back to my set up...
I currently use Ubuntu 11.10, previously I used Ubuntu 10.04 LTS.  

About 6 months ago I noted that my CPU was maxing out for no apparent reason. After playing around with the colours of the system monitor (in the panel) I was able to see that the iowait component was what was taking the CPU usage from normal usage to 100% of both CPUs.

I searched the forums and googled the problem with little sucess...

[INDENT][COLOR="Red"]Well it is happening as I write. The iowait is chewing up one whole CPU and intermittently maxing out the other. The computer is running firefox and thunderbird only. Using iotop, after waiting 2-3 minutes for terminal to start, I note that I now have "gconftool-2 -R / --direct --config-source xml:readwrite:/home/simon/.gconf" and [sync_superusers] bottle-necking.[/COLOR][/INDENT]

Anyway on with the story now that the computer has resumed normal operation. I checked my disk integrety and system setup to no avail - all was good. Concluded that I had somhow corrupted the system and decided to upgrade my system and start again. I then reinstalled ubuntu - new partition, formatted with ext4, brand new everything. Turned the unit on and the same delays were apparent (almost immediately). Concluding it was a disk: I ran a low level check of the disk with 'fsck' (as described here [http://ubuntuforums.org/showthread.php?t=1823509](http://ubuntuforums.org/showthread.php?t=1823509)) with no problems being found.

Excluding disk failure I then started searching again. Others mentioning the same issue. Some examples can be found here...

[http://askubuntu.com/questions/116844/how-to-diagnose-ubuntu-cpu-spikes-io-wait](http://askubuntu.com/questions/116844/how-to-diagnose-ubuntu-cpu-spikes-io-wait)
[http://ubuntuforums.org/archive/index.php/t-944314.html](http://ubuntuforums.org/archive/index.php/t-944314.html)
[http://forums.gentoo.org/viewtopic-t-893644-start-0.html](http://forums.gentoo.org/viewtopic-t-893644-start-0.html)

I then used the tools mention here [http://serverfault.com/questions/12679/can-anyone-explain-precisely-what-iowait-is](http://serverfault.com/questions/12679/can-anyone-explain-precisely-what-iowait-is) to clarify what was going on. What I found was that jbd2 was consistently topping the list. On investigation I found this had to do with the ext4 journaling system.

Others had also seen similar problems -- [http://askubuntu.com/questions/30191/how-can-i-prevent-flush-816-and-jbd2-sdb2-8-from-causing-gui-unresponsivene](http://askubuntu.com/questions/30191/how-can-i-prevent-flush-816-and-jbd2-sdb2-8-from-causing-gui-unresponsivene) .

From here the question was do I need journaling and can I turn it off. Answer to question 1 - yes but it is safer to have it on. Answer to question 2 - yes you can use tune2fs to turn off the journaling.

So I did this on my harddisk used to run ubuntu, the swap and tmp directories and the problem disappeared (for a month or so). I left journaling turned on on my data disk. 

I have noticed however that the problem is reappearing with a vengence and to a level where it is effecting production.

So I am at the stage that in a few weeks I intend to rebuild my system -- again. The question -- my original question -- stands. Considering the problems what should I do? Drop kick the HDs and start again? Change the underlying filesystem format? Turn off journaling?

Sorry for the long response but obviously people considered my request or comments unsubstantiated and to be fair in the absence of all this feedback that is understandable. Personally I try and avoid pestering people for help unless I have investigated as much as I can and reached a dead end.

Any help or suggestion are welcome.

---

### Post by jadtech on 2012-05-16
bad spots sector on a drive  are know to cause these issues hanging , freezing  CPU spiking due to  the inability to read and write areas of the hard drive(s)..

these issues  can happen now and again to every few mins to every few second depending on how many bad areas ..

bad area can be physical and logical a spot that suddenly for some reason become magnetically messed up unable to change the area state.. 

just a thought since the signs of a failing drives and bad spots have all the same characteristics you are describing ...

---

### Post by Simon Cropper on 2012-05-16
My thought also... at the start.

After checking my SMART stats on my disks and running fsck however, as I have described here [http://ubuntuforums.org/showthread.php?t=1823509;](http://ubuntuforums.org/showthread.php?t=1823509;) no problems were found.

Subsequent investigation suggesting the journaling or at least how the kernel interact with the journaling seems to support that the disk is not failing.

That said, aside from running 'sudo fsck.ext4 -cDftvy -C 0 /dev/sda1' to look for bad sectors etc, is there any other packages, tools or utilities you can suggest to check disk integrity?

Just in case, I have lined up a new HD for the new proposed install so this should be a good test of this hypothesis. If the problem continues then the disk is not the problem. Running with this line of thought though, has disk failure been the cause of everyone elses problems? Most reports are coming from 'power users' not newbees. These people have already eliminated the obvious and found iowait stairing back at them.

As stated my investigations are suggesting journaling or as noted above how the kernel interacts with journaling. Some reports have suggested that a kernel upgrade solves their problem but after what is probably 4-5 upgardes nothing has changed on my machine (in fact it appears to be getting worse).

---

### Post by sudodus on 2012-05-17
> **Simon Cropper said:**
> ...
Most reports are coming from 'power users' not newbees. These people have already eliminated the obvious and found iowait stairing back at them.
...
I think there might be a real problem for power users. If the problem is how the kernel interacts with journaling, I suggest that you test also some other distro, that is suitable for servers, for example Ubuntu's 'mother' Debian. And to play safe, Debian stable.

---

### Post by Simon Cropper on 2012-05-17
OK, change distro, I suppose that is another option. The idea was rolling around in my head but I suppose, as I quite like Ubuntu and grown use to its foibles, I was having trouble putting this on the table.

---

### Post by Gyokuro on 2012-05-17
If there is a problem with the ext4 filesystem then more people would post about and that is not the case. The only problem which I'm aware at the moment and it is not filesystem related is BUG# 985661 "High load average" ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985661)). In my experience such a jbd2 behaviour occurred 

a.) disk was dying
b.) bad cables
c.) PSU

and monitoring our servers I can not find such a described behaviour as people with mounted nfs home directory would cry at first. 

Try to swap cable and disk.

---

### Post by mastablasta on 2012-05-17
> **Simon Cropper said:**
> OK, change distro, I suppose that is another option. The idea was rolling around in my head but I suppose, as I quite like Ubuntu and grown use to its foibles, I was having trouble putting this on the table.
 
 
on a side note Debian is not that much different from Ubuntu  in the way you do things on it. i switched to it on one mashicne and had no problems adjusting. :-)
 
you could also give Fedora a try, maybe they have newer kernel.
 
also check the disks and cables as advised.... i think there are numerous linux servers out there running ext3/4 and have no issues and as others said if somehting was as wrong as in your case, there would be a flood of bug reports by now.

---

### Post by Simon Cropper on 2012-05-17
> **mastablasta said:**
> on a side note Debian is not that much different from Ubuntu  in the way you do things on it. i switched to it on one mashicne and had no problems adjusting. :-)
 
That's good to hear. I will put it on my list to try.

> **mastablasta said:**
> you could also give Fedora a try, maybe they have newer kernel.

I put in on the table but will need to review my core programs to see if the work on a redhat based system. If I can use it I will gve it a try between jobs.
 
> **mastablasta said:**
> also check the disks and cables as advised.... i think there are numerous linux servers out there running ext3/4 and have no issues and as others said if somehting was as wrong as in your case, there would be a flood of bug reports by now.

THIS IS EXACTLY WHAT I THOUGHT!

... but after eliminating everything else and a complete reinstall. I was left with only blaming the kernal or journaling. When other reported similar problems this reaffirmed this conclusion.

That said, I'll buy some new sata cables and use the new harddisk first and see how that goes. The 'problem' appears very quickly so it should only take a few days of installing various versions / distros and playing around with disks to get an answer.

---

### Post by jadtech on 2012-05-17
There is a couple other thoughts too , if you can be certain there is no disk issues no bad sector your machine is not close to high energy towers large speakers or even close to active short wave radio operators..

though radio may not directly effect hard drive  it can cause hanging a freezing by messing with the modem routers wireless slowing down the network in days of dail up they sold loads and loads of new modems and computers because they would work a few days and then have hours of sudden disconnects hangs and freezes in the name of bad boards hard drives and over heating modems only to find  the areas these people came from sometime whole neighbourhoods had a ham radio operator or 2..

older cordless phones where the base and charger are to close  can cause many issues with hanging  freezing and CPU spikes  because of slowing  and even stopping the flow of data from router  and DSL modems, everytime the phone rings or is answered the modem or router will  need resetting  computers in the house will hang up freeze or get odd random CPU spikes..
this cause is two things  older cordless phone use a frequency range that is harmonic with  many routers and modems also caused by the low pass filter gone bad  that separates DSL signal from the phone voice  from the phone can actually slip through to the modem mess things up big time, if people in the house are reporting  hearing  modem whine in the back ground the phone  while talking or dailing is another good sign, if you  are on DSL and start your computer  to discover no internet connection yet the modem seem normal active and in sync and you find  turn on a phone till there is no dial tone and then  you realize you now have internet connection ..

old florescent desk lamp that use  the large starts can cause issues as well, I have discover all of these issue  at one time or another over the years make computers run like they have hardware issues and software issues ..  

other causes for servers can be one noticed bad script line in a server over looked can cause months  and even year of head aches with these issues ..

the OS is just a very easy target when it comes to issues with the computer there are many other software and hardware cause  and even as many outside causes no one ever considers people have spent billion on hardware and software because of outside issues they never concidered ..

today in the broad band market they still like to toss around the term unlimited bandwidth   for which there is no such thing all provider throttle there services at certain hours of the day  and some also scan and throttle when a machine is connecting to any know bit torrent or P2p where mp3 and video is traded.. slow internet  is another cause of hang freeze and cpu spikes .. 

also if you are trying to run a webserver with your home provider  if they detect  loads of data going  in and out of port 80 they or mail ports they may or may not compllain but they will throttle your use  to a normal home user level bogging your internet while your servers are busy..

---

### Post by Simon Cropper on 2012-05-17
Thanks for the info jadtech. When I reinstall my system in a couple of weeks I will consider all the points you mention. If I find anything I will post an update of my findings.

---

### Post by Simon Cropper on 2012-06-17
OK. The aftermath.

Over the last few days I have been investigating this problem.

The upshot is that before I eventually got to upgrade the system the core drive with ubuntu on it failed.

So, after everything the issue was a failing disk!  

The problem was that I checked and rechecked the disk with everything that linux had to offer!

In addition, despite the disk being unable to be booted, I am able to mount the drive and look at the data it contains -- so the problem seems to be filesystem based rather than ext4 based!

Regardless, I am treating the 1TB dsk as damaged and drop kicking it out the door.

In conclusion, take care when relying on reports from disk checking programs -- they may not always be giving you the correct data.

---

