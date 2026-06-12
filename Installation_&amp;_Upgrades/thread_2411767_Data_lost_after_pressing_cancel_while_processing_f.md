---
title: "Data lost after pressing cancel while processing file sistem change of partition"
date: 2019-02-03
forum: Installation &amp; Upgrades
---

### Post by tritures on 2019-02-03
Guys I need help..
I wanted to replace Windows 7 with Ubuntu so I made USB flash bootable and started installation. But after I done partitioning I have changed NTFS partition (partition which had data that I wanted to keep) to EXT3 without checking checkbox for formatting but instead to wait that process to end I pressed cancel and then quit the installation process. After thet I thought that partition will be like they were before installation but it didn't happened. Because I didn't know what to do (I tried to find similar situation on the internet unsuccessful) I have changed EXT3 to EXT4 (partition which was NTFS before; this time partition had 13000 MB instead of 100000+ MB) and put it as /home partition. Then I installed Ubuntu hoping that those 13GB are just visible to Ubuntu and rest isn't, so I have to find some recovery tool to get it but I don't think that works like that so I came here to ask if there is any way how I can get my files back. I really need to get it back because there was, expect important files like photos, videos and school lessons, my graduation work which was almost done.. :/
Now, when it is installed, I can't see anything from that partition. There is just "Computer" and home in root is empty (has just default folders and files).
I know that I made a lot of mistakes..
Thank you in advance

Sorry if this is duplicate, I couldn't find something similar to this.

---

### Post by CatKiller on 2019-02-03
> **tritures said:**
> But after I done partitioning I have changed NTFS partition (partition which had data that I wanted to keep) to EXT3 without checking checkbox for formatting

There is no way to turn an NTFS partition into a different filesystem that preserves the files that are on there.

Those files are gone.

If you stop using that drive for anything you may be able to retrieve some of the data from those files using file recovery software, although that only has limited success even under ideal conditions. These are not ideal conditions, since you've formatted it - twice - and used the drive for something else in the meantime.

People have reported some success using photorec, although I've never used it myself.

The most important thing is that you stop using that drive until you've recovered what you can.

---

### Post by tritures on 2019-02-04
I recovered with Photorec almost everything. Visual Studio files can't be recovered, at least not with this tool. Some data was corrupted, I guess thst those files were changed before I pressed cancel but after resorting and deleting unnecessary data like files of some programs, it was shrinked from ~120gb to 83gb.
Anyway, thank you for replaying.

---

