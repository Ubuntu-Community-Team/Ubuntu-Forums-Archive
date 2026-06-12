---
title: "Ubuntu 9.10 locks up"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by tperwez on 2010-04-17
Hi Everyone

I just upgraded my system from 8.10 to 9.04 and then to 9.10 yesterday. However, today I just found out that it is locking up. Specifically, it locked up when I was in Firefox and the system would not respond to anything at all. The keyboard would not respond at all. After hard reboot, I decided to work on Konqueror instead of Firefox and it happened again. 

The more persistent problem that I noticed reproducibly is that after I do the "Lock Screen", the system cannot be brought back at all. The screen stays blank and again there is no response from keyboard. 

I did not have this problem ever before and I used Ubuntu 8.10 for more than a year. The only one instance of lock up was last week (when I was still on 8.10) when Firefox locked up. 

I looked up on the bug reports and found out that there were many reports of system lock up soon after the 9.10 was released. Since I upgraded the system only yesterday, I do not think that my problem is the same. I am sure those bugs would have been fixed by now. 

I would like to know if others have experienced the same sort of problem with 9,10 recently and what sort of fix is there. My own hunch is that perhaps the mouse or the mouse driver is at fault and I am testing a different mouse to test this. 

I am running Ubuntu on AMD Athlon 2400+

Regards,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
My desktop was locking up on me and I ran fsck /dev/sda3 in recovery mode at it hasn't done it since.

EDIT: I have replaced the rest of this post with the proper, safe way to force fsck to run automatically on the next boot to prevent anyone from trying to do it the way I first said. Which for some reason did work for me.

Open a terminal
Applications > Accessories > Terminal
and run
```
sudo touch /forcefsck
```

and on the next reboot it will start the fsck checking like if it had reached 30 boots.

Any time you want to force it to do a fsck, give the above command and reboot.

---

### Post by tperwez on 2010-04-17
> **2hot6ft2 said:**
> My desktop was locking up on me and I ran fsck /dev/sda3 in recovery mode at it hasn't done it since. So run
```
sudo fdisk -l
```
to make sure which is your ubuntu partition if you don't already know.


Then reboot into recovery mode and drop to the Shell prompt and run
```
fsck /dev/sda3
```
or whatever your ubuntu partitions sda# is and see if that helps.

I ran 

sudo fdisk -l

in the terminal and it ran silently; i.e., there is no output. Notice that I am still running a GUI session and not in recovery more yet. What exactly should I expect an an output from this command? I thought it should give me the name of the partition?

Also, how do I log in in the recovery mode. Forgive me for being rather naive; I have never done this sort of thing before and am a bit hesitant to do something that could be potentially nasty given the fact that I am already reeling from a problem from this upgrade that has made the system practically unusable.

I must add something that I just found: When I ask the system to "Lock Screen" and wait for more than a minute or so, the system just hangs up; it can come back again only if I move the mouse within a minute or so; otherwise, I have to do hard boot.

However, if I ask th system to "Log Off..." then the system seems to be fine even 15 minutes or so later and would let me log back on. I feel that there might be a bug in the system that makes the system hang up like that.

Regards,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
Something like this
```
hot6ft2@UUE-2-laptop:~$ sudo fdisk -l
[sudo] password for hot6ft2: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd03d783

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463        9612    41367375   83  Linux
/dev/sda3            9613       60801   411175642+   f  W95 Ext'd (LBA)
/dev/sda5           58625       60552    15486628+  83  Linux
/dev/sda6           60553       60801     2000061   82  Linux swap / Solaris
/dev/sda7            9613       13631    32282554+  83  Linux
/dev/sda8           13632       58624   361406241    7  HPFS/NTFS

Partition table entries are not in disk order

```
and that's a lower case -L after fdisk

And you should have a recovery mode option at the grub screen.
Since you did an upgrade you are probably still running grub legacy so when it says
Grub Loading...
hit the Esc key to get to the grub menu

Your issue may not be the same as mine was but it wont hurt anything to run fsck it's a check of the filesystem like windows chkdsk.

---

### Post by tperwez on 2010-04-17
Soory for the earlier post: I had made a mistake. Here is the out out from the fdisk command:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         125     1004031   82  Linux swap / Solaris
/dev/sda2   *         126        4182    32587852+  83  Linux
/dev/sda3            4183       25944   174803265   83  Linux


Do you think I need to run 

fsck /dev/sda3

