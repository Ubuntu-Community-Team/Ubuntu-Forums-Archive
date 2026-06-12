---
title: "dual boot win 7 and ubuntu"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by donquiscot on 2011-09-08
I have 2 500 gb HDDs on raid 0 for a total of 1Tb with winows 7 ultimate 64 bit and I added a 30 Gb SSD and planning to install Ubuntu on the ssd , I have 2 issues, the major one is that everytime I install Ubuntu on the SSD using "install Ubuntu alndside windows 7" option the system will only boot to the ssd Ubuntu everytime with no luck to get windows running again, I know that windows is there on the HDD but I cannot get to it. the second problem is that before installing ubuntu , windows does not list the ssd or cannot find it. it only shows up on the start up list of drives as a non raid drive but windows 7 cannotfind it or format it or anything

---

### Post by oldfred on 2011-09-08
I do not know RAID but you may have to install extra drivers for Ubuntu to see data inside the RAID.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm

Windows will not see any Linux partitions, so once you format the SSD as Linux, Windows will not see it anymore.

Do you have other NTFS partitions for data? You should only put data in a shared NTFS that you may want for both systems, and not write into your Win7 system partition.

---

