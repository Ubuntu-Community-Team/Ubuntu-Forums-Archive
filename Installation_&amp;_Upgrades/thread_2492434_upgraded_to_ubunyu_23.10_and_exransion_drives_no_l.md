---
title: "upgraded to ubunyu 23.10 and exransion drives no longer works"
date: 2023-11-10
forum: Installation &amp; Upgrades
---

### Post by wss7819 on 2023-11-10
Hello,

I upgraded to 23.10 about 3 weeks ago and can only access my expansion and external drives when I use Ubuntu 23.04 or lower.
seems like a big bug in the upgrade has caused my other drives not open in file manager. Yet, if I am to start the program 23.04 or 22,04 in one of the other partitions of my HD or memory stick or expansion drive the file manager program easily opens the desired drive.

So what is it with the 23-10 release that makes it impossible to do the same? I have been searching and reading a plethora of sites and responses with little or no success in solving the issue. 
I was even told to accept the loss of my drives and do a 'fresh' install that wipes the drive of any data. At the same time I find I am unable to go back to the previous installed version as something with 23.10 won't allow that to happen.
Even if I did do the fresh install with the drive wiped there is no guarantee that would be able to open any drive other than the one I would be working from.
So, if anyone has an answer to how to correct the problem with the 23.10 version I would be glad to hear it.Thank You for your time.    William

---

### Post by MAFoElffen on 2023-11-10
Show me this and explain what I am seeing with that. Please post the output within CODE Tags.
```

lsblk -e7 -o name,label,size,fstype,mountpoint,model

```

---

### Post by wss7819 on 2023-11-11
I am unsure of what you are asking. Are you asking for a report from terminal, if so tell me which commands you want me to input
 And how much detail you are looking for.

---

### Post by ian-weisser on 2023-11-11
> **wss7819 said:**
> I am unsure of what you are asking. Are you asking for a report from terminal, if so tell me which commands you want me to input
 And how much detail you are looking for.

Input the following single terminal command: 
```
lsblk -e7 -o name,label,size,fstype,mountpoint,model
```

Copy/paste the entire output, properly formatted ([How to use CODE tags]("https://ubuntuforums.org/showthread.php?t=1189729")) into your response. Omit nothing.

---

### Post by TheFu on 2023-11-11
For 50+ yrs, the way to get back to any prior setup was to restore from a backup.  It is expected that if you need that capability, then you would make a backup.  So, my answer for how to get back to 23.04 which has about 2 months of support left is to restore from your backups.  Simple.

As for things that don't work after an upgrade related to mounting storage, have you verified that the file systems necessary to mount that storage are loaded into the upgraded OS?  If they aren't default and you didn't tell them to be loaded, the computer probably didn't.  The command requested by MAFoElffen will show the file systems in use, so you can verify the file system tools required to support those are installed.

And if those devices have been connected to MS-Windows, it is likely that the other OS didn't correctly close the file system, so you'll need to force that. I don't know how to do it without MS-Windows, since Linux doesn't work that way.

---

### Post by wss7819 on 2023-11-11
NAME   LABEL                     SIZE FSTYPE MOUNTPOINT MODEL
sda                            931.5G                   Expansion+
&#9492;&#9472;sda1 Seagate Expansion Drive 931.5G ntfs              
sdb                            149.1G                   ST9160821AS
&#9492;&#9472;sdb1 FreeAgent Drive           149G ntfs              
sdc                                0B                   USB SD Reader
sdd                                0B                   USB CF Reader
sde                                0B                   USB SM Reader
sdf                                0B                   USB MS Reader
sdg                            596.2G                   WDC WD6400AAKS-65A7B0
&#9500;&#9472;sdg1                         536.2G ext4              
&#9500;&#9472;sdg2                             1K                   
&#9500;&#9472;sdg3                            54G ext4   /          
&#9492;&#9472;sdg5                             6G swap              
sr0                              4.4G                   TSSTcorp CDDVDW SH-S223T

---

