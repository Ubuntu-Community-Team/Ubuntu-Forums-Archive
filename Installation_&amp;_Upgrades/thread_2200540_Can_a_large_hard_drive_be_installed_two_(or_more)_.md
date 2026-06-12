---
title: "Can a large hard drive be installed two (or more) Ubuntu OS?"
date: 2014-01-19
forum: Installation &amp; Upgrades
---

### Post by ruwan2 on 2014-01-19
Hi,
Because I often reinstall Ubuntu when I cannot recover some problems, I would like to have a hard drive installed more Linux copies. That is, I can select one Linux (same Ubuntu) boot. When one OS fails with some software installation, I can reinstall that one. The main purpose of my intention is that there are many combinations when I have problems, I want to test these software with different Ubuntu OS copies. To repair a problem Ubuntu sometimes needs too much time for me.




Thanks,

---

### Post by ersatzsplatt on 2014-01-19
Yes, you can install more than one copy of Linux on a hard drive.  In short, you make your second install on a different partition of the drive.  My recollection is that ubuntu asks you if you want to install over an existing install or install next to it.  Then you will end up with more than one install on the same system, but the default may not give you grub menu options for each install.  If you find yourself in this situation, then just run:
sudo update-grub
then
 sudo grub-install /dev/sda

... assuming you have a single drive you are using.

You can do the same with a second drive attached and use multiple partitions on the attached drive.

---

### Post by Bashing-om on 2014-01-19
ruwan2; Hi !

Sure ! You can install multiple operating systems on your hard disk.
Example: I am presently triple booting:
```

sysop@1310mini:~$ sudo blkid
/dev/sda1: LABEL="1310mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1310mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1310mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
sysop@1310mini:~$ 

```

If you are going to do a lot of "testing" perhaps you should consider VM (virtual machines) ?

When it gets serious ->
[INDENT][INDENT][INDENT]have a backup 
[/INDENT][/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-01-19
You could also create a home and/or data partition.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=home+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=home+partition&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2014-01-21
I have two installs on my SSD, and many installs on my larger rotating drive. It is to the point of keeping track is difficult without bootinfoscript and turning off os-prober as it finds too many systems to boot.

Several years ago, I bought a new 640GB drive after having only 160GB drive, so it seemed huge. I created two 100GB data partitions and left rest unallocated. Then I started adding 25GB partitions for a new install, since space was available, I just kept adding. 
I think I finally have filled drive and really need to houseclean old installs. A test install only needs to be 10GB. My working install uses about 11Gb but default install without much change or added software is much smaller.

---

