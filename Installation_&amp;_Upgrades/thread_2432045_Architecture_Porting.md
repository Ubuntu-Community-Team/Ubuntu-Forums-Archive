---
title: "Architecture Porting"
date: 2019-11-26
forum: Installation &amp; Upgrades
---

### Post by icjtqr-gmail on 2019-11-26
Hello everybody!
I have a little-big issue...
I have a PowerPC based Server (Quad Core 790MP @ 2.5 Ghz with 16 GB ECC SDRAM) and it's running Ubuntu 16.04. It has two SATA Hard Drives one for swap and /, /boot partitions (/dev/sda) and the other hard drive (/dev/sdb) has the /home partition for user.
I am planning to change Server (using an x86_64 Quad Core machine @ 2.83 Ghz with 16 GB SDRAM). My concerns are if I can use the /home hard drive simply swapping it to the new platform.
In the x86 server I will install the same Ubuntu version 16.04, so I suppose all my software will run as-is, without any issue...

Is this a viable way to do this platform-architecture side-grade?

Sorry for my english, but I hope you catched all important stuff.

Regards,
Gianluca

---

### Post by TheFu on 2019-11-26
Data files should be ok. Scripts should be ok.  Text system settings should be fine.  May need to recreate the swap, but I honestly don't know.  Things that are "binary" can be impacted, but file systems should be fine.

Compiled files that aren't Java, will be an issue. They will not work.  The solution is to use **apt-mark showmanual** to store a list of manually installed packages and move that list over to the new system.  
To restore new packages on the new box, ```

######[ to restore pkgs ]#######
sudo apt-mark manual $(cat apt-mark.manual)
sudo apt-get -u dselect-upgrade
```

Obviously, make the filename correct.

I wouldn't know you aren't a native English speaker if you didn't say something.

---

