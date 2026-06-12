---
title: "After true install on HP Pavilion, Ubuntu 11.4 won't boot"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by freee on 2011-05-02
I completely deleted NTFS as having a boring windows doesn't make any sense today, installed it with ext4:

/boot = 200MB
/swap = 1GB 
/ = space left 

After successful install, the BIOS screen with HP logo remains stuck, it won't boot anything in another words. I can't get the boot loader, nothing as if it awkwardly trying to boot from external data drive. Did my hard drive go poof? or did I miss something during install? How can I get my hd to read? Thanks for taking time to help.

---

### Post by dino99 on 2011-05-02
make a standard config:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

note: i'm not sure but HP have probably set a hidden partition (tatooed) that is disturbing installation. The solution is to format the hdd with tool available with western digital or seagate. Then redo it as said into the link above.

---

### Post by freee on 2011-05-04
I bow to you!

Fixed everything with partedmagic and got fired it up. What a nice tool!

---

