---
title: "PROBLEM: Ubuntu 8.04 install with multiboot and fake RAID"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Herbert_Vaucanson on 2008-04-30
Hi all!

I am trying to install Ubuntu on a fakeRAID array (configured as raid1 = mirroring) in a dual booting configuration with WinXP.
I got a Gigabyte p35ds3r mobo, with an Intel Ich9r chipset.

I have on my back a succesful experience of dual booting WinXP and Gentoo on the same fakeRAID setup, which I decided to switch to a WinXP-Ubuntu because I run out of stamina while installing the wonderfully configurable, box-optimized Nvidia drivers + XorgX11 + LightGnome...

I read the [Ubuntu FakeRAID Howto]("https://help.ubuntu.com/community/FakeRaidHowto"), the  [Ubuntu FakeRAID 0 HowTo]("http://ubuntuforums.org/showthread.php?t=630644") and [How to Multi-Boot]("http://ph.ubuntuforums.com/showthread.php?p=4518862").

I tried to post on these threads-howtos to get help, but on one thread I was slightly off-topic, while the other looks a bit in a lull of activity. Moreover, noone concerned Ubuntu 8.04 (Hardy Heron) so far.
So I decided to start a new thread, thinking this might be useful to other folks, too. Just think how many people with a WinXP fakeRAID box are trying to avoid the Vista tourist trap, but are not yet confident enough to jettison the, ahem, Linus deck of WinXP. Or want to keep playing that cool game which unfortunately does not run pleasantly in Wine. But still would like to plunge the toes into Linux, with as few problems as possible.

Ok, now to business. What I did:
[LIST=1]
[*]I boot the Ubuntu 8.04 install CD
[*]I installed dmraid: sudo apt-get install dmraid; sudo dmraid -r
[*]I saw the array as expected, and I partitioned it: sudo fdisk /dev/mapper/myarrayfunkyname
[*]I rebooted in order to read the modified partition table
[*]After reboot (and reinstallation of dmraid) I saw again the array (as expected) with the updated partition table
[*]I formatted the new partitions without problems (2 EXT3, 1 SWAP and 1 EXT2), then I shut down to go to sleep.
[/LIST]

The day after I tried to go on with my "monkey sees, monkey does" approach through the howtos.

[LIST=1]
[*]I boot the Ubuntu 8.04 install CD
[*]I installed dmraid: sudo apt-get install dmraid; sudo dmraid -r
[*]dmraid installs and drop a line quoting myarrayfunkyname, which pleases me. Unfortunately, the folder /dev/mapper appears EMPTY with the exception of a "control" file or item. That's right, the array is not there anymore.
[*] I reboot without the install CD to check the sanity of my array (and mine) and find myself in the awkward situation of feeling relieved when looking at the windows logo of XP, oozily booting to life (?).
[/LIST]

Any ideas how the Bad Thing happened?

---

### Post by Herbert_Vaucanson on 2008-05-02
Come on, no ideas? Am I the only one with this problem?

---

### Post by Herbert_Vaucanson on 2008-05-05
Ok, so I had to try figure it out on my own. After contemplating dmraid messages for quite some time, I developed the following interpretation:

dmraid finds the raid array isw_alphanumstring_IntelRaid1, but activates isw_alphanumstring, without the _IntelRaid1 piece. The end result is that the raid volume activated is empty (no metadata for it) while the real array lies always inactive.

As for the reason of such a phenomenon, I came up with only one possible explanation: that the format operation performed from the Ubuntu livecd (from a command line in a terminal) somehow corrupted the metadata of the array.

Before sweating with Ubuntu I installed a copy of WinXP on the very same raid array. Windows keep working properly, so I am going to use it in my Ubuntu install, in the following way.

I am going to destroy the partitions I previously created for Ubuntu from the linux terminal, and create new unformatted partitions with the help of the Windows partitioner.

Then I am going to launch Ubuntu livecd and check if I am again able to see the array (hopefully). If so, I will format the new partitions and install the OS on them WITHOUT rebooting in between. Then I am going to install GRUB on the Ubuntu partition, not on the MBR.

