---
title: "NTFS permission changes to everyone on dual boot HDD"
date: 2023-09-07
forum: Installation &amp; Upgrades
---

### Post by richthommy on 2023-09-07
I'm running Kubuntu [FONT=monospace][COLOR=#000000]22.04.3 LTS.

[/COLOR]I've placed this in my /etc/fstab file
[/FONT]UUID=01D96FD73EC749C0 /mnt/windows ntfs defaults,nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002,x-gvfs-show 0 0

When I type mount on the Terminal it shows this
[FONT=monospace][COLOR=#000000]/dev/sda3 on /mnt/windows type fuseblk (rw,nosuid,nodev,noatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,x-gvfs-show)

I'm thinking Linux is overriding my settings.

When I write any file on the Windows NTFS file system, it changes the security permission to Everyone only. Is possible for this not to happen.
[/COLOR]
[/FONT]

---

### Post by Holger_Gehrke on 2023-09-07
Is that line verbatim what you have in your fstab ? Including the space in 'no atime' ? Then that space is the culprit. The option is noatime (no space). The options are a comma-separated list with **NO** spaces. At the space mount assumes that there are no further option and tries to parse everything after the space as the 5th and 6th fields.

Holger

---

### Post by TheFu on 2023-09-07
> **Holger_Gehrke said:**
> Is that line verbatim what you have in your fstab ? Including the space in 'no atime' ? Then that space is the culprit. The option is noatime (no space). The options are a comma-separated list with **NO** spaces. At the space mount assumes that there are no further option and tries to parse everything after the space as the 5th and 6th fields.

Holger

+1 on spaces as the issue. I see 2, not just "no atime" ... there's another. No spaces are allowed anywhere in the "options" part of the mount.  There need to be 6 space-separated fields, not 7 or 8 or more.  The last two are optional, typically for NTFS, those would be "0 0" anyway, so pretty useless.  1 space or 10 spaces together doesn't matter. contiguous spaces are a single field separator.

Also, the *permissions* option only worked for me about 4 weeks, then never again.  That was after I setup that separate directory on the NTFS storage to handle uid/gid to Windows UUID/GUID mapping too. Without that mapping setup, I don't see how permissions from a different OS could be honored.

At the top level of the NTFS file system, if you aren't using AD for account management, then a directory named 
```
.NTFS-3G
```
with a file inside named, .NTFS-3G/UserMapping
that looks something like this:
```
1000:1000:S-1-5-21-3141592653-589793238-462643383-1000
Undecided :

1001:1001:S-1-5-21-3141592653-589793238-462643383-1001 
1002:1002:S-1-5-21-3141592653-589793238-462643383-1002
1003:1003:S-1-5-21-3141592653-589793238-462643383-1003 
1004:1004:S-1-5-21-3141592653-589793238-462643383-1004 
1005:1005:S-1-5-21-3141592653-589793238-462643383-1005 
1006:1006:S-1-5-21-3141592653-589793238-462643383-1006 

```
is required.  Check your Windows install to find the mapping between users and unique identifiers. I cheated.

---

### Post by MAFoElffen on 2023-09-07
+1 --

As a sidenote, here are two mount lines from the fstab of my workstation... that I think I put together from reading some of TheFu's recommendations to other people over the years... (Thank you TheFu.)
```

UUID=0A24D9F224D9E0AD             /home/mafoelffen/WIN_G  ntfs  defaults,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0 
UUID=828C01738C016351             /Media_H                ntfs  defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0 

```
I think they have both worked well, with no problems for over 6 years now.

---

