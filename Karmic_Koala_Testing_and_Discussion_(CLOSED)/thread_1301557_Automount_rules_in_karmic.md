---
title: "Automount rules in karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by n0_mad on 2009-10-26
Solution:
> I found solution finally. 
Just add ```
gnome-mount -p Data(change it to your volume label)
``` to gnome startup applications. Now drive will be mounted at startup and you will be able to mount/unmount it without any errors.

Hi,

By default ubuntu don't mount internal ntfs hard drives automatically. 
Solution with fstab is not working properly, because of conflict with "intelligent" mount system. If i add my hd in fstab and reboot - it will be mounted. But if you go to nautilus, open places panel and click eject button(unmount) and than click on hd again to mount it you will get an error: > Error mounting: mount exited with exit code 1: helper failed with: Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged) But options in fstab allow me to mount this drive.

In 9.04 to solve this problem you need to modify hal rules in /etc/hal/... preferences.fdi in my case i modified it for only one drive.
```
<device>
&#8722;
<match key="storage.hotpluggable" bool="false">
&#8722;
<match key="storage.removable" bool="false">
<merge key="storage.automount_enabled_hint"  type="bool">false</merge>
&#8722;
<match key="storage.model" string="ST3250310NS">
<merge key="storage.automount_enabled_hint" type="bool">true</merge>
</match>
</match>
</match>
</device>

```

But this is not working in 9.10 - devs removed this function from hal to devkit-disk or udev? I don't know. 
Could you please tell me where automount rules stored in 9.10? And how to create new rules, and what program controlls automount in 9.10.

---

### Post by dulek on 2009-10-27
I'm looking for a solution too. Do I really need to build NTFS-3G manually?

---

### Post by n0_mad on 2009-10-28
Bump. 9.10 is out, so this thread should be moved to general forums again i think.

---

### Post by Elcid247 on 2009-10-29
Since "Hal" is being deprecated, and ubuntu moved to devicekit-disks, i had a hard time figuring out how to set my drives to autmount on startup like i used to do with editing /etc/hal/fdi/policy/preferences.fdi and setting automount to ture.

i just found a solution for this, thanks to [this]("http://www.debianhelp.org/node/9937")

do this

```
sudo gedit /lib/udev/rules.d/95-devkit-disks.rules
```

at the end BEFORE ```
LABEL="devkit_disks_end"
```

just add

```
RUN+="/bin/mount -t auto /dev/sda6 /media/Programs"
```

of course replace /dev/sda6 with ur drive number and /media/Programs with the mount point u like.

i also added this rule, dunno if its needed, it was supposed to set me as the owner but i still have to enter my pass if i wana unmount and remount a drive again but i dont care...

```
KERNEL=="/dev/sda[0-9]", OWNER="user"
```

FINALLY! found a solution for this it has been bugging me like hell!

---

### Post by dino99 on 2009-10-29
is there a bug filled ?

---

### Post by n0_mad on 2009-10-29
It is not working.
After rebooting drive is mounted. I click unmount, enter the password, disk unmounts and mounts again instantly.

---

### Post by n0_mad on 2009-10-29
I found solution finally. 
Just add ```
gnome-mount -p Data(change it to your volume label)
``` to gnome startup applications. Now drive will be mounted at startup and you will be able to mount/unmount it without any errors.

---

### Post by Hreinsi on 2009-10-29
You can get pysdm in synaptic the easy way :)

---

### Post by n0_mad on 2009-10-29
You did not read first post and thread - fstab based solutions dont work correct. All this gui tools just modify your fstab.

---