### Post by MAFoElffen on 2023-11-11
Okay... When you post something that is gong to contain output or commands, use "Adv Reply" or "Go Advanced"... That will bring up the Advanced Editor with the "Extended Tool Bar"... I that tool bar, you will see an "#" Icon... Refer to the attached photo, middle bar, 3rd from the right. That is the Code Tag control. If you press that Icon it will insert Codes tags into the post. You can either move your cursor, to where you want, select that, and paste the output between those tags... Or if already there, select the text with your cursor, select that icon, and the tags will be added to wrap the selected text with code tags.

I would go back to your last post, edit it, and wrap the output with CODE Tags...

Are you talking drive /dev/sda and /dev/sdb?

---

### Post by wss7819 on 2023-11-11
That may be true for 50+ yrs and if I had placed the 2 or 3 backups on something that 23.10 would see as an accessible drive, I would be doing good. What I have verified is that the 3 previous versions (23.04, 22.04 and 20.04) all can see and mount my drives without any issues. Since 23.10 has the issue with mounting I can then deduct the problem is with the 23.10 version. No? When I brought the issue up on another site I was told that I jumped the gun and would need to do a fresh start, wiping my current hard-drive of the data on the partition the 23.10 created. 

I do appreciate instructional directions on the various commands in Terminal and have asked over the past posts where one might find a site, list or page explaining the various commands so I could assist myself with identifying problems with whatever version I happen to be running at the time. To which I have rec'd no response. So if I may appear unknowing of what is asked of me, that is because I have holes in my knowledge that others don't have. I really don't appreciate being talked down to or ridiculed or belittled for knowledge that have not been presented to me. Some say that words have no way of transmitting the senders emotions, I beg to differ on this.
As far as my Windows use, I switched over to Linux 10 yrs or longer, I'd say longer ago and have not had the issues with Linux in the past as I do today. In fact I have had to little terminal work in the past 5 years due to the dependability of Ubuntu. I have been with Ubuntu since it's start,that is how long I have been using Linux, a great product.

To sum up what I am experiencing today with 23.10:
-- I am unable to access drives all other versions of Ubuntu can mount

---

### Post by wss7819 on 2023-11-11
```
NAME   LABEL                     SIZE FSTYPE MOUNTPOINT MODEL
sda                            931.5G                   Expansion+
&#9492;&#9472;sda1 Seagate Expansion Drive 931.5G ntfs              
sdb                            149.1G                   ST9160821AS
&#9492;&#9472;sdb1 FreeAgent Drive           149G ntfs              
sdc                                0B                   USB SD Reader
sdd                                0B                   USB CF Reader
sde                                0B                   USB SM Reader
sdf                                0B                   USB MS Reader
sdg                            596.2G                   WDC WD6400AAKS-65A7B0
&#9500;&#9472;sdg1                         536.2G ext4              
&#9500;&#9472;sdg2                             1K                   
&#9500;&#9472;sdg3                            54G ext4   /          
&#9492;&#9472;sdg5                             6G swap              
sr0                              4.4G                   TSSTcorp CDDVDW SH-S223F

```   

(This does change when I try to use the thumb drive.)

Yes, drives sda, sdb, I receive an error message that they are not mountable because of "wrong fs type, bad option bad super block........" which prevents me from using my backups or any data I need to populate my empty files and folders with.OR creating new back-ups of the current system. The production time has been blown out due to missing files and folders.
I hope this is what you are seeking.

---

### Post by MAFoElffen on 2023-11-11
Okay, so you do not have Windows there, but you have 2 external USB drives, that are formatted as NTFS... That are not presently mounted to your system.

They worked on Ubuntu 20.04, 22.04, 23.04... But not on 23.10.

Sideline question. You sound like you were on an LTS release schedule, then went to interim releases. Was there a reason for that?

If you open a terminal session, what happens if you do
```

sudo fsck.ntfs /dev/sda1
sudo fsck.ntfs /dev/sdb1

```

---

### Post by yancek on 2023-11-12
The suggestion not to use a short term release like 23.10 is good advice for use on a primary system.  The only reasons for going to a short term release would be if something does not work on the current system and you have good reason to believe it will on the new release.  Updating it shortly after its release often leads to problems but in any case, I would suggest as above to stick with LTS releases.

