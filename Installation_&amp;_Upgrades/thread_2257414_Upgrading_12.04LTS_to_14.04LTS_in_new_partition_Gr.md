---
title: "Upgrading 12.04LTS to 14.04LTS in new partition Grub and partitions messed up."
date: 2014-12-19
forum: Installation &amp; Upgrades
---

### Post by buck2 on 2014-12-19
I have an internal 500GB HDD, and external 1.5TB HDD (USB) and an internal CD/DVDRW.

What I want to do is create a second copy of my current OS (12.04LTS) on a partition on the external HDD.  Upgrade that drive and test 14.04LTS before actually upgrading my internal drive. 

Added external partition 475GB to external drive.  Installed 12.04 to new partition.
Clonezilla'd to that same partition.
Grub can't find it. :(

Cloned  whole drive from internal to external: No mater which drive I use BIOS  to boot from, it reverts to the internal drive copy of 12.04 (my  original.)

Partitioned external drive to 60GB /boot, 32GB swap, and 500gb ext4.  
Installed 14.04 to 500gb partition.  

Grub lets me boot to 14.04 first, or I can select my old 12.04 on my internal.

Added 475GB partition to external drive and installed 12.04.
Clonezilla'd my internal partition to overwrite the new OS.

Grub lets me boot to the external 14 or my internal 12 not the external 12.

My next idea is to erase the 1.5TB and clone my internal drive to it, do the update and if it fails, restore with the clone.

Before doing so, I disconnected the external drive to test boot. UGH!  Grub crashes!

I turned off swap and unmounted all the drives, turned off computer, took out the hdd and rebooted-Grub crashes.

I had to reconnect the external drive to boot, but after unmounting all partitions, I have removed it and can still operate without error.  (I am currently working that way now.) But, I'll have to reconnect it to boot again.

I guess I could make a clone of the internal drive to an image on the external, but I seem to be stuck with the partitions on the external drive, which was never my goal.  I would really like to wipe the external clean and operate without it unless I choose to use it.

I eventually need to repartition my internal drive, but I guess right now, I need to get back to using it without needing the external drive.

Any suggestions?

---

### Post by Dennis N on 2014-12-19
> What I want to do is create a second copy of my current OS (12.04LTS) on a partition on the external HDD. Upgrade that drive and test 14.04LTS before actually upgrading my internal drive. 

I really don't see the need of the copy. Sounds like you plan to then upgrade the copy - Why not just do a new install of 14.04 on the external drive and test that? Or if there is room, do a new install of 14.04 on the internal drive on a new, separate partition?

---

### Post by buck2 on 2014-12-19
My goal is to protect my original workstation while testing the copy to make sure all my software works, etc.

I really don't want to reinstall everything and lose all my saved emails, etc.

---

### Post by Dennis N on 2014-12-19
If you make a new install of 14.04 on a new partition, that would not affect the current 12.04 installation or data - I don't see how it would. It's basically making a dual boot setup.

---

### Post by Bashing-om on 2014-12-19
buck2; Hello;

Food for thought:
My system quad booting:
> 
sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
sysop@1404mini:~$