on the sytem?

Could you please also let me know how to start in the recovery mode? I am clueless on this. Regards,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
> **tperwez said:**
> Soory for the earlier post: I had made a mistake. Here is the out out from the fdisk command:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         125     1004031   82  Linux swap / Solaris
/dev/sda2   *         126        4182    32587852+  83  Linux
/dev/sda3            4183       25944   174803265   83  Linux


Do you think I need to run 

fsck /dev/sda3

on the sytem?

Could you please also let me know how to start in the recovery mode? I am clueless on this. Regards,

Tariq
sda2 appears to be the boot partition.
Do you have a separate /home partition?
If not what is the other Linux partition?
Whichever one is ubuntu is the one you want to run it on, either sda2 or sda3. Or both, one at a time.

And you should have a recovery mode option at the grub screen.
Since you did an upgrade you are probably still running grub legacy so when it says
Grub Loading...
hit the Esc key to get to the grub menu and select Recovery
Then after all the text scrolls by select Shell Prompt
The prompt will show up at the bottom of the screen.

Your issue may not be the same as mine was but it wont hurt anything to run fsck it's a check of the filesystem like windows chkdsk.

---

### Post by tperwez on 2010-04-17
Thanks for all your advice. However, could you please help me on this probelm that I just ran into. 

I entered the recovery mode and then went to the root shell prompt. Then I entered

fsck /dev/sda3

and got a nasty warning that the filesystem is mounted and could suffer serious damage.

I chose "n" to exit from the command. I wanted to get out from the recivery mode and retart the system. So I gave the command 

exit

and I am still logged in as a user (not root) because it asked for login name and password.

How do I exit from all this and get back to the usual GUI?

I would appreciate your advice.

As for the asnswer to the other partition directory, I will have to get back to the usual GUI and re-enter the 

sudo fdisk -l

to find it. 

Thanks. Regards,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
type in reboot and hit Enter
Or ```
sudo reboot
``` if you're not root
Strange it didn't say anything like that when I ran it.
Oh well.

---

### Post by tperwez on 2010-04-17
Thanks again. I did eneter

reboot

but it asked for the login name etc.

Anyway, it does not matter anymore because in the meantime, the screen has gone blank and is not responding anymore. I think I will need to just do another hard boot!

It really sucks since I have wasted an entire day on this and still no apparent solution. I appreciate your advice and all the suggestions. Best,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
I guess that since you did an upgrade instead of a fresh install it would be pointless to say to do it from the livecd.
It sounds like your upgrade didn't go so well, you may end up reinstalling if no one comes in with another solution.
Time to eat Dinner here.

---

### Post by tperwez on 2010-04-17
> **2hot6ft2 said:**
> type in reboot and hit Enter
Or ```
sudo reboot
``` if you're not root
Strange it didn't say anything like that when I ran it.
Oh well.


I am back in the system again. Here is the full output of the 

sudo fdisk -l

command. 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00081d9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         125     1004031   82  Linux swap / Solaris
/dev/sda2   *         126        4182    32587852+  83  Linux
/dev/sda3            4183       25944   174803265   83  Linux


Does it answer your question about the other partitions etc? What partition should I run the fsck command on? Regards,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
> **tperwez said:**
> 
```
/dev/sda2   *         126        4182    32587852+  83  Linux
/dev/sda3            4183       25944   174803265   83  Linux


```
Does it answer your question about the other partitions etc? What partition should I run the fsck command on? Regards,

Tariq
Looks like it should be sda3
Judging by the size I think sda2 is just a boot partition.

---

### Post by tperwez on 2010-04-17
> **2hot6ft2 said:**
> Looks like it should be sda3
Judging by the size I think sda2 is just a boot partition.

Than you so much again. You are right, sda2 is the boot partition.

However, as I wrote earlier, when I entered the recovery mode, went to root shell and entered

fsck /dev/sda3

I got the warning that this filesystem is mounted and can suffer irreparable damage. So I backed off and entered "n" to get out of the command thinking that perhaps I was trying to run the command on the wrong partition. What should I do then? Do I need to "unmount" something? I am very hesitant to do something if I cannot get out of it easily. Best regards,

Tariq

---

### Post by neonathon on 2010-04-17
sorry to not know what you are talking about, but does anyone know how to make a new post, because i can't seem to figure it out

---

