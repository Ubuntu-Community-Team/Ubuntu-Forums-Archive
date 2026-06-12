---
title: "Sharing /Home with Windows?"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-05-29
I am pretty much over Windows, but some of my family are still a little hesitant to give it up until they know all their hardware is compatible. 

The family machine has a virus, and when I visit next week i will be salvaging their system with linux, and I may even be installing linux on it....I dont know how big their hard drive is so it may be a small partition unless I can share with windows....yeah, I know you can read windows files, but that doesnt solve the space issue unless you can post to the C drive or whatever it is in Windows.

Is this possible? Is there a neutral file system that they can share? Fat-32?

Can I have a very very small C drive, a very small /home file, and then a large shared drive? How would this work?

---

### Post by bildr on 2010-05-29
yes the can both read fat32, no you can't use that for the home partition.  permissions problems WILL ensue and you may not even be able to boot X-server.

share a new partition.

---

### Post by Nick_Jinn on 2010-05-29
Thats what I was getting at if you read the last line. Sharing a third partition (other than 2 for the OSs).

But how do I get everything to go there by default? Just do it program by program?

---

### Post by Mark Phelps on 2010-05-31
I don't think that putting your /home directory on an NTFS partition will work. NTFS uses very different permission/security schemes from Linux.  While Linux can use NTFS filesystems, NTFS can't accommodate the needs of Linux.  Don't be surprised if you then get filesystem problems after doing that.

---

### Post by oldfred on 2010-05-31
My original install now about 4 years ago just had root, swap and a shared (then FAT, now NTFS) partition for data I needed/wanted in both.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

I just mounted the shared partition in /home as another folder. I then changed/moved my firefox & thunderbird profiles to the shared partition and modified both windows & Ubuntu's profile.ini to see the new location. I put all photo's in the shared and picasa found them with a few settings to tell it to look there. I then set a .bat file to copy a few files where programs insisted on saving to their own directory, just so I had all my important windows data in the shared & could back it up easily. I never saved anything to My Docs if I could help it even before I had Ubuntu. I still have my shared as I have one or two things I still use XP for, but now most of my data is in Ubuntu and now I have /data ext3 partition for that.

---

### Post by Nick_Jinn on 2010-05-31
> **Nick_Jinn said:**
> Can I have a very very small C drive, a very  small /home file, and then a large shared drive? How would this  work?

The first two posters didnt address this portion of my post. Here I was  not talking about sharing home but how to make a third partition the  default for the download and filing destinations for both OSs.



> **oldfred said:**
> My original install now about 4 years ago just had root, swap and a shared (then FAT, now NTFS) partition for data I needed/wanted in both.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

I just mounted the shared partition in /home as another folder. I then changed/moved my firefox & thunderbird profiles to the shared partition and modified both windows & Ubuntu's profile.ini to see the new location. I put all photo's in the shared and picasa found them with a few settings to tell it to look there. I then set a .bat file to copy a few files where programs insisted on saving to their own directory, just so I had all my important windows data in the shared & could back it up easily. I never saved anything to My Docs if I could help it even before I had Ubuntu. I still have my shared as I have one or two things I still use XP for, but now most of my data is in Ubuntu and now I have /data ext3 partition for that.


Thanks. I will look into that.

---

