---
title: "Updating to Lucid"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by Doug11 on 2010-04-26
I know Lucid is not on the update list yet through the update manager,,but is there a way to update without doing a fresh install from the dvd. I don't want to have to backup all my photos and music and such. I know that I should whenever taking a major upgrade. I do however have them on my Laptop though.

---

### Post by cak3 on 2010-04-26
yes, there is. Once it is released, the upgrade will be available through update-manager, but if you want to upgrade before then, run
```

sudo update-manager -d

```

the -d option has it check if a devel release is available to update to.

---

### Post by dnr1128 on 2010-04-26
I have a similar question.  Can I install off the CD without losing all my data?  I've heard something about running the live cd and installing from there, but selecting to NOT format the partition.  Supposedly that will only replace the old system files with the new ones but not overwrite the userdata.  I don't want to do an upgrade but do a clean install without losing my music, pictures, etc.

---

### Post by Doug11 on 2010-04-27
> **cak3 said:**
> yes, there is. Once it is released, the upgrade will be available through update-manager, but if you want to upgrade before then, run
```

sudo update-manager -d

```

the -d option has it check if a devel release is available to update to.

Thanks,,i will give that a shot and see how it goes.

---

### Post by darkmakozu on 2010-04-27
> **dnr1128 said:**
> I have a similar question.  Can I install off the CD without losing all my data?  I've heard something about running the live cd and installing from there, but selecting to NOT format the partition.  Supposedly that will only replace the old system files with the new ones but not overwrite the userdata.  I don't want to do an upgrade but do a clean install without losing my music, pictures, etc.

I know there is a way to do it with the alternative install CD, but i'm not 100% sure about the live disk.

---

### Post by Jonny87 on 2010-04-27
I've got a couple question along these lines and I don't want to start a new thread just for it.

I ve decided that I want to do a clean install from scratch as I want to re-arrange the partition setup, i.e. put the home folder on a separate partition as I should have done to start with. When I do this can I just copy a copy the old home folder over to transfer all the old file and program settings etc or will there be problems. Also if I installed it on another partition along side of the 9:10 install, would it transfer the settings etc during the process and what exactly would it transfer?

---

### Post by Vined Adobo on 2010-04-27
Disregard--duplicate msg.

---

### Post by Vined Adobo on 2010-04-27
> **dnr1128 said:**
> I have a similar question.  Can I install off the CD without losing all my data?  I've heard something about running the live cd and installing from there, but selecting to NOT format the partition.  Supposedly that will only replace the old system files with the new ones but not overwrite the userdata.  I don't want to do an upgrade but do a clean install without losing my music, pictures, etc.


There is no better way to ensure that an upgrade will go well than to backup your precious files (especially family photos.)  Back them up to  cds, dvds, memory sticks, every other computer on your home network AND to your safety deposit box...better rent TWO and sync them with each other.  Trust me, when you lose those files, it's as bad as a fire destroying your home.  You can recover from everything burned except your mementos.  Once they're gone, they're gone forever.

O.k. I'm getting off my soapbox now.  Once you have backed up your home directory, you can go ahead with a normal update. Since you backed up,  IF something goes awry, you can recover.  I upgraded last night.  everything went well.

Ususally, I backup my home directory, and install as new.  I use manual partitioning and I format the partition which has everything other than /home but I do not format the /home partition.  Two releases ago, I installed fresh and put /home in its own partition (very smart.)  With this method, I do have to re-install the files which aren't on the live cd, but even so, it's FAR quicker to re-install these files and directories than to UPGRADE to a new Ubuntu version (my opinion only.)

I have done stupid things while learning and had to start all over, losing everything.

Had I backed up, I would have been far better off.

Since I started backing up before doing anything stupid, I've had some problems, which were easy to overcome.

In final analysis, you can upgrade and lose nothing; however, don't tempt fate.  You'll be happier!

Dave

Please note:
Disclaimer:  The methods I use to go to a new release may not be best for you

---

### Post by Doug11 on 2010-04-28
That seemed to work OK. But I seem to have a lot of duplicate stuff in my grub list. I dual boot with Doze 7. How can I edit my grub list to make it simple again. THX.

---

### Post by finnlloyd on 2010-04-28
I'm planning on doing a fresh install but I am currently running the 10.04 rc (which was a clean install).  Is the update process good enough in this case?

---

### Post by mlan on 2010-04-28
Just upgraded 9.10 to 10.04 RC. No issues, everything is working perfectly. :P

---

### Post by dnr1128 on 2010-04-28
> **Vined Adobo said:**
> There is no better way to ensure that an upgrade will go well than to backup your precious files (especially family photos.)  Back them up to  cds, dvds, memory sticks, every other computer on your home network AND to your safety deposit box...better rent TWO and sync them with each other.  Trust me, when you lose those files, it's as bad as a fire destroying your home.  You can recover from everything burned except your mementos.  Once they're gone, they're gone forever...

I'll be backing stuff up onto a flash drive, just in case it doesn't work and I have to do a clean install.

---

### Post by garvinrick4 on 2010-04-28
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list &&  sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by nishanvincent on 2010-04-29
I had upgrade from karmic to lucid lynx RC last week directly using update-manager -d
Can I upgrade from Ubuntu 10.04 RC to Ubuntu 10.04 in the same way?
Currently its not showing any new version when I do that...

---

### Post by maddg3241 on 2010-04-29
Now It Has Been Realesed (proves it here) [[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1465419[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1465419") Download Here [[COLOR=#444444]http://releases.ubuntu.com/releases/10.04/[/COLOR]]("http://releases.ubuntu.com/releases/10.04/")

---

### Post by Cushie on 2010-04-29
> **Doug11 said:**
> That seemed to work OK. But I seem to have a lot of duplicate stuff in my grub list. I dual boot with Doze 7. How can I edit my grub list to make it simple again. THX.

Doug, if you mean older versions of linux core file just use 'Synaptic'  and search 'linux' to remove older versions completly and then Alt F2 'sudo update-grub' and grub sorts it all out for you.

If they are not in 'synaptic' you will find older versions in '/boot' where I have just deleted them then run 'update-grub'

---

### Post by Doug11 on 2010-04-30
> **Cushie said:**
> Doug, if you mean older versions of linux core file just use 'Synaptic'  and search 'linux' to remove older versions completly and then Alt F2 'sudo update-grub' and grub sorts it all out for you.

If they are not in 'synaptic' you will find older versions in '/boot' where I have just deleted them then run 'update-grub'
No,,not older versions. Actually duplicate kernels. There is always two kernels, one normal and the other generic and your memtest and whatever else you boot. My new kernel is listed an extra two times. Just makes it look real cluttered. Thought there may be some .list I could edit somewhere.

---

### Post by Doug11 on 2010-04-30
OK,,i looked in my /boot folder and there are a few duplicate files. I can't remember how ot get my admin rights so I can remove them.

---

### Post by Doug11 on 2010-04-30
OK,,got it all worked out. Problem solved.:popcorn:

---

