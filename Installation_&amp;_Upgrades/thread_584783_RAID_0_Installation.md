---
title: "RAID 0 Installation"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by mabolo on 2007-10-21
Hi everyone!
I´m a total newbie but would like to give the 7.10 a chance in my windows dominated life..
I have xp and vista installed on a raid 0 (two 74gb raptor sata hdd´s) but with a 40gb partition dedicated for ubuntu.
When i try to install from livecd I can´t see the ntfs partitions neither the free unpartitioned space.
The second problem is that ubuntu doesn´t seem to read the raid as a ~150gb logical disc but as two standalone 74gb hdd´s.

The raid system is an Asus P5W DH Deluxe (Intel Matrix)

Is there an answer or an explanation to this problem?

Thanks in advance!! :)

---

### Post by battyice on 2007-10-21
Your motherboard doesn't have a real raid controller.  You can set linux up in software raid, but I'm not sure if you can retain your ntfs partition.

---

### Post by skattman83 on 2007-10-21
You can setup Ubuntu on fakeraid.  Check out the Ubuntu wiki entry on fakeraid: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto).

---

### Post by mabolo on 2007-10-21
Thanks for the replies!!! :)

I´ll give it a try..
.. but it feels like ubuntu istn´t ready for hardcore windows users to cross over yet. :/
I was hoping for a bit more native support in ubuntu 7.10 since you can hear the big drum and read about the new release almost everywhere..

But i´ll clone my system and give it a shot and pray to the gods that i´ll find the light at the end of the terminal window!!! ;)

---

