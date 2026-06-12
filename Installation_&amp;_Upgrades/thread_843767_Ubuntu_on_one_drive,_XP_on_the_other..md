---
title: "Ubuntu on one drive, XP on the other."
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by voltare on 2008-06-28
I plan on having ubuntu and windows xp on my comp.... i have xp now. I'm going to install another HD....I want to have an dual boot system, set up like this: I want to boot into ubuntu on the second drive; and have my son as an account for the XP drive.How would I go about doing this?

---

### Post by avtolle on 2008-06-28
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs) will help you in installing Ubuntu to the second HDD.

---

### Post by voltare on 2008-06-28
So....I can d/l it on this drive and set it up on the other one? then allow for 2 accounts with a different hard drive for each account??( sorry for the seemingly dumb questions....but I'm not going to Vista. Period.)And thanks for your reply!

---

### Post by Sidewinder1 on 2008-06-29
In Nov'07 I did exactly what you want to do for exactly the same reason (Vista, NOT) and have been nothing less that thrilled. There is a bit of a learning curve (obtained almost exclusively from this fantastic site).
Essentially what I did was: downloaded the correct ubuntu (32 bit, 64 bit, desktop, etc or whatever matches your system) to my C:\ drive; verified the file was absolutely correct using MD5SUM; then burned the iso image to cd rom to make a 'live cd', (it's a good idea to run ubuntu from the live cd to resolve any driver / configuration issues). That being done I then installed, from the live cd to what then was my F:\ (all ntfs / fat32 data will be lost and unrecoverable from F when you repartition it to "ext3", "swap", and "extended" linux partitions). What I ended up with is a dual boot system that prompts each time for either 'ubuntu generic' (first, default, choice) or 'windows XP'.
Just make sure that you back up all that you don't want to loose. 
By the way----> WELCOME TO UBUNTU and this most valued forum.

---

### Post by forger on 2008-06-29
> **voltare said:**
> So....I can d/l it on this drive and set it up on the other one? then allow for 2 accounts with a different hard drive for each account??( sorry for the seemingly dumb questions....but I'm not going to Vista. Period.)And thanks for your reply!

You mean set your son's home directory to the XP drive?

Not sure if it's possible, but there is an option with the **adduser** command:
```
adduser --home '/media/mount/xpdrive/linuxhome/son/'
```
(The above is just an example, you'll have to point to the mount point of your XP drive.)

Your XP drive is NTFS? I'm not sure if it's a good idea to have the home directory in a windows partition

---

