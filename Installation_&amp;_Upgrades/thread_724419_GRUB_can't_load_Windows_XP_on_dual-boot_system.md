---
title: "GRUB can't load Windows XP on dual-boot system"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by Dylock3 on 2008-03-14
Problem: I can't get Windows XP Pro to load on my dual-boot system.

System: Dell Inspiron e1705, exact specs [here]("http://www.notebookreview.com/default.asp?newsID=2776"):

History of problem:
1-I used a third-party tool to resize the Windows partition so I could install uBuntu.
2-When I tried booting XP, it said, "Loading PBR 2...done."  Then it halts.  After some research I found out that PBR relates to Dell's intermediary bootloader. Dell PBR found my partition size had changed so it didn't boot.
3-No problem, I'll just install uBuntu, overwrite the MBR, and boot WinXP with GRUB.  However on installation I get the error message, "*File system doesn't have expected sizes for Windows to like it.  Cluster size is 2k (1k expected;  number of clusters is 24026 (47959 expected;  size of FATs is 94 sectors (188 expected).*"
4-I've researched that error and found that restoring my NTLDR with a fixmbr from Windows Repair might fix it.  This would kill GRUB though, maybe I could get Windows to boot uBuntu.  However I have an image CD and not a WinXP install CD.  I don't know if it would work without that Dell PBR either.
5-My next option (and perhaps final) is to find out how to get GRUB (or an alternative) to boot Windows.  Perhaps I'll have to resize the clusters to standards specs?  I have no idea how to do either one.  I've tried the first 5 suggested threads and even tried searching Google to no avail.

sudo fdisk -l says:
> Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        5743    46082452+   7  HPFS/NTFS
/dev/sda3            5744        7050    10498477+  83  Linux
/dev/sda4            7051        7113      506047+  82  Linux swap / Solaris

/boot/grub/menu.lst says:
> title Microsoft WinXP Pro
root (hd0,1)
savedefault
makeactive
chainloader +1
boot

title Microsoft WinXP Pro force 
root (hd0,1)
makeactive
chainloader --force +1
boot

Can you tell I've been experimenting?  Don't know if the below would help from the forums, I highly doubt it
rootnoverify
Windows boot editor? [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

Misc. facts:
-uBuntu can't read my NTFS partition to access files, but it recognizes it.
-Once after editing /boot/grub/menu.lst I restarted my computer and it said "NTLDR missing" without booting GRUB.

---

### Post by radioraheem on 2008-03-14
> I've researched that error and found that restoring my NTLDR with a fixmbr from Windows Repair might fix it.  This would kill GRUB though, maybe I could get Windows to boot uBuntu.

Why the concern about it wiping out grub?  If it's a fresh ubuntu install (that you ultimately don't care about right now if it's just the OS) then try that fix, see if Windows can boot, and if so then try the ubuntu install again.  If the fix doesn't work and windows is still not working then maybe it's time to use a ubuntu live cd to save the data you care about and reinstall both OS's from scratch.

Good luck with whichever path you choose :)

---

### Post by Dylock3 on 2008-03-14
> **radioraheem said:**
> Why the concern about it wiping out grub? ...try that fix, see if Windows can boot, and if so then try the ubuntu install again.  If the fix doesn't work and windows is still not working then maybe it's time to use a ubuntu live cd to save the data you care about and reinstall both OS's from scratch.

Can't reinstall XP, I wiped out the image partition.  I made a backup of my files anyways (good thing because uBuntu can't see them due to the cluster issue).  If I can't get it working (I'm not going to back off this challenge now) then I'll just completely wipe out WinXP. Besides, Wine isn't working as well as I'd like.  Perhaps Cedega?  But I digress....

I did find some Windows LiveCDs, hopefully they can restore my WinXP bootloader and/or change the cluster sizes back.

FIrst I'm going to try the[ WinLiveCD BartPE]("http://www.nu2.nu/pebuilder/") to fix my bootloader.  If that doesn't work, I'm going to try[ WinBuilder.]("http://www.winbuilder.net/news.php")

After I've successfully booted into Windows, I'll replace GRUB [with this]("http://ubuntuforums.org/showthread.php?t=224351").  Unless I can get NTLDR to boot Linux.

Hopefully that will fix it or I'll need to find a cluster resizer program.  Any advice is MOST welcome.

---

### Post by zvacet on 2008-03-15
You can try [this.](http://neosmart.net/dl.php?id=1)

---

### Post by sandysandy on 2008-03-16
>  Unless I can get NTLDR to boot Linux. 

 have a look at this link 

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

regards

---

