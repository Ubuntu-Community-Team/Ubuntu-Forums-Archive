---
title: "Feisty upgrade broke my system"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by graabein on 2007-06-13
I used the update manager in Dapper (**edit: Edgy**) and clicked Feisty and it took it's time with no incidents. 

After I tried to boot into my new system it took ages and some errors where reported. I tried to reconfigure xserver and it got screwed up. Every time I boot it takes several minutes and now even the terminal font is just crud. It says something about fstab. 

Where do I go to debug the problem? I don't know much about what log-files to check for errors. When I try the fail-safe alternative in grub I get a readable font for terminal but no X, but I can get to the log-files and also fstab and backup of working xorg.conf files. What worries me is it having screwed up one of my hard drives.

So the question is what log-files to look at when I get home from work?

---

### Post by berg,foss on 2007-06-14
> **graabein said:**
>  

After I tried to boot into my new system it took ages and some errors where reported. 
 

what's errors were reported ?? 

> **graabein said:**
>  
I tried to reconfigure xserver and it got screwed up. Every time I boot it takes several minutes and now even the terminal font is just crud. It says something about fstab. 
 

what is says ???

> **graabein said:**
> 
Where do I go to debug the problem? I don't know much about what log-files to check for errors. When I try the fail-safe alternative in grub I get a readable font for terminal but no X, but I can get to the log-files and also fstab and backup of working xorg.conf files. What worries me is it having screwed up one of my hard drives.
 

Its normal in failsafe mode (rescue) , dont start x ,because this is a emergency mode, and  is used  to have access a configurations files in the  a usable system ( aka not freeze system :p ).

> **graabein said:**
>  
So the question is what log-files to look at when I get home from work?

in /var/log folder exists some files that  can help : 

dmesg 

dmesg.* ( olders dmesg files)

Xorg.0.log

Xorg.0.log.old


you can attach this files,but need a valid extension accept by forum program in addition options above. So you need zip the files or add .txt suffix ( copy original file to you home  and rename it )

---

### Post by silkstone on 2007-06-14
I thought you had to upgrade one step at a time - Dapper > Edgy > Feisty???

---

### Post by Pumalite on 2007-06-14
> **silkstone said:**
> I thought you had to upgrade one step at a time - Dapper > Edgy > Feisty???

Correct.

---

### Post by graabein on 2007-06-15
Oh I'm sorry I just messed up the names. I did upgrade to Edgy when it came out and everything was dandy. Except I couldn't get Beryl/Compiz to run on two X screens but at least I had tv-out and the nVidia config app was nice.

I'll boot it up when I get home from work and take notes. Thanks for the replies. :D

---

### Post by graabein on 2007-06-27
Hello again. I didn't get around to look into this before I went away on holiday. 

Don't know if I'll try to fix it or rather do a clean install. It might be quicker than debugging the problem and I've updated the system each time since Warty or whatever I installed originally back in 2004/2005 so it might be high time for a clean sheet.

If I choose to reinstall the system I'll naturally keep the **/home** partition and do the route where I add the same users I had earlier and hook them up with the corresponding user directories. Does anyone know if there's a wiki page on this?

What do I need to check before a clean install besides **fstab**? -- or does the *alternate install disc* detect partitions automatically?

---

### Post by graabein on 2007-07-31
OK here is my **fstab** and it don't look nice!

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=bf530c25-4f49-49fa-8636-b368d368375d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=024f689b-dde0-4fe4-944b-c4653ce0f932 /home ext3 defaults 0 2
/dev/hdd        /media/dvd   udf,iso9660 ro,user,noauto  0       0
/dev/cdrom        /media/cdrom   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy  auto    rw,user,noauto  0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=bdee2bc9-6e8a-443f-8015-d7dd25fa38b6 /mnt/store ext3 defaults 0 2
```

I booted a Feisty CD (7.04) yesterday and got the **fstab** file + my freevo skin off the **root** partition. 

Anyone know if a clean install picks up my old user directory or do I have to create a different name master user and do the thing manually afterwards?

Gonna try to get the log files off the computer when I get home.

---

### Post by logos34 on 2007-07-31
Another poster had a similar question just yesterday.  Check out this link:
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion?highlight=%28%2Fhome%29%7C%28install%29](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion?highlight=%28%2Fhome%29%7C%28install%29)

Remember to use the same username and be careful not to format /home (hda6)

---

### Post by graabein on 2007-07-31
Thanks. I wonder what happens with my dual boot with XP - Can I leave GRUB as is?

---

