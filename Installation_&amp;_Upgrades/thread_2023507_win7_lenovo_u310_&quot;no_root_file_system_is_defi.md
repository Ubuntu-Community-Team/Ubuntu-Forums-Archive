---
title: "win7 lenovo u310 &quot;no root file system is defined&quot;"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by rsharan on 2012-07-12
Hi,

I'm sorry I think this is an old problem, but I'm running into it. I tried installing 12.04 LTS using wubi but when it reboots into ubuntu it gives "no root file system is defined" error. I ran the boot info script. The results are here:

[B][http://pastebin.ubuntu.com/1088806/](http://pastebin.ubuntu.com/1088806/)

Lenovo U310 comes with a 32GB ssd drive (sda) and a regular HDD (sdb). The above results include a removable live USB (sdc).

Also, just in case, how do I get rid of the wubi installation *completely* and recover the disk partition from pre-installation? I didn't back up anything.

Here is sdb from DiskUtility:
[http://postimage.org/image/m3ea656f5/](http://postimage.org/image/m3ea656f5/)


Thanks
[/B]

---

### Post by shatteredgear on 2012-07-12
> **rsharan said:**
> Hi,

I'm sorry I think this is an old problem, but I'm running into it. I tried installing 12.04 LTS using wubi but when it reboots into ubuntu it gives "no root file system is defined" error. I ran the boot info script. The results are here:

[B][http://pastebin.ubuntu.com/1088806/](http://pastebin.ubuntu.com/1088806/)

Lenovo U310 comes with a 32GB ssd drive (sda) and a regular HDD (sdb). The above results include a removable live USB (sdc).

Also, just in case, how do I get rid of the wubi installation *completely* and recover the disk partition from pre-installation? I didn't back up anything.

Here is sdb from DiskUtility:
[http://postimage.org/image/m3ea656f5/](http://postimage.org/image/m3ea656f5/)


Thanks
[/B]

im having the same issue with my u410, hope someone responds to either of us soon

---

### Post by critin on 2012-07-12
> **rsharan said:**
> Hi,

I'm sorry I think this is an old problem, but I'm running into it. I tried installing 12.04 LTS using wubi but when it reboots into ubuntu it gives "no root file system is defined" error. I ran the boot info script. The results are here:

[B][http://pastebin.ubuntu.com/1088806/](http://pastebin.ubuntu.com/1088806/)

Lenovo U310 comes with a 32GB ssd drive (sda) and a regular HDD (sdb). The above results include a removable live USB (sdc).

Also, just in case, how do I get rid of the wubi installation *completely* and recover the disk partition from pre-installation? I didn't back up anything.

Here is sdb from DiskUtility:
[http://postimage.org/image/m3ea656f5/](http://postimage.org/image/m3ea656f5/)


Thanks
[/B]

I don't believe the Wubi installer supports the 'install inside windows' for 12.04.  You may have to use a virtual machine, using the downloaded iso.  Or use an earlier version of ubuntu with Wubi installer.  (I'm not talking of the wubi.exe, but the installer.)

If it was installed by the wubi installer, it will show in windows add/remove programs.  To completely remove all of it, you'll want to delete the wubi file in 'Programs'.

---

