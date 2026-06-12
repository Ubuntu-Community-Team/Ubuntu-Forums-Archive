---
title: "What happens with the uninstalled software?"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by kosak on 2008-01-16
Hi,

This is something that has been confusing me after I migrated to Gutsy from XP. When I uninstall a program from synaptic or apt-get remove I can still find files that belonged to that program usually under my home or other folders. For example I tried Parallels ([www.parallels.com]("http://www.parallels.com")) and uninstalled it. When I do "locate parallels" I get: 

---start----

kosak@kosak:~$ locate parallels
/usr/lib/parallels
/usr/lib/parallels/.parallels_common_options
/usr/lib/parallels/.parallels_license_2.2B
/usr/lib/parallels/.ereaded
/usr/lib/parallels/.dhcp.vnic0
/usr/lib/parallels/.dhcpd_configuration
/usr/lib/parallels/.random_salt
/usr/share/mime/packages/parallels.xml
/usr/share/mime/application/x-parallels-virtual-disk.xml
/usr/share/mime/application/x-parallels-vm.xml
/usr/share/mime/application/x-parallels-virtual-floppy.xml
/usr/share/applications/parallels-hdd.desktop
/usr/share/applications/parallels.desktop
/usr/share/applications/parallels-fdd.desktop
/usr/share/pixmaps/parallels-hdd.png
/usr/share/pixmaps/parallels-fdd.png
/usr/share/pixmaps/parallels-pvs.png
/usr/share/mimelnk/application/x-parallels-vm.desktop
/usr/share/mimelnk/application/x-parallels-virtual-floppy.desktop
/usr/share/mimelnk/application/x-parallels-virtual-disk.desktop
/usr/share/icons/hicolor/48x48/apps/parallels-hdd.png
/usr/share/icons/hicolor/48x48/apps/parallels-fdd.png
/usr/share/icons/hicolor/48x48/apps/parallels-pvs.png
/usr/share/icons/Human/48x48/apps/parallels-hdd.png
/usr/share/icons/Human/48x48/apps/parallels-fdd.png
/usr/share/icons/Human/48x48/apps/parallels-pvs.png
/usr/share/icons/crystalsvg/48x48/apps/parallels-hdd.png
/usr/share/icons/crystalsvg/48x48/apps/parallels-fdd.png
/usr/share/icons/crystalsvg/48x48/apps/parallels-pvs.png
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-application-x-parallels-virtual-disk.png
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-application-x-parallels-vm.png
/usr/share/icons/gnome/48x48/mimetypes/gnome-mime-application-x-parallels-virtual-floppy.png
/usr/share/icons/gnome/48x48/mimetypes/parallels-hdd.png
/usr/share/icons/gnome/48x48/mimetypes/parallels-fdd.png
/usr/share/icons/gnome/48x48/mimetypes/parallels-pvs.png
/usr/share/icons/gnome/48x48/apps/parallels-hdd.png
/usr/share/icons/gnome/48x48/apps/parallels-fdd.png
/usr/share/icons/gnome/48x48/apps/parallels-pvs.png
/etc/rc2.d/K90parallels
/etc/rc2.d/S90parallels
/etc/rc3.d/K90parallels
/etc/rc3.d/S90parallels
/etc/rc5.d/K90parallels
/etc/rc5.d/S90parallels
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vm-main.o
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/hypervisor.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/hypervisor.mod.o
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vmvirtualnic.o
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vmvirtualnic.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vm-bridge.mod.o
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/hypervisor.o
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vm-main.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vm-main.mod.o
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vmvirtualnic.mod.o
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vm-bridge.o
/lib/modules/2.6.22-14-generic/kernel/drivers/misc/parallels/vm-bridge.ko
/home/kosak/.qt/parallelsworkstationrc
/home/kosak/.qt/.parallelsworkstationrc.lock
/home/kosak/.local/share/applications/parallels.desktop
/home/kosak/.parallels_settings

---End---

Maybe not the best example. but this tends to happen with other software as well.

So, should I manually delete these files, or is there another way to take them away? (I always use apt-get remove, auto clean, and on synaptic I check for orphaned dependencies to make sure I take it all). 

