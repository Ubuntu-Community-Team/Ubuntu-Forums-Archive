---
title: "dual boot installation"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by bgen90 on 2011-07-16
I am new to linux n want to use it for web development. I just downloaded the ubuntu 11.04 from net and using usbinstaller, i made it bootable with my pen drive. I already have Windows XP and Windows 7(dual boot) in my system....Windows 7 is in my E drive...I want to replace it with ubuntu....Can anyone give me step by step instruction to install ubuntu in my E drive(I have four partitions C,D,E,F   E:34GB  Total HD:160GB HP notebook)

---

### Post by raja.genupula on 2011-07-17
just remember that drive name and size .

in the bios options change the first boot as Removable disk . 

you know what have to do upto partitions . when you came for drive selection just select that partition at which you wanna install , at the options click at delete  to delete that partition . after that , select that  free space and make a partition with ext4 format and "/" mount point . keep a 2-3 gb free for swap partition , its will be in that list where you have selected ext4 . then click next . ubuntu have grub loader for dual installation . so you can able to do dual boot .if you have any doubt clear them all before installation to prevent data loses .

---

### Post by bgen90 on 2011-07-17
I had done what u have said...i deleted e drive....created 4gb for swap area....installed ubuntu in free space. Everything is fine .....BUT when i went back to xp i could not see F drive...When i went inside ubuntu i can see f drive(mount n see) there....how to bring the view in xp? plz help

---

### Post by bgen90 on 2011-07-19
plz someone help me

---

### Post by alphaamanitin on 2011-07-19
XP will never see a drive that is in a *nix format.  Well, not entirely true, but the windows drivers for the ext hard drive formats are not reliable and I don't think you should try them.  Anyway, windows just thinks the drive is completely empty (not even formatted) and so it won't show it in my computer and the like.  You can find it through other means though, but there is no point as windows can't use it.  If you need go-between storage you need to make a new FAT32 partition that both Windows and Ubuntu can access.  But beware, you cannot store a file larger than 4gb on FAT32.  You could use NTFS but Ubuntu sometimes messes up NTFS formatted drives, which is why it is not recommended you access your windows partitions from ubuntu.  Though I do this all the time and have never had an issue, but that does not mean that I will not have an issue in the future.

AlphaA

---