I'm also curious as to why you have an ntfs filesystem on your backup drives.  If you don't have windows and don't share with windows there should not be a need or use for windows filesystems.  The problem you get when you do this is the possibility that the filesystem gets corrupted and you have no way to repair it.  You need windows software to do that, for example running chkdsk /f from windows on the filesystem.  You should be able to get windows as a  free download or some windows repair software to do this.  The fsck and ntfsfix options available for ntfs filesystems are extremely limited compared to the actual windows software chkdsk.

Since, if I understand your post, you still have earlier versions of Ubuntu, prior to 23.10 installed and are able to access those foreign filesystems (ntfs) on your external drives with them there would be no point in reinstalling 23.10.  I don't know what the problem might be if that is the case as I don't use short term releases.

---

### Post by MAFoElffen on 2023-11-12
+1 -- 
I was planning to suggest that once he got this fixed and it mounts okay, that you think about a plan to convert the underlying filesystem of those two drive to ext4. ext4 is native to Linux, and has file journaling,  which uses checksums in the journal to improve reliability. This feature can can also improve performance.

---

### Post by TheFu on 2023-11-12
> **wss7819 said:**
> That may be true for 50+ yrs and if I had placed the 2 or 3 backups on something that 23.10 would see as an accessible drive, I would be doing good. What I have verified is that the 3 previous versions (23.04, 22.04 and 20.04) all can see and mount my drives without any issues. Since 23.10 has the issue with mounting I can then deduct the problem is with the 23.10 version. No? When I brought the issue up on another site I was told that I jumped the gun and would need to do a fresh start, wiping my current hard-drive of the data on the partition the 23.10 created. 

The first problem, appears (harder to tell with the incorrect format) to be that you have decided to use a non-native file system, NTFS.  If those partitions had been formatted with a native Linux file system, we'd be passed that issue completely and could be looking at other things like USB controllers, USB cables, drivers, etc.  

I can't imagine that wiping the OS would be needed to get this working.
Also, I'd guess that just the NTFS drivers weren't installed, so if you install those and run a mount command for each, that would make the storage available ... until you can wipe it and format to a native Linux, say ext4, file system.

> **wss7819 said:**
> 
I do appreciate instructional directions on the various commands in Terminal and have asked over the past posts where one might find a site, list or page explaining the various commands so I could assist myself with identifying problems with whatever version I happen to be running at the time. To which I have rec'd no response. So if I may appear unknowing of what is asked of me, that is because I have holes in my knowledge that others don't have. I really don't appreciate being talked down to or ridiculed or belittled for knowledge that have not been presented to me. Some say that words have no way of transmitting the senders emotions, I beg to differ on this.
 

Everyone has gaps in their knowledge. It is impossible to know everything.  But with 10 yrs of use, that does go to say how intuitive things have become if you haven't needed to learn much more.

Nearly all commands are explained in the "man pages" on your system.  It is all there already, unless you go out of your way to prevent that information from being installed.  
```
$ man {name of command}
```
So, 
```
$ man lsblk
```
will explain how to use **lsblk**.
To learn how to use the man pages, **man man**.  I really wish we weren't disallowed from pointing people in this direction on this forum.  manpages have so much useful information and it teaches people how to fish for themselves.  To search the "summary" of a all manpages on the system, use the **apropos** command.  To learn more about it, 
**man apropos**

Any beginning Linux/Unix book would have this information, probably in chapter 1. It is embarrassing that it doesn't get explained.  Also, use the manpages  ON-YOUR-SYSTEM, not those on a website or another system.  That's because manpage versions are tied to the specific version of the program on-your-system, which could be different from what's on my system.

> **wss7819 said:**
> 
As far as my Windows use, I switched over to Linux 10 yrs or longer, I'd say longer ago and have not had the issues with Linux in the past as I do today. In fact I have had to little terminal work in the past 5 years due to the dependability of Ubuntu. I have been with Ubuntu since it's start,that is how long I have been using Linux, a great product.
 

While I mostly use the CLI, not a GUI, it is good to have both methods.  OTOH, 80% of the power in Unix comes from the CLI interfaces and having things automated. If you are happy using 20%, that's great too.

