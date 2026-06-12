---
title: "Upgrading from 9.04 to 10.10"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by jsirotto on 2010-12-26
I currently have Ubuntu 9.04 Installed and everything works perfectly. Its no longer allowing me to do the automatic updates saying my distribution version isnt supported anymore, and want to upgrade to 10.10.

When version 9.10 came out I upgraded through the Update Manager, and it screwed up the install and nothing worked.  I ended up deleting everything and started from scratch. I dont want to go through that again. 

I was wondering the easiest way to upgrade to version 10.10, because even the Update Manager only gives me the option to upgrade to version 9.10

 Thanks

---

### Post by Megaptera on 2010-12-26
I found the easiest and safest way was to back-up all my docs, pics etc to external media and do a new install of 10.10. wiping previous version completely.

---

### Post by mikewhatever on 2010-12-26
The only way to upgrade from 9.04 would be 9.04->9.10->10.04->10.10.

---

### Post by karthick87 on 2010-12-26
Ubuntu 9.04 has reached the EOL.So no updates will be available.Backup all your important datas and have fresh installation of ubuntu 10.04 or ubuntu 10.10

---

### Post by jsirotto on 2011-01-16
Ok so I backup up my entire home folder before I reinstall Ubuntu (upgrading to 10.10).  Will it be as easy as replacing my version 10.10 Home Folder with my 9.04's? Will it bring everything in properly?

---

### Post by kansasnoob on 2011-01-16
> **jsirotto said:**
> Ok so I backup up my entire home folder before I reinstall Ubuntu (upgrading to 10.10).  **Will it be as easy as replacing my version 10.10 Home Folder with my 9.04's?** Will it bring everything in properly?

No! There have been too may changes to .gconf and .gnome(2) just to name a couple.

Do me a favor and post the output of:

```
sudo parted -l
```

And:

```
df -H
```

BTW that's a lower case L in "parted -l" and I deliberately used a capital H.

Also, please post the output of those two commands using code tags by clicking on the **#** at the top right of the reply box, then with the cursor blinking between the code tags complete the copy-n-paste. It makes it soooooooo much easier to read :D

---

### Post by jsirotto on 2011-01-16
```

Model: ATA Maxtor 6Y080L0 (scsi)
Disk /dev/sda: 82.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags    
 1      32.3kB  82.0GB  82.0GB  primary  fat32        boot, lba


Model: ATA WDC WD5000AAKB-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  497GB  497GB   primary   ext3              
 2      497GB   500GB  3076MB  extended                    
 5      497GB   500GB  3076MB  logical   linux-swap        




```

```

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb1              490G    58G   408G  13% /
tmpfs                  526M      0   526M   0% /lib/init/rw
varrun                 526M   218k   526M   1% /var/run
varlock                526M      0   526M   0% /var/lock
udev                   526M   168k   526M   1% /dev
tmpfs                  526M   205k   526M   1% /dev/shm
lrm                    526M   2.3M   524M   1% /lib/modules/2.6.28-19-generic/volatile


```

---

### Post by kansasnoob on 2011-01-19
Oops, I failed to see this yesterday :(

But with a 500GB drive, and Ubuntu on a 497GB partition with only 13% used you could quite easily install either 10.04.1 or 10.10 in a dual-boot with your existing Ubuntu. I do a lot of distro-testing (particularly Ubuntu iso-testing & upgrade-testing) so this is total overkill but have a look:

[ATTACH]181505[/ATTACH]

You'll notice that I use Gparted to label my partitions, that way they're easily identified when I go to Places > Removable Media. In this example the OS I'm running is on the left the OS I mounted in Removable Media is on the right:

[ATTACH]181509[/ATTACH]

As with most things there are a few caveats to be aware of:

DO NOT copy parts of the "running" OS to the "non-running" OS, but rather vice-versa. Then either reboot or restart X for the changes to take effect.

Rather than "removing" existing files/folders on the new OS just rename them. I quite often append the name with a "_OLD", then after a reboot if things seem to be OK I send the "_OLD" file or folder to the trash.

DO NOT use the "Move to" option in Nautilus, but rather the "Copy to" option. That way the existing data is left unchanged so the old OS will operate normally until you're thoroughly satisfied that all is well with the new OS. 

Many of the "parts and pieces" you'll want to copy are "hidden" so in Nautilus go to View > Show hidden".

If you choose to install 10.10 please read my posts #1 and #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Basically if you use the "Install alongside other operating systems" option in the 10.10 installer the next screen includes "buttons" to "Use entire partition" or "Use entire disc". **[COLOR="Red"]Clicking on either of those buttons is likely to erase all data on your drive![/COLOR]**

I've had a lot of interruptions this AM, I'll try and type a more coherent post ASAP.

---

