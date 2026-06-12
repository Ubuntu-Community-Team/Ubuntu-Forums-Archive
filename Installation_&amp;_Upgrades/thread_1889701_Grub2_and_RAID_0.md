---
title: "Grub2 and RAID 0?"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by rollin77 on 2011-12-01
Hi all I was just reading through some threads before I install Ubuntu 11.10 on my home PC as a dual boot with Windows 7, and found a few threads mentioned something about Grub2 not working with hard drives setup in a RAID 0 array.

I'm a little confused, but why would RAID 0 matter?  Since RAID 0 is setup on my motherboard, currently Windows 7 has no clue it's sitting on 2 hard drives in a RAID 0 configuration, it only sees one hard drive from its perspective.  So why would this be an issue with installing Ubuntu as a 2nd OS?

I just wanted some clarification before I go forward with the install later on tonight, and if I need the alternative CD mentioned in other posts I'll want to make sure to do that, though I'm still confused why this is even an issue.

Thanks in advance for any help!

---

### Post by darkod on 2011-12-02
I have never used the bios fakeraid personally but I think most threads I have seen are because people keep using the desktop image and not the alternate. The documentation clearly says that grub installation on fakeraid might fail if using the desktop image.

I think with the alternate you should be OK.

---

### Post by rollin77 on 2011-12-02
Just to be clear, RAID 0 isn't done through the, (Asus P8P67 DELUXE), motherboard BIOS but through the on-board Marvell controller.  While this certainly isn't going to offer the performance of a high end server class RAID controller, I don't see why it would be "fake".  

I don't see why/how Ubuntu would even know it's installing itself onto 2 hard drives because it should see it as just one, which is just what happened when I installed Windows 7.  It saw one 1Tb hard drive instead of two 500Gb hard drives.

Perhaps people running into problems aren't really running a RAID setup because I don't understand why my setup should cause any issues, but just wanna be sure before I start the install.

---

### Post by darkod on 2011-12-02
I might not be in touch with all the details, but the term fake would still apply I guess. The thing is that dedicated raid cards have their own CPU and even memory, and do the whole job themselves.
Having just a chip on the board, regardless whether you enter into bios or by pressing some key, is still using your cpu and ram, hence the term fake.

Yes, ubuntu will see it as single device but using the desktop cd can make grub installation fail. Don't ask me why, the developers know much more than me for sure. It might be how the desktop cd and the alternate cd are "looking" at the raid and what type of drivers they have to support it.

---

### Post by rollin77 on 2011-12-02
I'm not trying to be an jerk, but I'm looking for answers from people that have more knowledge regarding this potential issue.  

Does anybody else know about this issue, or have heard about it?

---

### Post by oldfred on 2011-12-03
I do not believe in RAID for most desktops. If you want speed use a SSD, and if you want redundant data do more frequent backups.

More info on RAID here:
Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)
Software RAID w/mdadm driver
[https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)
[https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html)

---

### Post by rollin77 on 2011-12-03
I'm not changing my hardware configuration, and I'm certainly not buying an SSD.  All hardware is remaining the same.  I already have a 60Gb partition set aside for Ubuntu on the 2 drives in RAID 0, so what exactly do I need to do differently so it installs fine?  Do I need this alternate CD I read about, and what is different about this alternate CD anyway?  The version I plan to install is Ubuntu 11.10

---

### Post by darkod on 2011-12-03
I know you are not trying to be a jerk, just to get information in advance and I support your view. I'm not trying to be a jerk either.

But you seem to keep asking for a solution for a problem that doesn't even exist since you haven't started the installation yet.

If you are looking for a letter by letter specification what is different between desktop image and alternate image, only the developers would know that and I doubt they will visit here and answer.

What we as "normal" users can see, is here (for the latest version): [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

Read towards the beginning, in the section Alternate CD:
- LVM and/or RAID partitioning

That's enough for me. As for you, it's up to you. The images for download are on that page towards the bottom. Just select which one you want, being it desktop/alternate/server and 32/64bit.

When you say 60GB partition, I hope you mean unpartitioned space because any ntfs partition created in windows is worthless for linux. However, you can always delete it during the install partitioning, no need to specifically delete it from windows.

You will want to use the Manual partitioning option to have more control. I always recommend it.
You probably know you need to create as minimum bigger / and smaller swap partitions. A separate /home is up to you.

You already have a number of links posted earlier by another poster too.

---

### Post by megahertz on 2011-12-03
I have just made a multi boot system (Win7 64+WinXP 64+ Ubuntu64) on a RAID 0 array.
As you already have Windows installed, it will be a little different, but my post could help.
Se my post [http://ubuntuforums.org/showthread.php?t=1886279&highlight=raid](http://ubuntuforums.org/showthread.php?t=1886279&highlight=raid)

---

### Post by rollin77 on 2011-12-03
> **darkod said:**
> But you seem to keep asking for a solution for a problem that doesn't even exist since you haven't started the installation yet.

The problem does exist but I'm not going to wait until it exists on my system, that would be stupid. The point is to avoid having any problems.  I don't want to FUBAR my primary PC.

> **darkod said:**
> If you are looking for a letter by letter specification what is different between desktop image and alternate image, only the developers would know that and I doubt they will visit here and answer.

I never asked for a specific "letter by letter" differentiation between the install discs, I just need a general understanding as to what about them is different, and if/why I might need to use the alternate disc instead of the standard. If you don't know the differences don't worry about it, I'm sure somebody here does.


So just to recap, my system is a Windows 7 PC currently running on two 500Gb Sata drives in RAID 0 setup through the on-board Marvel controller of my Asus P8P67 Delux mobo. I already have a 60Gb partition ready for the Ubuntu install, but my only concern is with an issue I read about that the grub2 bootloader might have.

Does anybody have more info on this possible issue and/or why I might need the alternate disc? What is different about it so I know why I'd need it instead of the standard install disc?

---

### Post by rollin77 on 2011-12-03
> **megahertz said:**
> I have just made a multi boot system (Win7 64+WinXP 64+ Ubuntu64) on a RAID 0 array.
As you already have Windows installed, it will be a little different, but my post could help.
Se my post [http://ubuntuforums.org/showthread.php?t=1886279&highlight=raid](http://ubuntuforums.org/showthread.php?t=1886279&highlight=raid)
Thanks, this looks like exactly what I need to read.  I was about to just sa F-it and start the install, but I might wait until I have more time for troubleshooting should things go haywire.

---

### Post by megahertz on 2011-12-14
To "see" a fake raid you must load the appropriate drive. 
The problem is that the Ubuntu desktop installation software comes with and loads the Raid manager software (dmraid), but it doesn't install it on target drive. The second main problem is that you're not able to install the boot loader (Grub), maybe because dmraid hasn't bean installed.
You have use ubuntu-11.10-alternate.

---

