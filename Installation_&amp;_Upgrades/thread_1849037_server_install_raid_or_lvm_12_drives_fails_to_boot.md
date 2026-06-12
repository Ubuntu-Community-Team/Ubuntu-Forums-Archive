---
title: "server install raid or lvm 12 drives fails to boot"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by abocanegra on 2011-09-23
So I've used this forum many times in the past but have never posted. 

I hope you can help me once again though. 

Situation:
Attempting to install ubuntu 11.04 server X64 on a Dell C2100 with (12) 2tb drives. 
There are 2 very basic controller cards (perc h200) installed by dell.  (No budget at this point to upgrade to better controllers)
    Controller #0 - (4) 2tb sas drives
   Controller #1 - ( 12 ) 2tb sas drives. 

I want to use Raid10 across all 12tb giving me approx. 12 tb of useable space after swap and bios-grub. 

After many hours, and possibly dozens of different approaches, some made up, some taken from forums and tutorials I have not found a satisfying solution than boots properly.  The only approach that booted properly - and without post-install live CD fiddling - was to raid10 the 4 drives on controller 0 and raid 10 the 8 drives on controller 1. Then during install i installed the bios-grub /root swap to the 8tb raid and the 4tb went to just data  

That worked but not what i want  the bulk of the space needs to be contiguous.

Failed setups include:
Multiple attempts at software raid from ubuntu install process.  Could not fix the boot to load from md0 or md1 dependong on the order i placed the root boot swap partions. I even tried with and without /boot and bios-grub.  Could not get grub to work using live cd or recovery mode  
Multiple lvm attempts as well same general issue as software raid  

Current state(willing to wipe and start from scratch):
Install says no issues and installs grub to mbr.  
Still does not boot at startup.
Hardware raid10 on both controllers (making 2 virtual drives)
From virtual drive on controller 0 i make a bios-grub partion, lvm space,/boot,swap
Controller 1 becomes all lvm
Lv logical group consists of both lvm spaces and is dedicated to /root  

This may be awkward but is the closest ive come in countless attempts.  In rescue or live cd i can get update-grub to look right, thr grub-install /dev/sda looks right. None of the errors shown during straight software raid or lvm installs appear....still wont boot.

Sorry for rambling  statement with no outputs or code  I am writing from my phone and am not on site, which is currently the only access to i have to the server until it boots on its own.

Any help, suggestions appreciated

---

### Post by YesWeCan on 2011-09-23
It would be helpful to see exactly what is on your disks. Not all 12 are needed but just one would do:
[COLOR="DarkSlateBlue"]sudo sfdisk -luS /dev/sdx[/COLOR]

And what the RAID components are:
[COLOR="DarkSlateBlue"]cat /proc/mdstat[/COLOR]

I suspect some potential issues. Using GPT when you don't need to. Making sure bios_grub is outside of the RAID. But I can advise better when you've posted the above.

---

### Post by abocanegra on 2011-09-24
Thanks for your help...Here is a brief structure recap and the requested info.
Hardware setup
"virtual disk 0": sda  consists of ( 4 )  drives that are on a hardware raid through the perc h200 controller 0
"virtual disk 1": sdb consists of ( 8 ) drives that are on a hardware raid10 through the perc h200 controller 1
Software Setup
"Virtual Disk 0": boot-grub, lvm, /boot, swap
"Virtual Disk 1": lvm
lvmgroup logical volume includes disk 0 and 1 for approximately 12tb space and is formatted as ext4 mounted at /

From Virtual Disk 0 (SDA)
```

[COLOR=DarkSlateBlue]sudo sfdisk -luS /dev/sda

WARING: GPT (GUID Partition Table) detected on 'dev/sda' The util sfdiskdoesn't support GPT. Use GNU Parted.

Disk /dev/sda: 486267 cylinders, 255 heads, 63 secors/track
Units = sectors of 512 bytes, counting from 0

Device Boot                         Start                           End                         #sectors              Id             Stystem
/dev/sda1                               1               4294968293                      4294967293               ee      GPT
                                           start:(c,h,s) expected (0,0,2) found (0,0,1)
/dev/sda2                              0                                 -                                 0                         0          Empty
[/COLOR][COLOR=DarkSlateBlue]/dev/sda3                               0                                 -                                  0                         0          Empty
[/COLOR][COLOR=DarkSlateBlue]/dev/sda4                               0                                 -                                  0                         0          Empty[/COLOR]


```
From Virtual Disk 1 SDB
```

[COLOR=DarkSlateBlue]sudo sfdisk -luS /dev/sdb

[/COLOR][COLOR=DarkSlateBlue]WARING: GPT (GUID Partition Table) detected on 'dev/sda' The util sfdiskdoesn't support GPT. Use GNU Parted.
  
Disk /dev/sba: 972535  cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0
  
Device Boot                         Start                            End                         #sectors              Id             Stystem
/dev/sdb1                               1               4294967295                      4294967295                ee        GPT
                                           start:(c,h,s) expected (0,0,2) found (0,0,1)
/dev/sdb2                              0                                  -                                 0                         0           Empty
[/COLOR][COLOR=DarkSlateBlue]/dev/sdb3                               0                                 -                                  0                         0          Empty
[/COLOR][COLOR=DarkSlateBlue]/dev/sdb4                               0                                 -                                  0                         0          Empty[/COLOR]
[COLOR=DarkSlateBlue]
[/COLOR]
```

```

cat /proc/mdstat

Pesonalities: [raid0] [raid1] [raid6] [raid5] [raid4]
unused devices: <none>

```Since I am using a hardware raid this time around i think the mdstat makes some since, but the other info seems quite off.

I have tried many approaches, if I need to wipe and start from scratch I am completely fine with that.
Thanks for looking at this for me.

---

### Post by abocanegra on 2011-09-24
I got it working. 
Looking at your comment about the grub_boot I decided to get rid of the hardware raid altogether and while i was doing that I notice that even though the controller 0 has 4 drives and  has 8, it was booting from 1 first, where the grub was not placed, I corrected this and then went with a software raid during install instead. I put the boot_grub outside of the raid on sda and then raided the rest for / and swap. It booted right up.

Thanks.

---

### Post by YesWeCan on 2011-09-24
Good stuff, you are welcome. :)

Just for anyone else reading this, if your disks are less than 2TiB big you avoid a lot of unecessary complexity if you format them MBR rather than GPT. With a GPT and BIOS booting, which is the typical scenario, Grub needs a separate bios_grub partition that must not be inside a RAID or LVM. If you use MBR format, however, there is no such complication. For most users there are no benefits to GPT over MBR unless your disks are bigger than 2TiB.

Don't forget to mark this as solved in [COLOR="Red"]Thread Tools[/COLOR].

---

