---
title: "Partition Lost"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by mayhem_metal on 2007-07-04
Hello ,

I messed up very badly in the process of moving /home to a differnet partition.:(

I have Dual Boot XP & Ubuntu 7. 

Two different HD (First Drive-Master) 

1/. UBUNTU      (partition 1)
2/. Swap           (partition 2)
3/. Ext3 /Home (partition 3)
4/. FAT32          (partition 4)

(Second Drive-Slave) 
1/. WINXP -ntfs      (partition 1)
2/. DATA  - ntfs      (partition 2)
3/. FAT32               (partition 3)
4/. FAT32               (partition 4)

As Ext3 / home was a smaller partition,  I wanted to move / home to  d:/data - ntfs. But what happend is I lost all the data in the data (d: drive)
It now displays ext3 in ubuntu with a ? mark when GPARTED is loaded.

WinXP displays a message do you want to format his drive.

Please ..............................request your help as all data & pictures everything is lost as my backup
was done four  months back.:(:(:(

There must be sopme way in ubuntu to recover all the data.

Finally I move the /home to first drive (Fat32) partition4 as ext3 as it had more space.

Thanks in advance for your help

I had Ubuntu moved into the

---

### Post by coldstatue on 2007-07-04
Did you use the guide at phychocats? if so, it creadted a home_backup folder.

---

### Post by mayhem_metal on 2007-07-04
I dont remember exactly but I did not take a backup of the /Home. I have not lost anything from /home.

What is gone is NTFS(DATA) and all my data that was created using XP

---

### Post by coldstatue on 2007-07-04
Ok, I msunderstood. So the ENTIRE D drive is showing as ext3 with a '?'

That doesn't sound good at all. If someone is able to help, you are in the right place, but formatting the NTFS drive as ext3 would make it very difficult to recover anything. 

Hope a data recovery genius see this thread.

Best of luck!

---

