---
title: "Install Edgy on AHCI SATA drive"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by kris42 on 2006-10-30
Hi,

I've got a weird installation problem with Edgy. But first things first:
I have an Asus P5B Deluxe motherboard with an Intel P965 chipset and two identical 250GB SATA drives wich are set to AHCI mode in BIOS. One drive has two partitions (NTFS and ext3), the second drive is formatted with ext3 only.
I'd like to install Edgy on the first drive's ext3 partition.
But when setup starts the partitioner, it shows only one drive, which is the one that is formatted as ext3 exclusively, so I can't install to the drive that I want. There is also only one disk drive in /dev (-> /dev/hda)
Now the question is: Why does Edgy detect only one of my two drives? If no drive were detected at all, the logical explanation would be that AHCI is not supported or something like that, but it does detect one of the drives, so the whole thing is a bit weird.

Would be great if someone could shed some light on this matter!

Regards,
kris

---

### Post by _Eleazar_ on 2006-10-30
You need to use DMRAID it sounds like. Though if you are a new user to Linux I wouldn't suggest it. The documentation is terrible for a new user and only is really good for people who already have some sort of knowledge about Linux. Here is a howto for Dapper Drake 6.06, with some 6.10 tips.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

You will most likely need to get the latest version of DMRAID from here
[http://librarian.launchpad.net/4934470/dmraid_0.9.9%2B1.0.0.rc13.source.tgz](http://librarian.launchpad.net/4934470/dmraid_0.9.9%2B1.0.0.rc13.source.tgz)

You are going to have to build it yourself. To build it you are going to have to go to the directory you extracted the dmraid folder. For me it was the Desktop. You first have to download all the dependency libraries from the Synaptic Package Manager, which are:

Build-essential
libdevmapper-dev
libklibc-dev
libselinux1-dev
zlib1g-dev
automake (download the -dev too if it exists, it may not)
autoconf (download the -dev too if it exists, it may not)

So I:
cd ~/Desktop
cd /dmraid
cd /1.0.0.rc13

I then,

./configure
make
sudo make install

That should get it installed for you. Then from there follow the documentation. I would like to reiterate that I would not recommend this for someone who is still rather new to Linux. The guide just leaves some things out that really should be told to a new user. For instance, how to find out the end sector location of 60GB on your hard drive. This is necessary if you are going to be using ntfsresize for your NTFS partition. There are other things muddled throughout the guide it just assumes you know, that a new user wouldn't know. Make sure you read it first if your going to give it a go.

EDIT:
Some people say they have had more success with this guide:
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

Though I know for sure Gparted will not pick up your DMRAID drives, which is what this guide uses. This is also a guide for 6.06 so just like the other guide, not everything will apply and things could be different.

---

### Post by kris42 on 2006-10-30
Hm thank you. But these Howtos both are about a RAID setup. But I actually don't have my SATA controller in RAID mode, but AHCI. Since AHCI is a very new technology, I should have expected problems. I guess the most obvious solution would be to set it to IDE mode, sacrificing the performance advantages of AHCI. The problem with that is that I already have a Windows XP installation which I don't want to break.

---

### Post by jhnphm on 2006-11-01
Passing irqpoll as a boot parameter works. Be aware that I am currently experiencing random lockups after a few hours though.

---

### Post by kris42 on 2006-11-05
Hi,

I switched to IDE mode now, fortunately it caused no problems with my Windows installation. Looks like I've got to wait until Linux hackers catch up with bleeding edge hardware once again. In this case, I'd consider it a minor annoyance, though :-)
What really bugs me now is a completely different problem that makes my installation of Edgy practically unusable:

[http://www.ubuntuforums.org/showthread.php?t=291338](http://www.ubuntuforums.org/showthread.php?t=291338)

Regards,
Chris

---

