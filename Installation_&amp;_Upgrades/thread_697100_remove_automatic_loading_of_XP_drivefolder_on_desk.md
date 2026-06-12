---
title: "remove automatic loading of XP drive/folder on desktop"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by Hizzoner on 2008-02-14
I made a change which I wish to reverse. The XP partition/drive/folder is automatically loaded when I boot Ubuntu 8.04. I then have to unload same manually.How do I remove this auto loading app.?

---

### Post by stevejesus on 2008-02-14
I dont understand completely what you mean.  If you mean to stop a Windows partition from auto-mounting, then all you have to do is remove the drive's entry from /etc/fstab/

---

### Post by Hizzoner on 2008-02-14
Hi ...Pls. advise me as as to which line should be removed...many tnx..../H

---

### Post by Hizzoner on 2008-02-14
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=9284af7a-4470-44c4-ad72-ae366b41250a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=dd539f6d-08ed-4325-83cb-a9dd34a13d04 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"fstab" [readonly] 10 lines, 546 characters

---

### Post by blazerte on 2008-02-14
This sounds like the gnome-volume-manager problem. By default it seems to mount all available media, removable or not. I had four different, unwanted partitions loaded at boot. 
   
Anyway, read /etc/hal/fdi/policy/preferences.fdi and comment out the section for ignoring non-removable devices. It should look like this when you're done:

<!--
  The following shows how to hint gnome-volume-manager and other programs
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>

Then reboot. That worked for me.

---

