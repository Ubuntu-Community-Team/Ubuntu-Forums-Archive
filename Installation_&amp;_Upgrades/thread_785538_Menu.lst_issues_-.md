---
title: "Menu.lst issues -"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt on 2008-05-07
Hi,
I have 3 Hard Drives and all of them have some version of Linux installed on them (HD1 = Ubuntu 8.04, HD2 = Mandriva 10.3 and HD3 = Ubuntu 7.10). After installing Mandriva on my second HD, the menu that I get upon restart seems to be coming from HD3 - I would like the menu to come from HD1 since that is my primary drive. The other thing is, I get a "file not found" error when I select Mandriva from the grub menu - any help on the above two would be greatly appreciated.

thanks,
DB

---

### Post by confused57 on 2008-05-07
You can install whichever distro's grub to the main drive's mbr that you want, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You can then add an entry to boot Mandriva:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

If you use chainloading, you need to setup grub on the root partition of the distro you're wanting to boot, e.g.
```
root (hd1,0)
setup (hd1,0)
```

For a configfile entry, I'm not sure if Mandriva uses menu.lst or grub.conf:
configfile (hd1,0)/boot/grub/grub.conf
or
configfile (hd1,0)/boot/grub/menu.lst

Grub doesn't need to be installed to the root partition, if you use configfile method to boot.

---