> **wss7819 said:**
> 
To sum up what I am experiencing today with 23.10:
-- I am unable to access drives all other versions of Ubuntu can mount

**Can you please post the exact [B]mount** command that isn't working or the fstab entry that you think should mount the storage?[/B]
BTW, to learn about the mount command, use
```
$ man mount
```

To learn about the fstab file, use
```
$ man fstab
```

When it comes to system problems, note the time that you try something which fails then look at the system logs at that time to see the errors they show.

---

### Post by wss7819 on 2023-11-12
"sudo: fsck.ntfs: command not found"

I was instructed to run the 'ntsffix' program to repair errors with the drives. The result was they were successful.

The reason to go with the 23.04 from 22.04 was to correct a NVIDIA issue with resolution of my display and there was something else and I would need to go through my old notes for that. 
I had done some research before upgrading and it was explained that the issue would be resolved. I found a few references to resolution issues and 23.04 helping to fix the problem.
I didn't study enough on whether or not the new version would cause other serious issues as well. As the lady said 'looks like you jumped the gun.'
I ended up removing myself from the site as it was no longer helpful.

Up and until 22.04 I never had issues with the drivers for my monitor. After going to 22.04 I only had 2 options for resolution and neither had a refresh rate listed. 
22.04 removed all stored data on my display and manually adjusting/Increasing magnification just caused more visual problems.  
Hope that helps.

---

### Post by MAFoElffen on 2023-11-12
Can you mount your two drives now?

---

### Post by wss7819 on 2023-11-12
When I am in the drives program or when I try to mount from the side menu of the desktop I am unable to mount the drives. 
Thank You for the response.
The drives are still unavailable to me.

---

### Post by TheFu on 2023-11-12
If you have NTFS corruption, use MS-Windows to resolve it, not Linux.  All non-native file system tools are hacked together, reversed engineered, to get something working. How well that "something" works is mostly chance.  About once a month, my only NTFS file system gets corrupted and I'm forced to reformat it, losing all data is contains at the time.  OTOH, I haven't had any major data loss with ext4 in over a decade - perhaps 2 decades.

I don't think **fsck.ntfs** exists.  I always use **fsck -t** and don't call the direct programs. Just never got into the habit.  Most of the time, I don't need to specify the type (-t) of file system, since the header for the file system knows that information already.

I'm still waiting to see the **mount** command used that you claim worked before.

---

### Post by MAFoElffen on 2023-11-12
'fsck.ntfs' used to be just a symlink to 'ntfsfix'... Which 'ntfsfix' is an utility from the package 'ntfsprogs' that is a default installed package...

You are right, that symlink is no longer there. Dang. LOL.

+1 with TheFu...

As I mentioned earlier, usually if a NTFS filesystem goes awry, I fix that directly with Windows, which that is native to it, BUT... You haven't had Windows in 10 years. Why still have a filesystem that is not native to anything you have? I suggested that when you do get access to the data, you should make plans to get it onto an ext4 filesystem...

[HR][/HR]
Back to looking at it. You said this started when you upgraded the release to 23.10...

If you boot from an Ubuntu Installer 23.04 or 22.04 LiveUSB, can you mount it and see your data?

If not, then I'll give you directions to repair the filesystem from a Windows 10 install disk...

---

### Post by wss7819 on 2023-11-12
```
william@william-FK522AA-ABA-a6544f:~$ mount /dev/sda1/
mount: /dev/sda1/: can't find in /etc/fstab.
william@william-FK522AA-ABA-a6544f:~$ mount /dev/sda/
mount: /dev/sda/: can't find in /etc/fstab.
william@william-FK522AA-ABA-a6544f:~$ sudo mount /dev/sda1/
[sudo] password for william: 
mount: /dev/sda1/: can't find in /etc/fstab.
william@william-FK522AA-ABA-a6544f:~$ 

```

When I try to open from the sidebar or drives program I receive a message stating

"error: Failed to mount “Seagate Expansion Drive”: Error mounting /dev/sda1 at /media/william/Seagate Expansion Drive: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error"
A catch all explanation.

