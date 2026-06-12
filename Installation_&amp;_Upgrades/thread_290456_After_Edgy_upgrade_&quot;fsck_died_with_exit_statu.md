---
title: "After Edgy upgrade: &quot;fsck died with exit status 8&quot;"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Dafydd on 2006-11-01
After upgrading (and fixing xorg problems), I still get an error fsck error message which opens up a root terminal. If I exit "root", then the system goes on to boot (it concerns a partition with Suse 10.1 on it).

Anyone have any ideas?
Thanx
Daf

----------

Log of fsck -C -R -A -a 
Wed Nov  1 11:11:27 2006

fsck 1.39 (29-May-2006)
/dev/hda5: clean, 10992/2215168 files, 3429595/4427907 blocks (check after next mount)
fsck.ext3: Unable to resolve 'UUID=d64d70d0-f73d-4922-a64e-2bb8a663e09f'

fsck died with exit status 8

Wed Nov  1 11:11:27 2006
----------------

---

### Post by thoolihan on 2006-11-01
what's your /etc/fstab look like?  You ought to be able to disable that filesystem from being checked by putting a 0 in the sixth column of that entry in the fstab, or better yet, don't list it in fstab, since it's not part of your ubuntu install.

---

### Post by Max_Might on 2006-11-01
I have exactly the same problem
[http://www.ubuntuforums.org/showthread.php?t=290380](http://www.ubuntuforums.org/showthread.php?t=290380)
any how can we fix this?? I want my ubuntu back :]
in my case the error is in hdb3 but it is my root filesystem .....

---

### Post by Dafydd on 2006-11-02
> **thoolihan said:**
> what's your /etc/fstab look like?  You ought to be able to disable that filesystem from being checked by putting a 0 in the sixth column of that entry in the fstab, or better yet, don't list it in fstab, since it's not part of your ubuntu install.

hi,
thanx for reply. here's my fstab. i would still like to access the problematic Suse partition from ubuntu (to use as storage for media files or copy over data, etc).

daf

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=42aceba7-706e-41cb-9845-770f8d07ec4a / reiserfs notail 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=6d807015-e469-48e2-b050-c7db1ddbbbc5 /home ext3 defaults 0 2
# /dev/hda1 -- converted during upgrade to edgy
UUID=d64d70d0-f73d-4922-a64e-2bb8a663e09f /media/hda1 ext3 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=7445ea9e-bd73-41fb-8a56-6ba03f2c4739 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by thoolihan on 2006-11-02
If you read here:  [http://ubuntuforums.org/showthread.php?t=286758](http://ubuntuforums.org/showthread.php?t=286758), it explains the new fstab system.  Use the command in that thread(sudo vol_id -u <partition>) to verify that your fstab in fact has the right UUID's.  

If it still fails, I would make a backup of fstab and switch it back to using traditional identifier's, like /dev/hda1.

Hope that helps.

---

### Post by Max_Might on 2006-11-02
thoolihan, thanx for the useful link, I`ll try this and see if it works.

---

### Post by Max_Might on 2006-11-02
yeeey it works, i just removed the line with the bad partition from fstab, i never used this partition (8 mb :) ), then had to reconfigure the X server and now i have Edgy :)
thanks again m8 :)

---

### Post by Dafydd on 2006-11-04
> **thoolihan said:**
> what's your /etc/fstab look like?  You ought to be able to disable that filesystem from being checked by putting a 0 in the sixth column of that entry in the fstab, or better yet, don't list it in fstab, since it's not part of your ubuntu install.

thanx. i just deleted the entry and now everything works fine. the sudo uid thing did not work though.

daf

---