If after a reboot I am NOT able to see the array anymore from the livecd, I will go back to windows, create and delete a partition in order to rewrite the array metadata, and try again. If the array appears again, I am going to install another copy of GRUB from a separate dedicate partition on the MBR, but not from Ubuntu, this time from Gentoo, because before trying Ubuntu I was able to configure a dual booting setup on my array with it.

---

### Post by ssican on 2008-05-05
See, also, Installation/SoftwareRAID:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by Herbert_Vaucanson on 2008-05-05
> **ssican said:**
> See, also, Installation/SoftwareRAID:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Thanks, but that does not really help. I am mired in an (officially unsupported) fakeRAID problem. This has nothing to do with Linux software raid which I am not planning to install, because I want to keep WinXP on the same raid array. The page you offer does provide a link to fakeRAID issues, but it is one of those I already read and sadly it does not cover my problem.

---

### Post by ssican on 2008-05-06
If you want install some software using your LiveCD, then you want "LiveCDPersistence": [https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence](https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence)

Also, make use of Search in this Forum: [http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)
Search by, RAID, Dual Boot.

---

### Post by Herbert_Vaucanson on 2008-05-06
> **ssican said:**
> If you want install some software using your LiveCD, then you want "LiveCDPersistence": [https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence](https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence)


According to the page, it does not work with Heron...
Moreover, the howtos I followed are pretty clear, the installation should work even without persistence.

> 
Also, make use of Search in this Forum: [http://ubuntuforums.org/search.php](http://ubuntuforums.org/search.php)
Search by, RAID, Dual Boot.

I tried this too, but I was not able to find anything relevant - except this very thread, listed in 3rd place.
I'll keep digging, though. And as soon as I have a bunch oh hours to play with my PC, I'll try my plan as presented some posts above.
Thanks for trying to help, though ;)

---

### Post by Herbert_Vaucanson on 2008-05-09
Ok, my strategy failed. I cannot see the array anymore from both Gentoo and Ubuntu. My guess is that something is wrong with dmraid as it is now - the name mismatch between isw_blahblah and isw_blahblah_IntelRaid1 remains.

I run out of ideas, which means that I will not be able to install Linux. The first time Gentoo let me down (so much configurable that beginners get lost) and this time Ubuntu (easy, but not supporting some of the most popular PC solutions like fakeraid in a robust way).
I will let the issue rest for a while. Then maybe I will give it another try, or I will wait for a better release.

---

### Post by dstew on 2008-05-09
Isn't the command to activate the RAID sets **dmraid -ay** ?

If you think you have a Hardy-specific problem, you could try to install Feisty or Gutsy following the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). If that works, maybe try upgrading to Hardy from within the previously installed system.

---

### Post by Herbert_Vaucanson on 2008-05-09
> **dstew said:**
> Isn't the command to activate the RAID sets **dmraid -ay** ?


Yes, I used this form too after carefully reading the man page. Altough dmraid -r worked the first time (it recognized the array).

> 
If you think you have a Hardy-specific problem, you could try to install Feisty or Gutsy following the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). If that works, maybe try upgrading to Hardy from within the previously installed system.

I am prone to believe it to be a problem of dmraid and its support of ich9r. I tried Gentoo, which worked just fine the first time around, but now I can't see it any raid array with that, too. I am puzzled.

---

### Post by mlcooper on 2008-06-13
Really curious to hear if anyone discovered how to do this with the Intel ICH9R chipset.  I'm actually installing a software RAID of Hardy 64bit now on my new box, but unfortunately from everything I read I can only do RAID1 with my two drives and have the system boot from them also.

Ideally I want to be on RAID0 to get full performance benefits.  Redundancy is not critical.

Anyone else have any luck with FakeRAID and the Intel ICH9R chipset?  I'm specifically running an ASUS P5E-VM HDMI motherboard with and integrated Intel x3500 video card that does an amazing job with Compiz Fusion.

---

### Post by blattengel on 2008-06-14
> **Herbert_Vaucanson said:**
> Hi all!
...

Ok, now to business. What I did:
[LIST=1]
[*]I boot the Ubuntu 8.04 install CD
[*]I installed dmraid: sudo apt-get install dmraid; sudo dmraid -r
[*]I saw the array as expected, and I partitioned it: sudo fdisk /dev/mapper/myarrayfunkyname
[*]I rebooted in order to read the modified partition table
[*]After reboot (and reinstallation of dmraid) I saw again the array (as expected) with the updated partition table
[*]I formatted the new partitions without problems (2 EXT3, 1 SWAP and 1 EXT2), then I shut down to go to sleep.
[/LIST]

