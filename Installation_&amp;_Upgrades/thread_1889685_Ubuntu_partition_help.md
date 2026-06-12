---
title: "Ubuntu partition help"
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by taha1112 on 2011-12-01
Hi,

I was installing Ubuntu, first I tried 11.10 but it didn't let me since i could not find the drive where  I want to install it (ubuntu/gparted is listing it as sdb), if i click on New Partition Table.., it tells me that it's going to delete everything and I dont want that.

I attached a screen shot of what it looks like, 

Any one know how to fix this?

Thanks

EDIT: forgot I was using 11.04 when i took the screenshot, but same thing occured

---

### Post by fantab on 2011-12-01
> **taha1112 said:**
> Hi,

I was installing Ubuntu, first I tried 11.10 but it didn't let me since i could not find the drive where  I want to install it (ubuntu/gparted is listing it as sdb), if i click on New Partition Table.., it tells me that it's going to delete everything and I dont want that.

I attached a screen shot of what it looks like, 

Any one know how to fix this?

Thanks

EDIT: forgot I was using 11.04 when i took the screenshot, but same thing occured


/dev/sdb means there are two hard drives? Are there?

How did you Partitilon your hard disk? what did you use, LiveCD?

---

### Post by critin on 2011-12-01
Assuming you have a second drive you want to install to, click on the drive icon arrows in top right to see the other drives, then choose the one you want.

---

### Post by oldfred on 2011-12-01
Your /dev/mapper/.... says you are using fakeRAID? That complicates things as with any RAID you should not use gparted or the standard installer. I do not know about RAID, so I cannot really help but here are a couple of links.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by taha1112 on 2011-12-02
Yes I do have 2 hard drives but I am not using raid,  since I moved to a much cooler place raid was not needed anymore, so i put it as standard 2 hard drive config.

I used gparted to format 70 gb as ext3 for ubuntu on sdb (second hard drive im presumong?) The problem is ubuntu isnt showing sdb in the installer.

Forgive my spelling mistake since i was using a phone with a very small screen.

And thanks.

---

### Post by fantab on 2011-12-02
> **taha1112 said:**
> Yes I do have 2 hard drives but I am not using raid,  since I moved to a much cooler place raid was not needed anymore, so i put it as standard 2 hard drive config.

I used gparted to format 70 gb as ext3 for ubuntu on sdb (second hard drive im presumong?) The problem is ubuntu isnt showing sdb in the installer.

Forgive my spelling mistake since i was using a phone with a very small screen.

And thanks.

So you want to install Ubuntu on the 70 gb HDD?

Use [Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php") and see what kind of Partition Table the HDD in question is using. My guess is it could be using GPT.... if it is then delete the existing partition and choose **DOS Partition Table** for your HDD. Then create your Partition with ext4 format. 

hope this helps....

---

### Post by oldfred on 2011-12-02
Hard drives have meta data on them from RAID that will interfere with a 'normal' install. If you are not running RAID you need to remove the metadata.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

