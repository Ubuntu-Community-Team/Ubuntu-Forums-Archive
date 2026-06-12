---
title: "Replacing existing OS with Ubuntu"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by Braximus on 2011-05-10
Good evening folks. I am very new to this so please bare with me. Today I decided to try Ubuntu. I have a spare desktop computer that is already having an issue with a Windows XP installation so I let it sit and collect dust for a few months. Figured why not use this. Anyways the Windows installation is junk so to speak and it wont boot up the OS, I am able to use the "Try Ubuntu" option but when I try to actually install it, it tells me there is not enough free space 2gb i think it was it install it. So I thought maybe the drive should be reformatted but I am unless how to successfully do this. I read over a few of the existing threads and used the search query feature but I am so confused as to where I should start with this.

I thought that maybe I should use a windows disc to atleast erase the current partition but I don't even have a windows disc so that's not an option.  How can I go about resolving this issue with the amount of space required for installing Ubuntu? Any and all suggestions are greatly appreciated.

---

### Post by spcwingo on 2011-05-10
During installation you should have an option to "use entire disk" or something to that effect.  That'll wipe out that pesky XP.  :popcorn:

---

### Post by wojox on 2011-05-10
If you want to get rid of Windows just tell Ubuntu to use the whole drive.

---

### Post by Braximus on 2011-05-10
> **spcwingo said:**
> During installation you should have an option to "use entire disk" or something to that effect.  That'll wipe out that pesky XP.  :popcorn:
It comes up with a screen that has a checklist. checks for three things. space, net connection, and one other. doesnt seem to let me proceed cause the space isnt available.

---

### Post by spcwingo on 2011-05-11
What version are you trying to install because they may have changed something in the installer on the latest release [11.04(which I'm not familiar with as I'm still using 10.04 LTS)].  If 11.04 is what you're trying to install I'm sure that it would still have gparted on the live CD.  You can try running it and deleting your Win partition from there and then retrying the installer.

---

### Post by Braximus on 2011-05-11
> **spcwingo said:**
> What version are you trying to install because they may have changed something in the installer on the latest release [11.04(which I'm not familiar with as I'm still using 10.04 LTS)].  If 11.04 is what you're trying to install I'm sure that it would still have gparted on the live CD.  You can try running it and deleting your Win partition from there and then retrying the installer.

10.10 is what I have on a disc.

---

### Post by spcwingo on 2011-05-11
Even in 10.10 you should still have that option to use the entire disk at install time...no big deal, you can still blast the XP partition from gparted.  After that, you can retry the installer.

---

### Post by Braximus on 2011-05-11
> **spcwingo said:**
> Even in 10.10 you should still have that option to use the entire disk at install time...no big deal, you can still blast the XP partition from gparted.  After that, you can retry the installer.
I am not even sure what gparted means. Sorry I am very new to this.

---

### Post by Hakunka-Matata on 2011-05-11
11.04 has been released, and it's fast, so far the best Release.  why not install it instead of 10.10

---

### Post by Braximus on 2011-05-11
> **Hakunka-Matata said:**
> 11.04 has been released, and it's fast, so far the best Release.  why not install it instead of 10.10
Hmm. Good question. Guess I'll burn this to a disc and give it a try. Thanks for the effort guys. Really means a lot.

---

### Post by Hedgehog1 on 2011-05-11
If I might offer a 'how-to' guide for manually installing Ubuntu:

**[SIZE="3"]Ubuntu Only Install[/SIZE]**

Boot of an Ubuntu LiveCD/LiveUSB, select 'TRY', and then menu to System >> Administration >> Gparted Partiton Manager.

**Create a clean, new partition map so you start with a 'clean slate':**

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]

**Then begin creating 3 partitions for '/' (root) '/home' & Swap:**

[IMG]http://img853.imageshack.us/img853/503/mbrpariondemo04.png[/IMG]

**Make your root partition 20-30 gigs**

[IMG]http://img7.imageshack.us/img7/2554/mbrpariondemo05.png[/IMG]

**Make your '/home' partition all the rest of the disk space except that you need for swap (swap = RAM size + 10%)**

[IMG]http://img851.imageshack.us/img851/2815/mbrpariondemo06.png[/IMG]

**Next your swap partition:**

[IMG]http://img132.imageshack.us/img132/8353/mbrpariondemo07.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-11
**Press the 'check mark' button to make the changes real:**

[IMG]http://img402.imageshack.us/img402/5460/mbrpariondemo08.png[/IMG]

**gparted will ask this:**

[IMG]http://img826.imageshack.us/img826/7826/mbrpariondemo09.png[/IMG]

**Then it updates your partitions:**

[IMG]http://img101.imageshack.us/img101/5706/mbrpariondemo10.png[/IMG]

**You can see a list of the changes made once the work is done:**

[IMG]http://img862.imageshack.us/img862/7135/mbrpariondemo11.png[/IMG]

**And a view of what the partitions look like after the update:**

[IMG]http://img600.imageshack.us/img600/4516/mbrpariondemo12.png[/IMG]

**Now when you install, select the 'something else' option in 11.04 or the 'manually' option in 10.04 or 10.10**

**And tell the install to use the three partitions this way (Your Drive is likely /dev/sda, not the /dev/sdc this screen shot was taken from):**

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]

**Please install the bootloader on /dev/sda - not sda1 or sda2, just /dev/sda.**

***The Hedge***

---

### Post by Braximus on 2011-05-11
Thanks for the guide. Ill give this a try and see how it works out

Says no devices detected?

---

### Post by spcwingo on 2011-05-11
From the live CD open a terminal and input this command:

```
sudo fdisk -l
```

(it's a lower case L in the command) and post the output in your next reply.  That'll help us by showing your current partitioning layout of your hard drive.

---