### Post by 2hot6ft2 on 2010-04-17
You should be able to run it on both, one at a time that is.
Maybe you can figure out which one is your ubuntu better by going to
System > Administration > GParted
Since I don't know if you made a separate /home partition.
Or run ```
df -hT
```
and post the output

---

### Post by 2hot6ft2 on 2010-04-17
> **neonathon said:**
> sorry to not know what you are talking about, but does anyone know how to make a new post, because i can't seem to figure it out
You just did. If you mean a new thread click on Ubuntu Forums in the top left then pick the best sub section for your topic then click on New Thread.

Like I said mine didn't give that warning and I don't know why yours did. Mine actually said there were errors when I went into recovery mode and told me to run it. So I don't know what to say at this point.

But it's time to eat so I'll be back in a while.

---

### Post by tperwez on 2010-04-17
> **2hot6ft2 said:**
> You should be able to run it on both, one at a time that is.
Maybe you can figure out which one is your ubuntu better by going to
System > Administration > GParted
Since I don't know if you made a separate /home partition.
Or run ```
df -hT
```
and post the output


thank you for your helpful ideas. 

This is the info from GParted:

Partition     File system    Mount point

/dev/sda1     linux-swap  

/dev/sda2      ext3          /            (Boot)

/dev/sda3      ext3          /home

Unallocated    Unallocated


(I have left off the size etc)

Does this help? It does seem that sd3 is the /home filesystem. What course of action should I be taking?  Regards,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
If you have a livecd you could boot into it and run it from the livecd session that way the partition wouldn't be in use at the time. The commands would be
```
sudo -i
```
then ```
fsck /dev/sda3
```

This is all assuming there may be a problem with the file system like mine had which was fixable that way.
There are other people have freezing problems so you're not alone. You want to see what you can find out in this thread.

[Random freezing in 9.10 karmic]("http://ubuntuforums.org/showthread.php?t=1309015")

I'll go look thru it too and see what I can learn from it.

---

### Post by tperwez on 2010-04-17
Here is something that I did not mention earlier.

I updated using ISO image for 9.10. I think I am also having trouble updating packages using the Update Manager. My system is connected to the network but in the Settings, of the Update Manager, the cdrom is selected. when I unselected, it gave me some errors for unauntheticated key etc and the sytem froze before I could read it all. 

What sort of settings need to be changed if I want to update packages using the network. 

thanks,

Tariq

---

### Post by tperwez on 2010-04-17
Here migth be some clue.

I had upgraded from 8.10 to 9.04 with ISI image and then to 9.10 with ISO image. In between, I did not reset anything in the Update manager (the upgrades were within one day of each other). Since the computer was connected to newtork, I also let it fetch any newer packages as it needed them. 

Now, I unselected the cdrom in the settings for the Update Manager and tried to update the packages. It gives these sorts of warnings:

Error

W. An error occurred during signatire verification. The repository is not updated and previous index will be used.

:
:
:

And several such errors.

It also says that xxxxxx  fialed to download etc

and

Some index files cannot be downloaded and ignored or old one used etc.


Since I upgraded using ISO image, there is some problem here about recognizing the repository perhaps.



Do you think my probem may have stemmed from upgrading twice using ISO images and not resetting the Update Manager in some fashion in between? Although the system did fetch upgraded packages during upgrades. How can I reset the update manager to start updating properly?


Regards,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
After reading all 18 pages of the thread I linked to earlier it looks like only 2 of them and the same issue as I did on page 16 and 17.
> **StuartN said:**
> Does your root filesystem go read-only during these freezes, requiring **a fsck after rebooting, with orphaned inodes**?

Actually I don't know if it's exactly the same but fsck fixed mine and it did have those types of errors.
> **go2dell said:**
> YES!  I have exactly the same problem with 9.10.
And there's no simple answer to the problem.
Some fixed it by downgrading the graphics driver (with limited success).
Some upgraded their kernel to 2.6.32 and 2.6.33 (with limited success).
Graphics cards varied nVidia, Intel and ATI were all affected.
Several went back to 9.04 (with limited success) since some still had freezes.

Some are getting freezes with overheating issues.
[Laptop overheating! in Karmic]("http://ubuntuforums.org/showthread.php?t=1315065")
There have been a few threads having to do with overheating just search for it.

