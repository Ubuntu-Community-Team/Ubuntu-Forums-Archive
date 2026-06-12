---
title: "Karmic goes muck-jumping into the septic tank"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2010-02-24
**Karmic goes muck-jumping into the septic tank** 			
 			 			 		   		 		 		Been using [U]Ubuntu Karmic 9.10 for a few months- but now it has a mind of its own.
[/U]About a week ago, Firefox would crash for no apparent reason. Then it became an increasing event. Today, after using the machine normally for several hours, it started crashing Firefox and Yelp before they loaded completely. It crashed again and again until it finally froze,
I had to do a hard reboot and then it would not load properly and then crash.
I checked the event logs and saw some warnings about an ALSA bug_ and then more _as it deteriorated.
Now it seems to boot but then when the Ubuntu logo shows up all it does is flash for a few minutes and then the screen goes black and the system freezes.
I tried using the recovery disk, but after 1 1/2 hours of black screen it reported
HD Error 0
and 6 Bus errors
And finally ended with invalid user "Ubuntu"

Then I put in a fresh copy of Karmic and ran it in recovery mode. It didn't recover and from the machine I then tried a live CD and it booted to the black screen and froze
And after I tried to do a new install I am getting lines and lines of errors like this
[ 1047 .871988] SQUASHFS error: Unable to read data cache entry [27f21194]
And about 1000 more similar.

I was going to just do a re-install, but when it started it froze and that's whats been happening.


I ran a drive integrity check and it passed and it passed an over night memtest.
The drive is about 6 months old.
I've tried the recovery in the current several times,but it goes to a black screen with a white dot in the center which spins, but does nothing else. It also freeze the system and I have to do a hard boot to release it.

Can I re-install ANY version of Ubuntu to save the data? Or is it right back to a total install and a data overwrite?

This is the 3rd time this has happened in 6 months.
Please guys - help me fix this problem.

PS 
There have been 3 versions of Karmic listed 9.10.14 , 9.10.17 , and 9.10.19 which is also listed as beta.
Does this have relevance?
I tried rolling back the kernals, but it didn't work.

If I do a re-install of Karmic or Jaunty does it automatically overwrite the data on the drive? 
I'm at the section where it wants to partition the drives
 - #1 Primary 318.2 GB B  EXT4, #6 logical 299.1GB  EXT4
#7 logical 11.4GB F Swap swap
#5 logical 11.4GB F swap swap

Do I have a save here, or can I simply skip the partitioning and reload a kernal?
All help appreciated.
Thanks
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8871121") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8871121")

---

### Post by tommcd on 2010-02-24
> **Gnusboy said:**
> 
If I do a re-install of Karmic or Jaunty does it automatically overwrite the data on the drive? 
I'm at the section where it wants to partition the drives
 - #1 Primary 318.2 GB B  EXT4, #6 logical 299.1GB  EXT4
#7 logical 11.4GB F Swap swap
#5 logical 11.4GB F swap swap

Do I have a save here, or can I simply skip the partitioning and reload a kernal?

Those errors you are getting are weird. Do you have any third party repositories on your system that are not part of a default Karmic install? If so, then do not add them back when you reinstall.
If you do not have your /home directory on a separate partition, and it looks like you do not, then a clean install will overwrite the entire root partition and any data on there will be lost. You could skip partitioning if you want to leave the partitions the way they are; but reinstalling Ubuntu to the same root partition will overwrite all data on the partition.
To rescue any data you may need try a System Rescue CD:
[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)
If you can not even run a system rescue CD, or any live CD, then I would suspect a hardware problem somewhere.
Why do you have 2 swap partitions? This is not part of any default linux install. You must have done something unusual here.
 And why are the 2 swap partitions 11.4GB each? This is way more than you need or want. If you plan to suspend to RAM, then make swap at least equal to the amount of memory you have. If not then I would limit swap to 1GB.

---

