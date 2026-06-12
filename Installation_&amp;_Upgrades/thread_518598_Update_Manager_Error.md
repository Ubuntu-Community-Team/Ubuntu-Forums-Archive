---
title: "Update Manager Error"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by Borb on 2007-08-06
Hello, whenver I try to download the remaining 47 updates I have left, I get the error of 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I know next to nothing about Ubuntu and Linux, so sorry if this is an easy fix.

Also, if anyone could tell me how to un-install Windows so Ubuntu has the full HDD space that would be great, thanks.

---

### Post by girard on 2007-08-06
reformat your drive first to erase windows. to do this, download and burn the live cd of gparted. insert it into the cd drive and reboot. make sure your bios is set to boot from cd, or something to that effect so that it catches the live cd and you can go into gparted. if not, it will continue to boot your hard drive.

but do you already have ubuntu installed? if that's the case, you can create a separate partition while in gparted so you preserve your current ubuntu installation. in essence, that would be deleting the partition windows is in, thus removing windows, and transforming it into an ext3 or whatever file system you want. 

but since you're having problems with the update, why not reinstall the whole of ubuntu anyway? it would take you less than 30 mins to do so. it would probably take longer waiting for someone more knowledgeable to answer you and give a solution to the update problem.

did you try typing the dpkg --configure -a in the terminal already?

> 
  dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package. If -a  or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

              Configuring consists of the following steps:

              1. Unpack the configuration files, and at the same time back  up
              the  old  configuration  files,  so that they can be restored if
              something goes wrong.

              2. Run postinst script, if provided by the package.


this is what it says it does in the manual - for that type

```

man dpkg

```

yeah... i think it's pretty ok to simply follow the instructions given and type it in.

---

