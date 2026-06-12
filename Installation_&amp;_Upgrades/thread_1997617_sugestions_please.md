---
title: "sugestions please"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by twisted hick on 2012-06-05
I had a issue with 11.10 32bit and have been running 12.04 64bit from a usb pen drive.  I now have a 2TB installed waiting to be formated.  sda is my 300gb that has the dual boot with all my files I need to save on it. What I am wanting to do is move the files I wish to save over to the 2TB  then do a new fresh install of 12.04 64 bit on sda no longer having a dual boot system. any ideas on how to do this ?

---

### Post by dino99 on 2012-06-05
you might already have a separate /home partition for all your data & settings, dont you ?

if you want to save the actual installation, watch partimage details inside synaptic

here is my way for installation:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by twisted hick on 2012-06-05
unfortunately I do not have a /home partition but will make sure I do it that way this time around

---

### Post by oldfred on 2012-06-05
If you do an auto install with a 2TB drive Ubuntu will make it gpt which is a newer partitioning scheme over the 30 year old MBR(msdos) scheme. But you do not have to use gpt as it really only is required for drives over 2TB, but is suggested for new drives.

I use gpt with BIOS, and gpt is required with the new UEFI boot. 

You can create partitions in advance with gparted. And create new /home. If you copy your current /home data into the new partition then using manual install, you can choose the new /home partition. It will then update old settings and have all you /home data. During manual install you do select to format / (root) and choose format as ext4, but with /home you DO NOT reformat as it has your data already.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If interested in gpt:
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
But if dual booting with Windows you can only use gpt with UEFI booting. Windows will read gpt drives but not boot from them with BIOS.

---