### Post by Gnusboy on 2010-02-26
> **tommcd said:**
> Those errors you are getting are weird. Do you have any third party repositories on your system that are not part of a default Karmic install? If so, then do not add them back when you reinstall.
If you do not have your /home directory on a separate partition, and it looks like you do not, then a clean install will overwrite the entire root partition and any data on there will be lost. You could skip partitioning if you want to leave the partitions the way they are; but reinstalling Ubuntu to the same root partition will overwrite all data on the partition.
To rescue any data you may need try a System Rescue CD:
[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)
If you can not even run a system rescue CD, or any live CD, then I would suspect a hardware problem somewhere.
Why do you have 2 swap partitions? This is not part of any default linux install. You must have done something unusual here.
 And why are the 2 swap partitions 11.4GB each? This is way more than you need or want. If you plan to suspend to RAM, then make swap at least equal to the amount of memory you have. If not then I would limit swap to 1GB.
Hi Tommcd

Thanks for your tips. I have 2 swap files because the last time I needed to reinstall I could not get Jaunty to re-install over itself, nor would Karmic install over that version ofJaunty. Even with a partition reformat.
I was only able to use the open partition to install Karmic - and I have tried a re-install over the broken version with no luck.
I have the system rescue CD operation on XFCE - but I have not learned what to do from the terminal yet - or really how to use what I can access. (I'm old and feeble-brained so it takes me longer to learn and retain the stuff.)
I'm still reading how to use the terminal to get to the desktop or the recovery console. Blah!
Time has been my big issue lately.
Hopefully, someone will post a baby-step solution and I can get the thing fixed pver the weekend. I'm way behind on my work.
Fortunately. I never transferred critical data files to this machine, so will only lose some bookmarks and configs - I think.
Sadly, the rescue CD won't let me access the net - I guess it's lost the the connection info or ???
Should I run Fsck? It looks like an available option in the Xfce. As far as I can tell my hardware checks out ok. Memtest reports 4 GB of working RAM and the disk integrity seems ok too. I did see there was a Pulse Audio error listed in my syslog before the crash. From what I see in the forums that has been a problem all through Karmic. Could that be the root of my problem?
In fact, my last crash came during a Media-Buntu install so my problems could stem from a bad sound config, yes? It's an onboard audio on the ASUS M3A78-EM motherboard. You think that is important?
Thanks for your feedback. I hope you, or someone can help me over the weekend.
Gnusboy

I really have not taken the time to learn all the stuff I should know to be a Linux user

---

### Post by tommcd on 2010-02-27
> **Gnusboy said:**
> 
Thanks for your tips. I have 2 swap files because the last time I needed to reinstall I could not get Jaunty to re-install over itself, nor would Karmic install over that version ofJaunty. Even with a partition reformat.
I have never had this problem. I always use manual partitioning though.
If you can not reinstall over the existing partitions then just delete the partitions and create new ones.
> **Gnusboy said:**
> 
I have the system rescue CD operation on XFCE - but I have not learned what to do from the terminal yet - or really how to use what I can access. 
If you need to rescue data you can use **rsync** from the System Rescue CD. See this from the System Rescue CD manual:
[http://sysresccd.org/Sysresccd-manual-en_Backup_and_transfer_your_data_using_rsync](http://sysresccd.org/Sysresccd-manual-en_Backup_and_transfer_your_data_using_rsync)
> **Gnusboy said:**
> 
Fortunately. I never transferred critical data files to this machine, so will only lose some bookmarks and configs - I think.
You should at least be able to mount your partition #1 from your first post and have a look around to see if any important data is there. If you are having trouble using the System Rescue CD then use the Ubuntu live CD. You can likely use rsync from the Ubuntu live CD also.
> **Gnusboy said:**
> 
Sadly, the rescue CD won't let me access the net - I guess it's lost the the connection info or ??? 
Is this wired or wireless? Connect with a wired connection if you can. Or use the Ubuntu live CD to access the net.
> **Gnusboy said:**
> 
 I did see there was a Pulse Audio error listed in my syslog before the crash. From what I see in the forums that has been a problem all through Karmic. Could that be the root of my problem?

I don't think pulse audio would cause all the problems you have experienced. The problems with pulse audio I have read about mostly deal with just sound difficulties.

---

