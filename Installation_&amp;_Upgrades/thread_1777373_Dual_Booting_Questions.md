---
title: "Dual Booting Questions"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by monjebleu on 2011-06-07
Ladies and gentlemen, gastropods and former French emperors, autocratic anthropomorphic simians and genetically engineered sentient root vegetables, I come to you today with a question on setting up a dually booted laptop. The model is the hp dm1z it currently has a copy of Windows 7 and I would like to partition the hard drive so that I may use Ubuntu 11.04 as my main OS. However, I have read that there can be only one Highlan -- err, only 4 partitions on my hard drive, which there already are. These are, according to gparted: sda1-"boot", sda2-main hard drive, sda3-"Recovery", and sda4-"HP Tools" or something like that. I am planning on deleting the HP tools drive, as I have learned elsewhere that it is not absolutely essential and also more recoverable that the recovery drive (seeing as I have no way of making external recovery media currently). Then I would simply shrink sda2 and create a new partition for ubuntu in the empty space. I have been trying to use [this post]("http://ubuntuforums.org/showthread.php?t=1744710") as a guide but it is a tad bit confusing and I just wanted some counsel on my planned course of action. Also, what is the deal on a swap partition? Many thanks.

---

### Post by oldfred on 2011-06-08
Did you click on solved before you got answers? With solved not many will look to help.

Welcome to the forums.

You should be able to easily back up the HP tools data as partition is small.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