NOTE: I have been replying to last message and I receive message stating duplicate posts.So here it is here:

  	 	 	 	   When I use the mount script for both drives:
 	-Icon drops off desktop and file manager
 	-Disks program show as mounted
 	-unable to locate disks
 	-unable to access drives
 
 
 Using the umount script:
 	-the icons return to  
 	-receive error message when I try to open disk

---

### Post by MAFoElffen on 2023-11-12
Try these commands to mount them:
```

sudo mkdir /mnt/drive1 /mnt/drive2
sudo mount -t ntfs -o defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw /dev/sda1 /mnt/drive1
sudo mount -t ntfs -o defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw /dev/sdb1 /mnt/drive2

```
When you go to unmount them, then do
```

sudo umount /mnt/drive1
sudo umount /mnt/drive2

```

---

### Post by wss7819 on 2023-11-13
When I use the mount script, the icons on the desktop go away and it appears as if there is little or no response in terminal, as it move to the next line and prompts.

the umount script brings the icons back with terminal giving little or no response.

In the disks (drive by my error) program it shows the mount and umount

In file manager I am unable to locate either disk after being mounted and I am receiving the same error message as before.

Could I not go to 23.04 and try to convert the ntfs to what is needed? I don't know if it is possible, just wondering.

I am unsure as to why any of the disks are in a format not native to Linux, it is not something I did at will.

---

### Post by wss7819 on 2023-11-13
When I use the mount script for both drives:
 	-Icon drops off desktop and file manager
 	-Disks program show as mounted
 	-unable to locate disks
 	-unable to access drives
 
 
 Using the umount script:
 	-the icons return to  
 	-receive error message when I try to open disk

---

### Post by wss7819 on 2023-11-13
3rd attempt to reply:


When I use the mount script for both drives:

 	-Icon drops off desktop and file manager
 	-Disks program show as mounted
 	-unable to locate disks
 	-unable to access drives
 
 
 Using the umount script:
 	-the icons return to  
 	-receive error message when I try to open disk

---

### Post by wss7819 on 2023-11-13
When I use the mount script for both drives:
 	-Icon drops off desktop and file manager
 	-Disks program show as mounted
 	-unable to locate disks
 	-unable to access drives
 
 
 Using the umount script:
 	-the icons return to  
 	-receive error message when I try to open disk
  

4th attempt to reply

---

### Post by yancek on 2023-11-13
> mount: /dev/sda1/: can't find in /etc/fstab.

When you get that error, you need to add the filesystem type, example in post 20 above.  Your ntfs filesystem is corrupted and you need at the very minimum, to run chkdsk from windows.  Until you fix that, you are not likely to be able to access these partitions.  You should be able to download a windows iso file and put it on a usb to boot and select a repair option to run chkdsk.

---

### Post by TheFu on 2023-11-13
> **wss7819 said:**
> When I use the mount script, the icons on the desktop go away and it appears as if there is little or no response in terminal, as it move to the next line and prompts.

What mount script?  Assume we are stupid, since if you are extremely clear, we don't know.  Also, we cannot read your mind.
> **wss7819 said:**
> 
the umount script brings the icons back with terminal giving little or no response.

What umount?  I must have missed that.
> **wss7819 said:**
> 
In the disks (drive by my error) program it shows the mount and umount

Forget the GUI.  That won't help you.  Stick in a terminal and use only the specific mount commands provided, in the order provided.
> **wss7819 said:**
> 
In file manager I am unable to locate either disk after being mounted and I am receiving the same error message as before.

When the mount commands work (there are 2), those file systems should be mounted under /mnt/.  Go look there.
> **wss7819 said:**
> 
Could I not go to 23.04 and try to convert the ntfs to what is needed? I don't know if it is possible, just wondering.

I am unsure as to why any of the disks are in a format not native to Linux, it is not something I did at will.

When drive makers ship their drives, they routinely preformat them to NTFS since 90+% of the world will need that.  As Linux users, we are expected to know this (magically) and setup the type of file system we want ourselves BEFORE we start using the storage.

