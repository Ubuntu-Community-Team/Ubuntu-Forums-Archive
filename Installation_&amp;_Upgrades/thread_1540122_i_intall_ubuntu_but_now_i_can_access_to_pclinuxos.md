---
title: "i intall ubuntu but now i can access to pclinuxos"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by laimigrante on 2010-07-27
i use the option when i install to install both side by side chosing wich one to login, but now i can access to pclinuxos after i install ubuntu.

---

### Post by realzippy on 2010-07-27
You can or cannot?
If not,run

```
sudo update-grub
```

Is pclinuxos listed in the output?

---

### Post by laimigrante on 2010-07-27
cannot, 
yes is listed

---

### Post by realzippy on 2010-07-27
Is it still not reachable when rebooting?

---

### Post by laimigrante on 2010-07-27
not, kinda start but then stop and the last output say, 
kernel panic- not syncing: vfs: unable to mount root fs on unknow-bock(0,0)

---

### Post by realzippy on 2010-07-27
Do not know if pclinuxos also has grub as bootloader...someone?

Do I understand the problem correctly?:
You can choose between pclinuxos and ubuntu during boot (grub menue),and if you choose "pclinuxos" it starts giving this error?=
**kernel panic- not syncing: vfs: unable to mount root fs on unknown-block(0,0)**

Maybe useful to see your
/etc/fstab    :

```
gedit /etc/fstab
```

---

### Post by laimigrante on 2010-07-27
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0b62e169-b9eb-462b-83f9-87e11916e8cb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=9d98b810-8e7b-493e-9444-d999e2f943e9 none            swap    sw              0       0

---

### Post by realzippy on 2010-07-27
Give [Supergrubdisc]("http://www.supergrubdisk.org/wiki/SuperGRUB2Disk#Difference_between_Super_GRUB_Disk_and_Super_GRUB2_Disk") a try to detect and repair your grub.Otherwise
a new thread might be useful titled with that error message,since this title is a bit irritating.
*kernel panic- not syncing: vfs: unable to mount root fs on unknown-block(0,0)*
further explanation only that pclinuxos stops booting after ubuntu install (name version!)

---

### Post by laimigrante on 2010-07-28
actualy im looking where to download supergrub and from their homepage say error page not found.

---

### Post by laimigrante on 2010-07-28
ok i find where to download, i click on detect any os, and click on pclos and pclos boot from sgrub cd, but not without the cd of supergrub, so im kinda lost im not sure how im going to work with this cd, just work at the moment not work without the cd.

---

### Post by realzippy on 2010-07-28
I am not sure which bootloader pclinuxOS uses.If it
is grub then it might be the problem that ubuntu lucid uses grub2,which
differs in counting partitions.(hd0,0) in grub is (hd0,1) in grub2.

If it is grub in pclinuxOS,then there should be a file:
*/boot/grub/menu.lst* in pclinuxOS.**Starting Ubuntu** and open this file
from ubuntu and edit all (hdx,x) in (hdx,x+1) might do it.

After this editing run
```
sudo update-grub
```
in Ubuntu.

Any suggestions and comments are welcome,grub is not my favorite theme !



Edit:
Another idea is to boot pclinuxos from it's LiveCD,open a root terminal there and run
```
redo-mbr
```

---

### Post by laimigrante on 2010-07-28
thanks i went to pclinuxos forums, and they told me that to try running **Redo MBR** from the PCLinuxOS LiveCD, and works.

i notice that u told me to that 2.

thanks!

---