I remember on windows one could use a regcleaner to get all those traces away from the computer, is there something similar on Ubuntu?

My second question is when installing from source (e.g. conky). I get the tar ball and follow the install instructions, but they never specify how to uninstall it. I tried to "make uninstall" but nothing there... so for the compiled programs that don't have uninstall on them what should i do, just hand delete (rm or similar -nautilus)? And is "make uninstall" a universal thing?

Finally, can I delete the *.deb files from "/var/cache/apt/archives/" that I don't use?

Thanks,

-nico ](*,)

PS. If you have any other info about how to deal with files that should be gone, please reply to the thread!

---

### Post by mikewhatever on 2008-01-16
You can try using purge instead of remove in the future. <sudo apt-get clean> should be removing the cached packages from /var/cache/apt/archives/. In the example of parallels, you'd have to remove the leftovers manually, since the package's been uninstalled.

---

### Post by meindian523 on 2008-01-16
and it's good to backup the /var/cache/apt/archives using APTonCD before deleting them jut in case you ever need (unlikely) to reinstall.
APTONCD:

```
sudo apt-get install aptoncd
```

---

### Post by mikewhatever on 2008-01-16
> **meindian523 said:**
> and it's good to backup the /var/cache/apt/archives using APTonCD before deleting them jut in case you ever need (unlikely) to reinstall.
APTONCD:

```
sudo apt-get install aptoncd
```

By the time one might need to reinstall, the backup would be outdated, so, why would one backup stuff one is unlikely to need and can get any time the latest version?

---

### Post by kpkeerthi on 2008-01-16
The **locate** command searches a local database of list of files present in your system. Ubuntu runs **updatedb** command via a cron to update the database periodically. 
You need run this command manually to sync it up as soon as you delete or add files to your system. 
```

sudo updatedb

```

---

### Post by meindian523 on 2008-01-16
> **mikewhatever said:**
> By the time one might need to reinstall, the backup would be outdated, so, why would one backup stuff one is unlikely to need and can get any time the latest version?
<rant>
APTonCD exists because there is a need for it,in the developing countries where broadband is not so common,so people can share their packages using it and others use it because they don't want to change their OS every six months or each year.Please don't be so imperious as to tell that anyone should immediately update/upgrade to the newest release/newer versions of apps if the present release suits their requirements.
</rant>
I meant that you got everything setup perfectly and you just want to install that last app and that messes up your system irrevocably /your HDD crashes/gives up on you.That's when you want to reinstall and it's possible that a new release might not be out at that point in time.Again,I point you to my rant.

---

### Post by mikewhatever on 2008-01-16
> **meindian523 said:**
> <rant>
APTonCD exists because there is a need for it,in the developing countries where broadband is not so common,so people can share their packages using it and others use it because they don't want to change their OS every six months or each year.

The original poster's location reads 'Rochester, NY', in case you haven't noticed.

> Please don't be so imperious as to tell that anyone should immediately update/upgrade to the newest release/newer versions of apps if the present release suits their requirements.

I never have. Frankly, I could not care less, given the amount of PCs currently running Linux, plus the lack of malware.

> </rant>
I meant that you got everything setup perfectly and you just want to install that last app and that messes up your system irrevocably /your HDD crashes/gives up on you.That's when you want to reinstall and it's possible that a new release might not be out at that point in time.Again,I point you to my rant.

I apologize for any inconvenience my previous post caused. Just to clarify, it's perfectly ok to use aptoncd for whatever reason.

---

### Post by kosak on 2008-01-16
thanks for the info guys..

 still any ideas about the tar ball programs?  

:guitar:

---

### Post by freddyp on 2008-01-16
Here's a link about removing software in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

I've used it with no problems.  Hope this helps.

---

### Post by meindian523 on 2008-01-17
@mikewhatever

It would do good to remember that we are not solving only the OPs problem,our posts will remain on the Net for eternity for other people who have the same problem to look up.So,the location of Rochester,NY really **doesn't** matter.
Apologies accepted.Let's bury the hatchet.

---