There is no "in-place conversion" from NTFS to any other file system.  You'll have to copy off all the data you want to keep, wipe the NTFS file system, then create a new ext4 file system, mount it using ext4 mount options (which aren't complex like NTFS) and copy the data back.  Also, normal Unix file permissions will be used when NTFS is gone, so if you haven't learned those in the last 10 yrs, you'll want/need to learn them.  Right after a native Linux file system is created, only root can access the mounted storage. This is by design - i.e. not a bug.  It is common to chown an entire data partition (really the file system), if there's only 1 userid that needs access. This needs to be done once.

BTW, while you are doing these things, you really should change the labels on both drives so they don't have spaces.  I suspect the spaces used in the labels is one of the problems getting the mount to work.  If a label has spaces in the name, you'll need to quote the entire label in all commands, like the mount. Best to just change the label to be unique, but meaningful to you.  For some example labels, here are some of mine:
videos-scratch, rom-2tb, R2-Array, Back2, rom-1tb, RAID1-Array, home01 .... note that none have spaces. That's so I don't need to use quotes.  If I want to mount using the label, I'd use
```
sudo mount -t ext4     LABEL=rom-2tb   /mnt/rom-2tb
```
That assumes ext4 is the file system.  I really don't mount storage long-term to /mnt/.  /mnt is meant to be used for temporary administrative work.  

You are probably used to seeing partitions/file systems show up under /media/.  Mounting storage under that area is controlled by Gnome programs. Best to avoid it so that your mounts and whatever the gnome-guys decide to do next don't conflict.  For a few years, the conflicts were bad. Bad enough that I just don't use /media for anything. I don't use Gnome and don't allow automatic mounting of random storage (using gvfs or gio) to my systems for security reasons.  

The idea that anyone could walk up, plug in a USB storage device and it would be mounted scares me.  All sorts of really bad things can happen with that enabled.  Of course, lots of other people decide that the convenience of that is worth the risks (or they don't really know the risks).  I can think of all sorts of nasty things that could be done with that capability, I promise.  I could probably trick you into doing something that would open a reverse shell over the internet back to one of my machines.  When I was teaching beginning Linux, I had the class copy/paste some code from a website to make a point.  The code that was displayed wasn't the actual commands being run.  Over 50% of the college students did it.  The other 50% weren't really paying attention and only 1 person (there's always 1-2 in every class) caught my sinister plan.

All HDDs fail, eventually.  My goal is to move my data off the most likely drive to a newer drive BEFORE any failure causes issues.

---

### Post by MAFoElffen on 2023-11-14
I'm going to answer these, then I'm out of here for the night. Please watch how you come across to others... I am very proud, and protective of the people here.

As both TheFu and I posted our commands to mount, we were being kind. We didn't want to flat-out tell you that you were wrong. If you look at what you did that didn't work... when it threw that error... 
Quote:
> 
mount: /dev/sda1/: can't find in /etc/fstab. 

That error comes up because your commands were wrong. They were missing the mountpoint. If you issue a 'mount' commend without a mountpoint, it assumes that it must be defined in your /etc/fstab file, and since it isn't, it told you that it was not defined in your fstab file. Do you understand that error now?

Now for your other questions
```

-Icon drops off desktop and file manager

```
Yes, because they were mounted into the filesystem at /mnt/drive1 and /mnt/drive2. That was a success, not a failure as you wrote that like... That is how that came across in your posts.
```

-Disks program show as mounted

```
Well... Yes they were mounted successfully. Problem solved right? LOL
```

-unable to locate disks
-unable to access drives

```
Only because you didn't navigate to where they were mounted-- At /mnt/drive1 & /mnt/drive2.. Look at the commands that told them to mout at those mountpoints... 

