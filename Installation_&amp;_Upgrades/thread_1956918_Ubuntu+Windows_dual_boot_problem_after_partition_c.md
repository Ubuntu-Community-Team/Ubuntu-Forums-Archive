---
title: "Ubuntu+Windows dual boot problem after partition change"
date: 2012-04-11
forum: Installation &amp; Upgrades
---

### Post by kondio on 2012-04-11
Hello,

I have Ubuntu 11.04 and Windows 7 dual boot, although today, after modifying the partition system (I allocated more space to Windows from Ubuntu partition via Gparted program) Windows does not load (asks installation CD in BIOS). Could this be corrected without reinstalling Windows?

Thanks in advance.



[&#1514;&#1493;&#1499;&#1504;&#1514; &#1514;&#1497;&#1493;&#1493;&#1498;]("http://allisrael.co.il/groups/%D7%AA%D7%95%D7%9B%D7%A0%D7%AA-%D7%AA%D7%99%D7%95%D7%95%D7%9A")
[&#1502;&#1514;&#1493;&#1493;&#1499;&#1497;&#1501;]("http://allisrael.co.il")

---

### Post by oldfred on 2012-04-11
Welcome to the forums.

Best to use Windows tools for Windows and Linux tools for Linux. Or use gparted to shrink or move the Linux partition and use Windows to expand its partition.

Normally when Windows changes sizes it updates PBR - partition boot sector and then runs chkdsk on next reboot which may also update some of the size changes in the PBR. So you need to repair PBR with Windows repairCD or USB.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
chkdsk c: /r

If using both Windows & Ubuntu it may be best to have a shared NTFS partition for any data you might want in both. I moved my Firefox & Thunderbird profiles into a shared NTFS partition so I had same email & bookmarks in both systems.

---