The day after I tried to go on with my "monkey sees, monkey does" approach through the howtos.

[LIST=1]
[*]I boot the Ubuntu 8.04 install CD
[*]I installed dmraid: sudo apt-get install dmraid; sudo dmraid -r
[*]dmraid installs and drop a line quoting myarrayfunkyname, which pleases me. Unfortunately, the folder /dev/mapper appears EMPTY with the exception of a "control" file or item. That's right, the array is not there anymore.
[*] I reboot without the install CD to check the sanity of my array (and mine) and find myself in the awkward situation of feeling relieved when looking at the windows logo of XP, oozily booting to life (?).
[/LIST]

Any ideas how the Bad Thing happened?

Hello!

Here is an idea.  I had a similar experience a while ago.  I have the nforce4 chipset though.

I was installing ubuntu following the FakeRaidHowto guide -- monkey see monkey do :)  I couldn't go further because my /dev/mapper directory was empty.  It was empty because I had done "chroot /target", and forgot to "sudo mount --bind /dev /target/dev" beforehand.  So I saw /dev/mapper properly before chroot, but it was empty after I had done it.  It took a long time to figure out that I missed that line in the guide.

---

### Post by secshunayt on 2008-07-02
I'm having a similar problem with ICH9R RAID. I've been trying to set up a dual boot on a RAID0 array; I know this is possible, as I have done it before, with an nvidia chipset.

The problem I'm having is that after recognizing the array, the *partitions* are not mounted under /dev/mapper; only isw_blahblah. This prevents me from continuing with the installation; it is also not possible to simply install, ignoring the problem, because the partitioner fails with error code 10. The last time I did this (on the nvidia RAID), I was able to use the partitioner and go along normally. Of course, the last time I did this, the partitions themselves were mounted under /dev/mapper.


Anyone having the same issue?

---

### Post by oliwek on 2008-07-12
hello Herbert, 

it seems to be doable from what I've read in the french ubuntu forum ;
1 way is to install from 7.10 (follow wiki on fakeraid and gutsy) and upgrade to 8.04, it does work on fakeraid with nforce chipsets at least, the other is to follow a procedure explained there by Buissonvert. Not much time to write right now, but I will be back soon.

good luck...


edit : sorry I hadn't noticed this was already an old thread.... for people interested, here's the link from the french ubuntu forum : [http://forum.ubuntu-fr.org/viewtopic.php?pid=1738308#p1738308](http://forum.ubuntu-fr.org/viewtopic.php?pid=1738308#p1738308)

@ secshunayt : the link explains how to solve specificly your issue (mount manually /dev/mapper... and so on)

---

### Post by my_2_cents on 2008-07-13
> **Herbert_Vaucanson said:**
> Yes, I used this form too after carefully reading the man page. Altough dmraid -r worked the first time (it recognized the array).

I am prone to believe it to be a problem of dmraid and its support of ich9r. I tried Gentoo, which worked just fine the first time around, but now I can't see it any raid array with that, too. I am puzzled.

I am trying to install Ubu8.04 onto an Intel ICH6R mobo controller and I found that issuing the command "dmraid -ay" is necessary after installing dmraid. I used the command "dmraid -ay -v" to get more information from that command.

But I am unable to get the Live CD installer to setup on the root partition, even though dmraid seems to be working.

I tried once after adding the "universe" package and the partitions didn't look at all right. Next time I added the "universe" and the "multiverse" packages and dmraid looked better. It saw the partitions I had set up with my boot manager, but the installer still wasn't able to setup on the root partition.

I read in another post an offhand comment that dmraid doesn't work without a boot partition and I'm trying to setup on a root with a swap partition, so I wonder whether we have to have a separate boot partition as well.

I might try one more time with the multiverse package only and see if dmraid will work better, but it's looking like dmraid isn't working on 8.04 or else there is some other tweak that is now required that didn't used to be. I'm also using RAID1 with Win XP already installed and operational.

---

