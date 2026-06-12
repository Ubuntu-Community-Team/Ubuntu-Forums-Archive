---
title: "trying to recover ubuntu"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by heloOO on 2007-01-08
Hi, i installed fedora 6 and it overwrote w/ a new grub menu. So my grub now has fedora and windows. I want to add ubuntu to this grub. 

I only have 1 hard drive
a) I checked my hard drive using grub> geometry and it gave me sth like this

 partition num 0: File system unknown, partition type 0x7
                     1:      "           ext2fs    , 0x83
                     2:      "           ext2fs    , 0x83
                     4:      "          unknown , 0x8e

b) then i used "find /vmlinuz", i got (hd0,1)

c) i went to grub menu and pressed 'e' and i saw 3 lines 
root(hd0,2)
kernel /vmlinuz blah blah
initrd blah blah

I dunno what the 0x83 which appears both on partition num 1 and 2 mean. Are there steps i can follow to find out more abt my ubuntu partition so that i can add it to grub? thx

---

### Post by tommcd on 2007-01-08
To reinstall grub from the ubuntu live CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
Or from the alternate CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
Or get yourself a super grub disk (great think to have in such a situation):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