Try to understand what the commands are doing by looking in the Man Pages for each. As an old adage about Unix and Linux commands went: The only 'man' you need, is at the commandline (man <command>)... If you still do not understand, then paste them into:
[https://explainshell.com/](https://explainshell.com/)

Please watch how you address people and how many times you bump a thread. When you do respond to something someone said, please either quote what you are responding to, or say who that is. We shouldn't have to guess. 

You bumped the thread 5 times, in 1 hour, all 3 hours after my last post last night. I had to sleep. By Forum Policy, you are allowed to bump a thread once in 24 hours waiting for a response... You should be happy the Moderators didn't flag you.

There was no "script". There were commands given, that expected feedback from you on how they went. Guess what = they worked. That is just misunderstanding, inexperience, and not knowing the nomenclature on your part. 
> 
"Communication" is the mutual understanding between "all" parties. 

Which also means that we need to watch how we recommend something to you, that we ensure you understand. Because it is very clear that we need to ensure you understand what is going on, and can recognize when things are going wrong, or that they are working like they should.

The 2 drive's filesystems are now repaired, and are now mountable, at least by manual commands.

So what I see you need to do, is to explain to these other Members what you need next. What doesn't work for you, and what you should do to prevent this from happening again.

I'm tired. I need to rest and recover from a few things. I'm sorry for being short, but I feel it had to be said.

Good night.

---

### Post by wss7819 on 2023-11-14
> You bumped the thread 5 times, in 1 hour, all 3 hours after my last post last night

I am sorry if I caused you to miss some sleep. I was not aware I was bumping the thread, it was late and after I completed a response and posted it, nothing happened on my end. I was never aware of a 3rd page being created until I checked the thread the next day. I apologize for the headache over that. 

> Yes, because they were mounted into the filesystem at /mnt/drive1 and  /mnt/drive2. That was a success, not a failure as you wrote that like...  That is how that came across in your posts.

I still don't  know where you are referring to, just where is /mnt? If I have three disks/drives and one is mounted should it show in the file manager program. If not why? Because that is how my 3 disks/drives appear before I manually mount another disk/drive in terminal. After terminal mounts the remaining two disks/drives the icon showing them to be apart of the system are no longer showing anywhere. Yet at the same time the internal disk/drive icon is still show that disk/drive as part of the system and accessible to file manager for me to work with. I am confused as to how the disk/drive is removed from the file manager and desktop ( yes, I know your desktop may not have a bar on the left hand side showing favorite pinned programs, running programs and I have pinned the disk/drives to the bar as well.)

I guess what I am saying is how can it be a success if I can no longer have access after mounting /dev/sda1 or /dev/sdb1, by success I mean seeing any type of file structure or error message or warning about that which I am attempting to open.

>  Your ntfs filesystem is corrupted and you need at the very minimum, to  run chkdsk from windows.  Until you fix that, you are not likely to be  able to access these partitions.  You should be able to download a  windows iso file and put it on a usb to boot and select a repair option  to run chkdsk./QUOTE]

Just how do you know my files are corrupted?

 I was able to have all 3 drives/disks scanned by a windows program and they were all ok. I used the that are part of the boot set-up (diagnostics) when HP (Hewitt Packard)first starts up, after I press the power button and the system starts coming on line. 

I will need  to find a way to check the external, expansion and internal drives from another version of ubuntu, but I will check into that later.

[QUOTE] As both TheFu and I posted our commands to mount, we were being kind. We  didn't want to flat-out tell you that you were wrong. If you look at  what you did that didn't work... when it threw that error... 

 I am unaware of what the "FU" is.

I am sorry if I was saying scripts instead of commands. I was at a loss for words when I was trying to explain myself.

The last sentence does not make sense as to what you are attempting to relay to me.
I have been questioning that error message from day one and getting nowhere near to a resolution for what it means or what I need to do to correct the problem .
MY purpose for this is because 23.10 didn't want to move the files and  folders when I installed it and if I recall correctly I received a  message from 23.10 that I could do this step later. So I didn't worry  about it then.


> Well... Yes they were mounted successfully. Problem solved right? LOL

So, a successful mount is a mount where a disk/drive is mounted yet unavailable for any other purpose. My purpose from the start was and is to gain access to my files and folders I backed up in an earlier version of ubuntu.


> Only because you didn't navigate to where they were mounted-- At  /mnt/drive1 & /mnt/drive2.. Look at the commands that told them to  mout at those mountpoints... 

I do not see where /mnt/drive1 and /mnt/drive2 are located. I have not seen an address that contains /mnt/drive1 or /mnt/drive2 within it. In all of my work here that has never been seen by me and I would think I would recall such an address.
Mount/mountpoints ? How does one access, move and edit files held within a disk/drive at the mount point? By files I mean my private folders and my back-up folders, which I created in an earlier version of ubuntu?

