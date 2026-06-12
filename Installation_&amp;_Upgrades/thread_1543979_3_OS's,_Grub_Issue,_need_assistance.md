---
title: "3 OS's, Grub Issue, need assistance"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by spine5 on 2010-08-01
I now have a new problem. I am able to boot into Ubuntu and my other operating systems, however, I was only able to boot by adding "rootdelay=120" through the Grub config. If I don't, I get the following error:

```
Gave up waiting for root device. Common problems:
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missingm odules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/myuuidhere does not exit. Dropping to a shell!

Busy box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)

(initramfs)
```This does not happen if I add the rootdelay, however, it increases my boot time considerably (often longer than 120 seconds, as would normally be expected by "120"). Is there any other workaround for this?

---

### Post by oldfred on 2010-08-01
Post this as it will tell us about your system. Do you have some removeable drives that the BIOS puts in before the first drive?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by spine5 on 2010-08-02
I now have a new problem. I am able to boot into Ubuntu and my other  operating systems, however, I was only able to boot by adding  "rootdelay=120" through the Grub config. If I don't, I get the following  error:

```
Gave up waiting for root device. Common problems:
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
 - Missingm odules (cat /proc/modules; ls /dev)
 ALERT! /dev/disk/by-uuid/myuuidhere does not exit. Dropping to a shell!
 
 Busy box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)

(initramfs)
```This does not happen if I add the rootdelay, however, it increases my  boot time considerably (often longer than 120 seconds, as would normally be  expected by "120"). Is there any other workaround for this?

---

### Post by oldfred on 2010-08-02
I would check log files to see what device is very long or repeatly trying to load and then gives up after 120 sec.

System, Administration, Log File Viewer
  Check messages, but I look at all of them.

---