So no real solution to the freezing problem.:(

As for your question about software sources and your upgrades. The servers are getting hammered pretty good lately with it being so close to the release date for Lucid and all the updates they're getting.
You can go to
System > Administration > Software Sources
and above the cd option is 
Download from
Click on the server and select Other
Then click on Select Best Server
It will search for the fastest server for where you are
When it finishes click on Choose server.
Then on Reload.

You can also clear up some issues like this
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```
If it has errors just run it again and it will sometimes clear things up on its own.

So I don't know what else to tell you about trying to fix the freezing.

---

### Post by tperwez on 2010-04-17
> **2hot6ft2 said:**
> 
As for your question about software sources and your upgrades. The servers are getting hammered pretty good lately with it being so close to the release date for Lucid and all the updates they're getting.
You can go to
System > Administration > Software Sources
and above the cd option is 
Download from
Click on the server and select Other
Then click on Select Best Server
It will search for the fastest server for where you are
When it finishes click on Choose server.
Then on Reload.

You can also clear up some issues like this
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get update
```
If it has errors just run it again and it will sometimes clear things up on its own.

So I don't know what else to tell you about trying to fix the freezing.

Hi 2hot6ft2

You have been most kind and gracious with advice and your time. I really appreciate it all. It seems like the issue of system lock is here to stay with me. I am (naively?) hoping that it might get solved with the newer upgrade to 10.04. 

As it stands, my system is practically unusable because it locks up 100% of the times when the screen locks after some time of inactivity. The only way it seems to go on is if I ask to "Log Off..." 

I did run 

sudo apt-get update

and then

sudo apt-get upgrade

There were no errors. The first command downloaded a lot of packages but I am not sure what it did with them. The second command reported that no new packages needed installing etc.

After that, I opened the Update Manager and clicked Check, and it did not report any errors as it did before. 

However, the system locked up again and I booted it. Now when I run

sudo apt-get update

I get the same errors again as in the Update Manager. Apparently, I am some serious issues. 

Any other suggestions?

Regards,

Tariq

---

### Post by 2hot6ft2 on 2010-04-17
That's odd. Did you have freezes in 8.10 or 9.04?
If not you might want to try 9.04 or maybe even 10.04.
I wouldn't go back to 8.10 if at all possible since it's not supported any more by now.

But before doing a fresh install of either 9.10 or 10.04 you should read this, it's rather long but well worth taking the time to read. At least the part about grub.
Ubuntu 9.10 before you install
[http://www.ultimateeditionoz.com/forum/viewtopic.php?f=67&t=341](http://www.ultimateeditionoz.com/forum/viewtopic.php?f=67&t=341)

---

### Post by 2hot6ft2 on 2010-04-18
I found out the proper way to force the system to run fsck at the next boot safely if you want to give it a shot.

To safely run fsck use
```
sudo touch /forcefsck
```

and on the next reboot it will start the fsck checking like if it had reached 30 boots.

Any time you want to force the system to do a fsck, give the above command and reboot.

And the warning that fcsk was giving you when trying to run it from the Shell prompt in recovery mode was valid. Never do a fsck checking on a mounted partition. Only the above command is safe.

---

### Post by tperwez on 2010-04-19
> **2hot6ft2 said:**
> I found out the proper way to force the system to run fsck at the next boot safely if you want to give it a shot.

To safely run fsck use
```
sudo touch /forcefsck
```

and on the next reboot it will start the fsck checking like if it had reached 30 boots.

Any time you want to force the system to do a fsck, give the above command and reboot.

And the warning that fcsk was giving you when trying to run it from the Shell prompt in recovery mode was valid. Never do a fsck checking on a mounted partition. Only the above command is safe.

Thank you very much for this advice. Somehow, my instinct did not let me go through the fsck earlier. I will try your suggestion. 

One thing I have noticed is that when I do hard boot after a crash, I see a message that reads something like:

xxxxx   cannot be mounted yet
Waiting


and then after a while the system begins to boot up. I have not been able to remember all of the above message because it disappears withing a second or so. I have seen it prstty much every time I reboot after crash.

Furthermore, I cannot update any packages from the Update Manager (or by sudo apt-get update). I get error messages of "Failed to fetch ...". I have seen many other posts where folks get similar messages but no apparent solution has been suggested.

I have resigned myself to the real possibility of clean install. I am hoping that this will fix the problem. It is just annoying that I will be staring from scratch on a system that was working so smoothly until two days ago. Perhaps doing the upgrade from ISO image was a mistake after all.

I appreciate all the advice you have given.

Regards,

Tariq

---