Did I ever say I had a clear set of fundamental skills working with Linux? I believe I said the opposite.

> So what I see you need to do, is to explain to these other Members what you need next.

First I am going to somehow back-up what I have on the internal hard drive and then create Linux formatted thumb-drive and put a version 20.0? of ubuntu on it and wipe the drive, so I can somehow repair the corruption/errors/failures of the drive.  
 Once I do that I can start the process of locating my freshstart program for ubuntu 20.0? and then install it upon my internal hard drive. 
That should leave me with the ability to once more access my corrupted, error ridden failing disk/drive that I could always access through earlier versions of ubuntu than I currently have. 

Thus letting us able to call this thread solved. 

BTW: I live out in the sticks about 30-35 miles from nowhere and don't usually randomly take commands from others and willingly input them into my system. 
I do check around and see if the commands have any issues which I should be aware of. 
People do not come out this far very often, other than the mailman and the box is down the road.
I do very little if any social media and have lots more chores to do than I am able to do. 
Getting old and getting the chores done have their downsides, not many, but enough to keep a persons mind active.
As I said before this disk/drive issue has put me behind and others are waiting for me to finish my part. 

Well let me get to working on my new path forward and unless I have some major issues with what I lined out above, you 'all shouldn't hear from me for a long time out.

SeeYa, W

OH, you don't have to respond to my remarks above, I'll be working on something and won't be looking for one anyway. Besides with the version of ubuntu I'll be using, any commands or suggestions probably won't work with it.

---

### Post by TheFu on 2023-11-14
> 
I do not see where /mnt/drive1 and /mnt/drive2 are located. I have not seen an address that contains /mnt/drive1 or /mnt/drive2 within it. In all of my work here that has never been seen by me and I would think I would recall such an address.
Mount/mountpoints ? How does one access, move and edit files held within a disk/drive at the mount point? By files I mean my private folders and my back-up folders, which I created in an earlier version of ubuntu?


In the file manager, after a file system is correctly mounted via the mount cmd or fstab, it doesn't get a separate button on the left.  It only appears like any other local directory.  Do you understand that directories are hierarchical?  
**/** is the top of all directories and all storage.
**/mnt/** is 1 level deep.
**/home/wss7819 ** is the HOME directory for username, wss7819. (I'm simplifying here, there are exceptions).
So when we say that /mnt/drive1 and /mnt/drive2 are mounted, that also says exactly where you should look for the storage for each.  Under /mnt/drive1 and under /mnt/drive2.  You can use the file manager to get there and mark those directories as "Favorites", I suppose.  I don't really use file managers.

I think the person posting that the file systems were corrupted was making an educated guess. It may have been true and it may have been corrected when you got chkdsk to run on them.  Or it may not have been true. We'll never know.  

What we do know is that the drives are mounted now, assuming you didn't reboot.  After each reboot, you'll either want to have the commands in post #20 handy to mount the storage again
OR 
you'll want to convert (or get help converting) those lines into the required lines to add to the fstab file so the file systems are mounted automatically at boot.

As to the real root problem for why things don't work like they did with prior versions of Ubuntu, I can only guess that the Gnome people changed their file manager and gio or gvfs programs.  I call those "fake mounts", because they don't do everything that real mounts do, don't provide the same controls over mount options and definitely are slower for storage access than real mount methods.  Had you been using the fstab method all this time, nothing would have changed between releases.  

The fstab file is extremely stable and hasn't changed much since 1993, thought in the early 2000s, they did make a push for /dev/sda1 like device names to be replaced using UUIDs.  I strongly prefer using LABELs, which are more human friendly.  The sda1 part can change at every reboot. The name is based on the order that the storage device is "found" by the Linux kernel at boot, so if one drive is slower than the other and that changes for any reason, then the drive names would likely swap.  It is strongly recommended NOT to use device names, like "sda1" in mount commands for that reason.  I tried to show a method in post #26 to use LABEL for mounting instead.

But it seems you never saw any of my posts or blocked them somehow.

---

