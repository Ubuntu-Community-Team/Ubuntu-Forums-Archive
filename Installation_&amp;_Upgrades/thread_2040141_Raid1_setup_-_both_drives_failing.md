---
title: "Raid1 setup - both drives failing"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by c0dem0nk3y on 2012-08-10
I am new to Ubuntu and have been learning about it for the past several months.

Few months ago, I installed Ubuntu Server 12.04 LTS with Raid1 setup by following this guide: 
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

Essentially, I have two 1TB drives in a typical (software) Raid1 setup.

I did install the GUI on top of the server (pardon me for doing this, I am still learning).

Recently, the system threw an error about both disks having issues. SMART reports that one disk is going to fail and should be replaced (sda). The second disk has a few bad sectors (sdb). The raid has not yet degraded.

I want to back up the system and then replace the disks to refrain from a full reinstall, but I am not sure if this will work. I have been searching online and I came across couple of threads pertaining to backing up and replacing drives in Raid1 setup. 

For backup I found this link:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

For replacing the drives I found this link:
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

My action plan is to replace sda first as its going to fail, rebuild the array, then replace sdb next which has a few bad sectors and rebuild again. Before I attempt this, I would like some advice, especially if anyone has come across a similar situation as mine. My other concern, is that since both drives are failing would replacing the drives one-by-one still have bad sectors copied onto the good drive? 

Thanks.

---

### Post by darkod on 2012-08-10
If it's aware about the bad sectors it should avoid writing data to them. And it shouldn't copy them.

Since you can't change both disks at the same time, the only option seems to be what you plan to do.

Replace the disk that's about to fail first, lets it sync fully. Then replace the other disk.

---

