---
title: "update-initramfs failing to incorporate dmraid properly"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by nyinge on 2007-02-26
[RESOLVED] See this [post]("http://ubuntuforums.org/showpost.php?p=2134349&postcount=3") for details.

It's a debootstrapped system to include dmraid.  I followed this guide, fakeraidhowto, and everything went smooth until a reboot (every reboot for that matter).  The system would stall for a few min and give me an "initramfs" prompt after complaining about not being able to find the raid array, i.e. /dev/mapper/isw_bghfabfaea_Volume01 (Intel software raid).

Only after issuing "dmraid -ay" at the <initramfs> prompt to bring up the raid array, the system continued loading the rest of the services.  Then it's a fully functional system.

The problem I believe is dmraid not being loaded properly at the beginning since the system only works after I issue the command, dmraid -ay.  The symlink to the script, dmraid, is present in the rcS.d folder:
```

S01mountkernfs.sh
S01readahead
S02hostname.sh
S04dmraid
S06keyboard-setup

```Issuing ```
update-initramfs -u -k `uname -r`
``` doesn't seem to help.
Yes, I could wait a few minutes at every reboot, but it's just a little annoyance :(.  Any help is appreciated.  Thank you.

---

### Post by nyinge on 2007-02-27
After much digging, I think it has to do with the program, dmraid, not being activated in the ram disk (initrd).  Where would I find the script (or anything similar) in the initrd that shows a series of programs being initialized?

---

### Post by nyinge on 2007-03-01
Moderators, please consider moving this thread to Feisty (Development) forum.  I apologize for the mistake.

---

### Post by nyinge on 2007-03-20
Refer to this [bug report]("https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/83231") on launchpad.  Make sure you read all the comments as there's a better solution in them.  Just for the record,
```
 udevsettle --timeout=10 
```

---

