---
title: "screwd fstab.."
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by fargoth on 2005-08-01
ive edited fstab with openoffice and it now says there's an error on line 1...
maybe its that null sign in the start of the file i see when i open it in pico?
anyway, i think the best way to fix this is have someone send me a copy of his fstab file....

thats the first one =)

now, the second one is i cant mount my ntfs parition... i mean i did it but only with root permission with
mount -t ntfs /dev/sda1 /mnt/winXP
but i want to have it mounted from startup and with all user permission...
tried entering in fstab 
/dev/sda1 /home/master/Desktop/windrv ntfs default,ro,umask=000 0 0

when using  
# mount /dev/sda1

i got:

[mntent]: line 1 in /etc/fstab is bad
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail 
fb0: VGA16 VGA frame buffer device
eth0: no IPv6 routers present
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
ibm_acpi: ec object not found
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS volume version 3.1.
NTFS-fs error (device sda1): parse_options(): Unrecognized mount option default.

any ideas?

---

### Post by adwait on 2005-08-01
Attaching an my fstab file. Just remove the extention, coz the forums wouldnt let me attach without the extention.

For your second question:
Are you sure /dev/sda1 is the one you want to mount? Are you sure that is not just an extended partition? Maybe you can post tge output of
```
 sudo fdisk -l 
```

---

### Post by fargoth on 2005-08-01
yep, sda1 is the right one as you can see:

 # sudo fdisk -l

Disk /dev/sda: 159.9 GB, 159998918144 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18815   151131456    7  HPFS/NTFS
/dev/sda2   *       18816       19421     4867695   83  Linux
/dev/sda3           19422       19452      249007+   5  Extended
/dev/sda5           19422       19452      248976   82  Linux swap / Solaris

---

### Post by fargoth on 2005-08-01
by the way, wheres the attached fstab?
i couldn't find it...

---

### Post by adwait on 2005-08-01
Uuhoops........forgot to attach :p

Anyway, I put the file in a gz file....so unzip and edit and then copy. But this time, use nano/vi/gedit to edit the file!!

---

### Post by fargoth on 2005-08-01
thanks =)
now it all works well, i got my mp3's...
the only thing left to do now is make it play them...
but i'll open a new thread for that, with a subject about sound card config or something.

---

### Post by adwait on 2005-08-01
no prob. As for mp3s...you'll have to download the gstreamer plugin for mp3s. Or download xmms.

---

