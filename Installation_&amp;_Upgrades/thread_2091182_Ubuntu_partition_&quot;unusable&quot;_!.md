---
title: "Ubuntu partition &quot;unusable&quot; ?!"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by tomasrey88 on 2012-12-04
Hi, 

I tried to install dual boot ubuntu latest version LTS 64 bit as dual boot with windows 7 by resizing the windows partition smaller to free up space for the ubuntu partition. After doing so, it is supposed to say "free space 125 GB" so I can click "add" on it to add the freed space as a new ubuntu partition liberated from resizing the windows partition smaller. However, instead of saying "free space 125 GB" on the clickable drop down menu of drives and data formats, it says "**unusable 125 GB**" and when I click "add" it does nothing. Funny thing is at the top of the window, the information bar says; 

sda1(ntfs) 208.7MB, sda2 (ntfs) 494.1GB, **free space 125GB**, sda3 (ntfs), sda4 (fat32). 

What should I do? I am stuck at this stage and cannot do a dual boot ubuntu/windows 7 install. This is a HP Pavilion dv6-7013cl Entertainment PC. It is a laptop I bought from Costco as a refurb. 

Thanks, 
tomarey88.

---

### Post by darkod on 2012-12-04
You already have four primary partitions sda1-sda4. That's the limit for a disk with msdos partition table.

You will need to delete one partition so you can create new ones. If creating the ubuntu partitions manually, do it as logical partitions. In that case you can create more than one. Usually you need a minimum of two, the root and swap partitions.

You can't delete the small partition that says System Reserved, it holds the win7 boot files. One option is the HPTOOLS partition, sda4, or the recovery partition which should be the sda3.

If you open the recovery software in windows usually it gives you option to create a set of recovery DVDs, so after deleting the recovery partition you still have the DVDs if at any time you want the wipe the machine to factory state.

---

### Post by oldfred on 2012-12-04
Pretty much the same as Darko posted. Or backups & delete one partition so free space becomes usable. 

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

    
       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.

---

