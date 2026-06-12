---
title: "Unable to install Ubuntu, manual partition option is empty"
date: 2019-12-25
forum: Installation &amp; Upgrades
---

### Post by subhechhu on 2019-12-25
I am trying to install Ubuntu to my Dell Inspiron 5490.
I want to erase the current windows os and replace it with Ubuntu18.x LTS
But it doesn't provide me with the option to Clear the drive & install Ubuntu
It doesn't even give me option for manual partition.

What am I doing wrong?

---

### Post by CatKiller on 2019-12-25
If you've got windows on there already you'll need to turn off Fast Startup before the partitions will show up. Windows doesn't shut down properly, it just hibernates, to mask its boot up time, and that leaves its partitions in a dirty state that can't be edited.

---

### Post by CelticWarrior on 2019-12-25
I suggest turning off the Fart Startup feature in Windows anyway but it may not solve your issue.

Your issue is more likely related to an incompatible "SATA mode" in UEFI: Intel RST and RAID modes aren't supported. You need to change to AHCI but be aware you need to install AHCI support in Windows before changing or Windows won't boot with AHCI.

---

### Post by oldfred on 2019-12-25
If erasing Windows, I would still back it up.
Many users post back later, that they want to reinstall Widnows as there is one game or application they need that only runs in Windows. Or they want to sell system & it has to have Windows.

Most of the vendors that have restore options, are using a partition on hard drive. You want a separate backup, just in case drive fails.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp) 
    
       Dell Latitude 5490 M.2 PCIe SSD
[https://ubuntuforums.org/showthread.php?t=2405822](https://ubuntuforums.org/showthread.php?t=2405822)

---

### Post by subhechhu on 2020-01-11
Thank you for the links.
It was really helpful :)

---

### Post by subhechhu on 2020-01-11
RAID mode was the problem.
Ubuntu installed successfully.
Thanks

---

