---
title: "Partial install problem"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by JustGus on 2010-06-17
The other night I tried to upgrade my system to Karmic Koala.  The machine took forever to download the packages and when it was almost completed, the installation phase in the Update Manager suspended.  Both keyboard and mouse weren't responsive so I was forced to shut the system down manually. 

Now when I boot up, it loads the desktop, a dialogue box pops up stating there's an Apt Authentication issue.  When I click "Run this action now" it opens opens a window showing it is about to download 15 packages, but unfortunately before it can load, the system hangs.  If I reboot, close the dialogue box and try to use the Update Manager as a means to correct the problem, the same thing happens.  

In addition to trying to find a solution, I'm keen to avoid doing a full, clean install, as I don't want to lose the system configs and data (I've got 200gb in music files and use the system as a music server)

I've also tried to load in "recovery mode" but it doesn't load properly.   
Any help/suggestions would be hugely appreciated!

Cheers,

Gus

---

### Post by leorolla on 2010-06-17
You can run```

sudo apt-get update
sudo apt-get upgrade
```
and post here the output.
This way will help us figure out what went wrong with your upgrade.

---

### Post by JustGus on 2010-06-17
Thanks v much for the suggestion. 2 things are now happening...
Firstly, in the early stages of the boot up process (when the white ubuntu logo pops up) the system starts a test/check process of the file system.  I have to hit ESC as it stays cycling through the process.  
Secondly, when the boot up completes and I launch the Terminal, I'm able to enter the password for the system but everything freezes within seconds of the Terminal window opening.
It appears that launching an application is what causes the system to lock up, having now tried with the Update Manager, Firefox, the Terminal.
I do have a pendrive with Karmic Koala on it. Is there any way I can boot with that but use some process to repair the operating system on my HDD (and so avoid wiping all my data and configs)?
Thanks again!

---

### Post by leorolla on 2010-06-18
A good idea at this point is to back up your data at some external HD.

Boot from Ubuntu 10.04 Live USB, try to mount you HD partition and copy the contents of your home folder to the external storage device.

You can also at this point check if your filesystem is OK.

After you have a safe backup, one quick solution is to install Ubuntu on the same partition but without formatting. This will keep your /home safe, but you will have to re-install all the programs and re-do all your tweaks/configurations (only those you have made with 'sudo'; the configurations you do as a normal user, like firefox etc, are safe inside /home).

---

### Post by JustGus on 2010-06-18
Thanks for the advice. I'm in the process of copying the files to a backup now. I take it there's no way I can boot with the pendrive but somehow run a process that will correct the install errors?  Or does the file check do this?  Not sure how to run this as i'm operating Ubuntu at a very basic level!

---

### Post by leorolla on 2010-06-18
So you could see your partition and all your files? Good news.

You can open System->Administration->DiskUtilities and check the filesystem.

But that is just to see if this is the problem... propably it isn't and filesystem check will not fix it.

We don't know what the install errors are... how important are your congis settings? Did you do a lot of tweaking etc. to have your hardware working well? If you don't mind reconfiguring the install, I would go for a re-install. Just make sure you choose "manual partition" and do NOT check the format checkbox for the main partition.

---

### Post by JustGus on 2010-06-18
I've tried to run the disk utility, but the screen blacks out after a while and I'm not able to get the desktop to reappear.

My pendrive has the option to install 10.4, which I've launched.

It shows that 9.10 is currently installed and offers 4 options:
1) Install 10.4 and leave 9.10, as a side-by-side option, to be chosen at startup. (not particularly desireable as I'd rather just dump 9.10) 
2) Erase and use the entire disk (don't want to do this for obvious reasons)
3) Use the largest continuous free spacde
4) Specify partitions manually.

The option I was hoping for was to simply remove 9.10 and replace it with 10.4.  

If I go ahead and choose option 1) is there the ability to remove 9.10 after and have it automatically boot with 10.4?

Seems like the full install is likely the only option. Unfortunately there are a number of tweaks I guess I'll lose (setting up Wake On LAN, auto shutdown each evening, squeezecenter launch on startup, etc) which took me awhile to figure out. Oh well.

Thanks for the help so far!

Gus

---

### Post by leorolla on 2010-06-19
I would go for (4) and uncheck the "format" box of the corresponding root partition. It will overwrite Ubuntu 9.10 system folders but not /home.

Before that, you can browse this root from the Live Session and grab the files corresponding to your tweaks, at least the ones you remember.

And next time, take notes of your tweaks elsewhere. I save mine as firefox bookmarks that are synchronized via 'firefox sync' addon.

---

### Post by JustGus on 2010-06-19
Thanks for the advice (again!).  
So, have selected option 4, but 2 problems are coming up.  1) The machine freezes (even though I'm using the pendrive), so I have to reboot.  2) If I do make it to the screen "Prepare Partitions" and select what I *think* is the root file system "/dev/sda1" I get a pop up window saying "No root file system is defined".  

I've no idea what to do.  Not sure whether I should drag the partition to take up the rest of the (unused) HDD space, or whether I should just nudge it up a bit.  Sorry.  This whole partitioning system is greek to me!

On the bright side, I've also managed to get the Disk Utility to run, to check the file system on the HDD and it's coming up clean...which is a bit of good news!

---

### Post by leorolla on 2010-06-19
Hum... could you boot the USB, open the terminal and post here the output of
```
sudo fdisk -l
df
```
?

Before running these, open the HD partitions with the file manager.

This will help knowing about your filesystems and how much free space you have.

---

### Post by JustGus on 2010-06-20
Hmm.  *Finally* managed to get the system to stay live long enough to do a clean install and reboot...only to find that there's still a persistent, erratic problem where the screen freezes after awhile.  In the end I opted to wipe everything (first copying all my data on a separate hdd, to be reintroduced later).
I'm assuming given all this that the culprit must be a hardware problem.
Thanks, leorolla, for all your help.  I'ts been very much appreciated!
Gus

---

### Post by leorolla on 2010-06-20
The commands I asked you to run before are intended to realize how you are supposed to reinstall without formatting.

---

### Post by JustGus on 2010-06-22
Hi leorolla
I understood that, but in the end decided that given how the machine kept locking up, that it might be better to just do a full install.  I've got the data all backed up.
Thanks so much for your help.

BTW, I'm stumped as to the why the machine still locks up.  Given this history, could you hazard a guess on the likely root of the problem?  Does it seem like a hardware issue?  Perhaps motherboard firmware?  Any ideas?

Cheers,
Gus

---

### Post by leorolla on 2010-06-22
We can try to guess. You will have a fresh 10.04 install. So you can apply the updates but just a few of them every day, until you (i) finish all updates without problems woohool or (ii) get the same problem again, in which case it will be easier to undo *those* updates until you find *the* problematic package and then it will be important to file this stable release update regression bug.

---

