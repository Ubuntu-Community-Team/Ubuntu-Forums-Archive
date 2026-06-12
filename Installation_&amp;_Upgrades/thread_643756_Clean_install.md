---
title: "Clean install"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by peakshysteria on 2007-12-18
After some considerations i think want to run a clean install. Currently i'm running a dual boot with XP pro X64 and Ubuntu 8.04 Hardy Heron Alpha 1. Can someone tell me how to run the install via the install cd over the existing Ubuntu partition? Meaning; i'm a bit concerned about affecting the existing Xp partitions. Is there an easy way of doing this?

---

### Post by ajgreeny on 2007-12-18
Just download the heron CD (or whatever version you want to clean install) and install, choosing the partition where your current version upgrade is installed.  There shouldn't be a problem as far as I know.  It should be just like any other clean install over an existing version; just make sure you choose the right partition, and back up everything first on both winXP and heron before you do it.

---

### Post by wharp on 2007-12-18
It should be fine.  When the installer gets to the point where it asks where you want to install, select Advanced and tell it to use the existing partitions.  It will help if you know which partitions XP and Ubuntu are currently on.

---

### Post by peakshysteria on 2007-12-18
> **wharp said:**
> It should be fine.  When the installer gets to the point where it asks where you want to install, select Advanced and tell it to use the existing partitions.  It will help if you know which partitions XP and Ubuntu are currently on.

Hmm, choosing the right one of the three in [step 4]("http://www.futuredesktop.com/images/gutsy/picture_4c.jpg") (if my memory serves me right) is the only difficult thing. And yes i think i'll go back to Gutsy even though it doesn't do my ATI card justice :)

If i choose manual partitioning, i can use the installer to resize existing FAT or NTFS partitions to create room for the Ubuntu install: and simply select the partition and specify its new size. According to the [install doc]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/howto-installation.html"). I've been at this step before, but i've never had to choose an existing Ubuntu partition. So i wonder how thess will identify itself??? Can i clearly see what is windows partitions and what is the Ubuntu partition if i choose manual? Or should i pick one of the other options? Clearly the first one's not it since it's automatic and little adaptable to my question. 

And can i go back after i have choosen manual? If so i can just see what manual brings. And if it is as intuitive as i think it is then i can go through with it.

---

### Post by wharp on 2007-12-18
If you let the installer do the partitioning the first time, you likely only have 3 partitions I think.  One should be your XP partition formatted as NTFS.  One should be your swap partition.  The third should be / formated as ext3.  You may or may not have a separate partition for /home.  You can run gparted and take a look at what partitions you currently have before doing the install.  

To do what you want to you'll need to use the manual option though.

---

### Post by peakshysteria on 2007-12-18
Xp currently have four partitions on three HDD's. C:\ and D:\ on the same partition as the Ubuntu partition. And two more HDDs with one partition each. So my only concern is if i can pinpoint the existing Ubuntu partition via the Manual option and make a clean install on that partition. Not sure how i will see it.  But should be easy if those other two (C:\ and D:\) is recognizable. I'll try this tonight then. More advices are welcome thou :)

---

### Post by meindian523 on 2007-12-18
I would think it would be pretty easy to recognize the Ubuntu partition by the filesystem(ext3)...provided of course you select the correct HDD from the three you have from the drop-down at the top-right.....

---

### Post by peakshysteria on 2007-12-18
I was hoping that you guys had experienced something similar and so could tell me if an existing Ubuntu partition would identify itself clearly under reinstalling/installing a new Ubuntu version on an existing Ubuntu partition. Well, thanks you guys, I've at least pretty confident it's the manual option which is right for me. Let's hope you guys are right and it goes like a breeze as usual :)

---

### Post by meindian523 on 2007-12-18
The manual option IS always the best if you want to dual boot and know exactly what you do when you create/delete a partition.....

Delete:Lose all data
Create:Make a container for your files,if you select an existing partition,lose all data due to format.....

of course,the create explanation has been modified to suit this particular context..... :)

---

### Post by peakshysteria on 2007-12-18
Is there a way/command i easily can list all my existing partitions with and then pinpoint the existing Ubuntu partition and its name before i reinstall? I'm afraid i cant choose the partition to place the new install on due to not knowing exactly which is the Ubuntu one :confused:

---

