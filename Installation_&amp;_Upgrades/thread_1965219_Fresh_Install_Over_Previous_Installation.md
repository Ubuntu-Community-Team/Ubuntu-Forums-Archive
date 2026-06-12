---
title: "Fresh Install Over Previous Installation"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by Victor99 on 2012-04-25
Hi! I'm new to Ubuntu and have just installed 11.10. I see that the new version is coming out, and I'd like to install that. I have a laptop that I dual boot with XP. I don't have a disc for the XP, so I don't want to lose it. Can I do a fresh install of 12.04 that will delete the old version? I know I could delete the old system by using XP or Partition Magic, but then I wouldn't be able to boot to XP, since grub would be gone. With the 12.04 installation disc, can I delete the old version and install 12.04 without any problems? If so, how do I do this? Any and all responses will be greatly appreciated. Thanks.

---

### Post by Curtis6767 on 2012-04-25
You could just upgrade. That is one option. It takes quite a while.

On the 26th the 12.04 LTS final version may show up in the Update Manager as an available update. If not the 26th, then shortly thereafter. At least that is my understanding.

---

### Post by darkod on 2012-04-25
If you want to install onto the existing partitions you will have to use the manual install and tell ubuntu to overwrite those partitions. It will not do it by itself.

You will have to select the Something Else option, click the root linux partition and click the Change button. Then change the Do Not Use into ext4, tick the format box, and select the mount point as /.

The swap partition should be reused automatically.

That will install using the same partition. Just make sure you select the ubuntu partition and not the XP partition.

---

### Post by oldfred on 2012-04-25
Welcome to the forums. 

The reinstall will overwrite all of Ubuntu unless you have a separate /home partition. So if you have made a lot of settings and have some data in /home you should back that up. If you have installed a lot of applications you can export a list to use to reinstall.

You also should backup XP as any major system change can cause issues.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