[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Dennis N on 2014-12-19
A final thought - You can test all the new 14.04 software from a new install, even using your previous files and documents on 12.04, since you can access your 12.04 documents and files from 14.04. That should give you a pretty good idea of how everything will work.

I think you are intent on upgrading rather than a new install. I don't fully trust the upgrade process - I now do a new install on a new partition and I keep a separate data partition for created files and documents, so that is also immediately accessible by a newly installed OS. A pretty painless transition.

Your decision in the end.

---

### Post by oldfred on 2014-12-19
You cannot clone your current install and install it on the same system as your current install. It works for restoring to same system or even to another totally different system.
The issue is that you cannot have duplicate UUIDs and if you try to boot a cloned system it may write to one or the other and then both get damaged as each has part of the changes.

Better to have your good backups and do a new install to external drive. Copy /home, perhaps some settings from /etc and reinstall the list of programs you have installed. Then you have new system with all your old settings & programs.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by buck2 on 2014-12-19
OldFred: Thank you, short sweet and to the point so I understand.
Bashing-OM: Thank you, I see you have multiple installations, but I am not sure they are copies of the same partition.
Dennis-N: Thank you for trying. I have installed and tested the 14 successfully, but I wanted to know I could upgrade without crashing my system, and without having to reinstall every piece of software and settings in it.

---

### Post by buck2 on 2014-12-19
Now that my system is messed up to the point of requiring the external drive just to boot.  I think I will install 12 and backup the internal and restore it to the 12 on the external.  That will give me the working backup on the external to test upgrading. 

If the upgrade works, I should be able to upgrade the internal drive safely and grub will default to the internal instead of the external.

Well, that may take a while, but that  is what I have to work with.  I am not very knowledgeable about editing grub, etc.

---

### Post by fantab on 2014-12-20
> **buck2 said:**
> My goal is to protect my original workstation while testing the copy to make sure all my software works, etc.

I really don't want to reinstall everything and lose all my saved emails, etc.

If I were you, instead of 'cloning', I would create a new partition on the on the internal HDD of about 20-25gb and install 14.04 to it. This way I will have both 12.04 and 14.04. I would keep 12.04 untill it reaches its 'end of life'. I would go actually a step further and create one more 20-25gb partition and install 14.10 to it.

I would not use a separate /home partiiton. Instead use a simple ext4 partition to store my personal data.

---

### Post by grahammechanical on 2014-12-20
I think that you are unaware of the way Grub does its work.

Every time we install a version of Ubuntu the new install will create a Grub boot menu and put that menu in charge of the boot menu that we see. And when we boot Grub will look for configuration files in /boot/grub/grub.cfg on the new installation.

 If the 12.04 (internal) was not put back in charge of the boot menu and if its Grub configuration files were not updated to detect newer installations then cloning that installation would have an out of date boot menu.

> [COLOR=#000000]Grub lets me boot to 14.04 first, or I can select my old 12.04 on my internal.[/COLOR]

That is because the 14.04 Grub has control of booting and it detects the 12.04 (internal). By the way, Grub is installed by default to sda unless we select otherwise.

> [COLOR=#000000]Added 475GB partition to external drive and installed 12.04.[/COLOR]

That 12.04 (external) would have taken over from 14.04 (External) in controlling the boot menu.

> [COLOR=#000000]Before doing so, I disconnected the external drive to test boot. UGH! Grub crashes![/COLOR]

Of course it would. In creating the boot menu Grub looks to configuration files on the external disc, which has been disconnected. Grub would have been looking for /boot/grub/grub.cfg in the new 12.04 (external) Or /boot/grub/grub.cfg in the 14.04 (external)

> [COLOR=#000000]I had to reconnect the external drive to boot, but after unmounting all partitions, I have removed it and can still operate without error. (I am currently working that way now.) But, I'll have to reconnect it to boot again.[/COLOR]

Of course. What you could try is 

1) connect the external drive and load into 12.04 internal and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Then see if you can now load 12.04 internal with the external drive disconnected.

Regards.

---

### Post by buck2 on 2014-12-20
Thank you, 
My goal is to avoid having to reinstall and reconfigure every piece of software I use on 14.04.  I just want to make sure that if it fails, I can be up and running again in an hour or two rather than a day or two.

---

### Post by oldfred on 2014-12-20
> rather than a day or two. 				

That is a Windows reinstall.

All your user &  software configuration files are in the .file and .folders in your /home. So if you restore /home all those settings are automatically restored.
The only setting not automatically reinstalled would be those system wide settings like fstab, grub, NFS or Samba that are in /etc. And you can save and copy those settings very easily again.

If you export a list of installed apps, then you can easily reinstall all those. Best to houseclean before saving file and you may want to edit out old kernels if they get included. And sometimes Ubuntu changes default app and if you do not both may want to edit out the old one. But list is very long as it includes all dependencies. Defaults  already installed would not be reinstall.

---

### Post by buck2 on 2014-12-21
Well, old fred, old friend, I wish I knew that I upgraded from 10 to 12 and lost everything. 

I have been using Ubuntu since about version 7 when they were sending out all the CDs.  But I have still have a poor understanding of how it works underneight.

I did finally do the upgrade.  It has a little bug, but I am trying to get the backup working right now.


Thank you to everyone who responded.

---

### Post by oldfred on 2014-12-21
I used to do upgrades from 6.06 to 9.04. But clean install, required for change to 64 bit sold me on good backups and clean install.
But then I have more than one drive and cheat. I do not remove old install until well after new install is working well. So if I have forgotten something I can still boot into old install or mount it and recover something.

---

### Post by buck2 on 2015-01-02
UPDATE: I completed my upgrade and all appeared to be doing well until New  Year's Eve.  Then I my fonts all went spastic.  My desktop icons are  about 4 times larger and all my fonts shrunk so small and thin that I  can barely read them. 

I'm creating a new thread for that issue.

---