### Post by meindian523 on 2007-12-18
```
sudo fdisk -l
```

that's a small "el" not a L......

---

### Post by tmm2112 on 2007-12-18
I have this exact same concern, reinstalling over an existing Gutsy partition.  ext3 is the linux format, which distinguishes it from Winders (NTFS or FAT32).  

I've been pondering this for a few days and I think I'll give it a shot.  I'm making the assumption that one needs to override the auto resize function and just use all the avialable space for this partition.  Riiiiight?

---

### Post by peakshysteria on 2007-12-18
Almost pissed my pants. But everything (nearly) went very smooth. I was unsure how the partition would show itself. But in console tested with: **mount** which gave me sda2 ext3 on line one. ext3 is an indication of a linux partition i'm told. I also wrote: **df .** (see the dot?) which also gave me sda2.

No confident i started the install. In step four the partition is decided. I chose Manual. And everything was as intuitive as everyone have posted above. All my four windows partitions identified itself as either Fat or NTFS and the existing Ubuntu partition identified itself as sda2 ext3 in addition to a swap. The rest was a walk in the park. Or so i thought.

Once the install process was going ahead and everything seemed to go well the install froze at aprox 59%. Leaving it alone gave me an error after half an hour telling me it could be something wrong with either the install disc, the HDD or the DVD/CD-rom. The HDD is two years old and should be ok as far as i know. The DVD is external and getting old. SO this could be it. I replaced the cd with another one (i had two different ones in case of trouble). Then going true the install process once again. But this time is stopped after aprox 15%.

Then after removing the disc and restarting the machine i'm prompted with:

GRUB loading, please wait_ _ _

Error 15
_

And there it ends. Cant go further from there. It want take my two Gutsy discs or the alternate disc. Trying the Win Xp disc also failed and ended in the same Grub error 15.

Any suggestions?

---

### Post by tmm2112 on 2007-12-18
Ouch!  On second thought, maybe I won't try that myself.  Why that wouldn't work is a mystery to me.

Peak, did you resize that partition or install it at full size?

---

### Post by wharp on 2007-12-18
Have you installed from that disk before?  There is an option at startup (when booting from the install disk) that will let you check the disk for errors.  You might want to try that.  If that checks out, it could be a problem with your hard drive.  Just because its 2 years old doesn't mean there can't be problems with it.  Hard drives fail all the time.

---

### Post by tmm2112 on 2007-12-18
To update, I just tried to install over my existing partition using guided partitioning.  Didn't work.  Although  I used guided partitioning, I asked it to resize hda1 to full size.  I think this was a mistake.  It seemed to go through the install as usual, but when I booted back up, the same problems existed, my same old account, but now I had a new, smaller partition and a new, smaller swap.  So, now I'm trying to undo this mess in partitioning and having little luck.  Looks like I have a total reinstall on my hands, which sux because now I'll have to wipe my XP as well.  Not really looking forward to this.  This partitioning stuff seems awfully complicated and testy.

---

### Post by wharp on 2007-12-18
It can be confusing at first, but its really pretty straight forward.

---

### Post by meindian523 on 2007-12-18
> **tmm2112 said:**
> I have this exact same concern, reinstalling over an existing Gutsy partition.  ext3 is the linux format, which distinguishes it from Winders (NTFS or FAT32).  

I've been pondering this for a few days and I think I'll give it a shot.  I'm making the assumption that one needs to override the auto resize function and just use all the avialable space for this partition.  Riiiiight?

Just use the manual partitioning option and select your ext3 partition,mount it as / and allow it to format......simple as that

---

### Post by peakshysteria on 2007-12-19
meindian523 is right. Choose Manual in step 4 and it all is pretty intuitive really :)

The install process stopped at 59% last night. So that's what really screwed things up for me. Could be because my DVD-rom is dying or maybe the install disc was bad (i have used this on three occasions before. With luck). Or it might be the HDD. So now my GRUB seems to be all f**ked up. And i cant get anywhere now :(

---

### Post by tmm2112 on 2007-12-19
You guys are right.  I wiped out my linux partitions, then rebooted.  then I went into install, manual, and chose the unformatted portion of my drive for installation.  Worked perfectly.  I'm now downloading updates and such.

Thanks for the help.  Now if I can just get this darn wireless card to work...:confused:

---

