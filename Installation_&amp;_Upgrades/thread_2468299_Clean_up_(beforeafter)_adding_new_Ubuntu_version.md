---
title: "Clean up (before/after) adding new Ubuntu version"
date: 2021-10-24
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2021-10-24
[Background. I've been doing more work on my Ubuntu 18.04 machine connected with consolidating data for a migration to a new NAS.  Old issues such as "System Problem" detected and something related to Spice for new software installations are bothering me more, so I want to move to a new separate 20.4 installation.]

The main 1TB drive will need to be replaced before long.  It's OK now, but I can clone to a newer one quickly if tests start getting closer to thresholds.

My questions are around cleaning up for good housekeeping - getting rid of partitions related to versions of Ubuntu from 14.04 and newer (some Desktop, some Server, all with LAMP.  And eliminating old GRUB entries. I'll keep the 18.04 installation until I add 22.04, and then keep just two versions if possible.  There's one other question as well around data storage.

The drive has several partitions related to Windows which is how it was purchased.  The only overlap with Ubuntu in those is - I think - the first partition mounted as /boot/efi.

There is also a /swap partition (32G) which is the same for every OS version.  There's a partition for each version - ranging from 78G to 186G.  And, I keep forgetting that there is 301G un-allocated.

Questions: 
1) Assuming that I've taken off any data needed from partitions with unneeded OS versions, is there any downside to getting rid of the partitions?
2) I think it's good housekeeping to get rid of extra OS entries in Grub.  I just looked at the menu with Grub-Customizer and noticed that entries for OS on partitions other than the active one take longer to show.  Is it better to have fewer Grub entries?
3) The last question set is new, and is from seeing discussions about /Home and /Data (or some other partition that's easily accessible to multiple OS installations.
[LIST]
[*]A single partition that multiple OS can access consistently seems like a good thing
[*]But I've seen comments along the lines of "/Home  cannot be used the same way as /Data
[*]Is this because the personalized files and directories starting with 'dot' may vary by OS or application version?
[*]If this is the case, does it make sense to keep /Home with the OS, and to set up links for standard subdirectories in the /DATA partition?
[*]/Home/User1/Documents => /Data/User1/Documents and so on?
[*]Or are there things I'm missing / better approaches?
[*]Am I correct in thinking that even if I get it wrong it shouldn't be too hard to adjust?
[*]
[/LIST]

Thanks

---

### Post by Tadaen_Sylvermane on 2021-10-24
It may be more involved but I personally think you would best be served by removing all of the linux partitions and creating a single lvm partition. Then you can make and trash logical volumes all day long as well as extend and shrink them as necessary. Snapshots are another bonus. You also don't "waste" any space on the drive with spaces between partitions due to how regular partitions work. Also you only need a swap = ram if you hibernate. If not no point. I run just fine with a 2gb swap and I can count the times on 1 hand that I've even seen more than 5% of it being used as per conky (that I can remember). It's not used much, even less so when you have larger amounts of memory. In many cases people disable it altogether. I keep 2gb just because some stuff expects it even if it never gets used.

That being said.

1. No point keeping what you don't use.
2. I personally wouldn't mess with it. Depending on the hardware you might be talking about a few seconds. If it's an OCD issue then go for it, it's your machine. But is it worth it? Not for any practical or compelling reason as far as I'm concerned. If you are rebooting the machine regularly enough for the couple seconds to cause a problem throughout the day then I'd think you may have bigger issues than to many grub entries.
3. I like to keep /home for each distro install. Then I have a partition mounted @ /data on each one. That is shared between X number of distros. This keeps the /home/"$USER"/.dotfiles from competing with each other (it can cause issues if you use multiple DE's or even versions of DE's). As your 4th / 5th bullets suggest symlink your DATA directories into /home/"$USER". Again for me I just keep my /home/"$USER"/${Documents|Video|Music|Pictures|bin} on the Data partition. I also tend to put my .wine folders if I have any, Steam... stuff like that. No sense downloading and installing for each one unless you have to. This is my opinion on what is best. I've picked it up from this and many forums. But there are 100's if not 1000's of ways and even then they may not match what works best for you.

---

### Post by oldfred on 2021-10-24
I have many Ubuntu installs. Some are now obsolete and eventually I will reuse that partition for a new or test install.
But first thing I do is backup grub.cfg, turn off os-prober and add those installs that I am still booting into 40_custom. Originally I just copies boot stanza from os-prober/grub.cfg, but better to use a generic entry that is not specific to one kernel.
If os-prober not run, update of grub is very quick as even adding 40_custom does not add much.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Some of my examples, now older & updated with newer versions:
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

I also  use a /mnt/data partition for data and mount it in every install. I then found /home is tiny with just the hidden files & folders, so now keep /home inside / (root). 

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

There is little reason for large swap unless hibernating. And hibernating is not recommended. If you have an SSD, you can boot faster than restore from hibernation. I started with a tiny 60GB SSD just as boot drive and found that helps booting a lot. Now have larger NVMe SSD that can hold everything, so HDD is backup, test installs (they do boot slower), and some misc partitions.

---

### Post by grahammechanical on 2021-10-24
> noticed that entries for OS on partitions other than the active one  take longer to show.  Is it better to have fewer Grub entries?

I do not understand why you are troubled by that fact. A utility is used to probe all the drives looking for operating systems. The more operating systems the longer it takes to find them. It is natural that should happen. Having one OS entry or ten is neither better or worse.

If we are going to have more than one OS then we must select an OS to be our main OS. Then whenever we install an OS or remove an OS we load into the main OS and run 

```
sudo update-grub
```

That will reconfigure the Grub boot menu. And yes it does take time to find all the operating systems. If we find that the main OS has lost control of the Grub menu then we load into the main OS and run

```
sudo update-grub
sudo grub-install /dev/sdx
```

Where x is the drive that the main OS is on. Such as sda or sdb. When I want to remove an installation I either install another OS over it or delete the partition.

Regards

---

### Post by 5circles on 2021-10-25
Thanks to all for helpful replies.
[LIST=1]
[*]I'm not really bothered by the slowdown of grub-customizer.  It was just something that made me think.
[*]I thought a little about LVM - primarily because it's the foundation behind the Synology Hybrid Raid system.  But a) I decided I needed to know more about it before jumping in, and b) while what Synology allows through its GUI isn't necessarily the same as what can be done, and changed, in regular Linux, I think I burned myself by setting up a single volume rather than multiple.
[*]It looks like I'm on the right track with the symlinks.
[*]I'll pay attention to making sure things are backed up and/or archived from the partitions I delete.
[*]I'll get some side benefit from getting a little bit more involved with a newer distribution,, but my primary motivation at the moment is the NAS migration and consolidation.  My desk and office is littered with drives.  Because I'm more hands on right now, I'd like to get rid of the errors I'm seeing.
[*]
[/LIST]

I didn't mention in the original question the main background thing this machine deals with - the private WordPress blog where I make frequent notes.  It would probably make sense to use the WordPress hierarchy and MySql access to a common database as part of the single /Date partition, otherwise I'll lose access when I switch distributions.  I assume that teething troubles (mine) will cause distribution switching, if not for the 18.04 -> 20.04 transition, for 20.04 to 22.04.
Mike

---

### Post by oldfred on 2021-10-25
If the wordpress blog is just for notes, I use Zim for my notes. Its just text files which I can also open with any editor.
I like it as it is searchable & links are clickable.

If you follow my posts you will see many are the same as I search my Zim notes & copy & paste.
Issues often similar or common.

---

### Post by 5circles on 2021-10-25
Thanks @OldFred.  

I do use  WordPress on my private Ubuntu machine for experiments that drive my public sites, but that's been pretty much on hold for quite a while and not likely to resume for at least a month or two.

I keep logs of several projects and ongoing activities using Microsoft Word, and also use Evernote for somethings.  Both are good for things where it's better not to have the files on the machine that's being worked on (don't sit on the branch that you are cutting) and Evernote has the advantage of accessiblity from multiple machines and locations - although until recently not Ubuntu.  There are more power outages and connectivity issues where I'm located now, so the model of local editing and syncing is helpful.

I will take a look at Zim, but I think Evernote might be a better fit (after I've moved to Ubuntu 20.04.

---

### Post by ActionParsnip on 2021-10-25
Are you planning to dual boot. If so then i recommend an NTFS partition for /data which both Windows and Ubuntu can access (Windows can't access very many fil systems natively). I may be reading this all wrong.

---

### Post by 5circles on 2021-10-25
I don't think you are reading it wrong @ActionParsnip - I just didn't write much about that side.   

I had the capabililty of dual booting to Windows, but I don't remember the last time I used it.  It's been a while since I've done any development, but it was generally using Windows tools (PhpStorm from JetBrains / xdebug) with a virtual machine on Windows, and sometimes a separate old dedicated Ubuntu laptop or this Ubuntu desktop.

I'm a little limited on space until things progress on the Synology migration, but it looks like with removing 3 old Ubuntu partitions after moving things that might need to be archived, shrinking the main Windows partition and moving/archiving from the 18.04 partition to a /Data partition, and reserving for the /20.04 OS, the used space should be down to the point where I can do a sort of clone to either a physical 500G drive or an SSD that's available from a laptop that just died.  That's not answering your question, but right now I think that an Ext4 partition for /Data is simpler.

There's a lot of remembering that I'm trying to achieve an overall objective, and minimizing the time that isn't in the path.  Some of the time I'm spending is on things that wouldn't have taken as long if I'd been putting more into maintenance and keeping up with changes (stitch in time).  That's inevitable because of tradeoffs in the past couple of years.  Some things I'm doing now should pay off. Others are "does it matter?" or "are there other ways?"  One I'm not sure of is tools used to look at space consumption.  I like TreeSize on Windows (a lot better than Ubuntu Disk Usage Analyzer), although TreeSize seems to have trouble with some of the information from Linux network connections.  Mapped drives may be better (and I'm using them as well).  Current things that stick out for me:
[LIST]
[*]Why is Snap consuming so much space?  Can I get rid of some old stuff?
[*]Why is the total from Treesize showing as many times the physical space? Hopefully that's something that can can be configured, and even if I can't - if I let the scan complete the lower level parts of the scan are helpful.
[*]It looks like some configuration settings I have are allowing uncontrolled growth for some log files, and in other cases (SQL backups) were not removed after creation stopped.
[*]
[/LIST]

---

