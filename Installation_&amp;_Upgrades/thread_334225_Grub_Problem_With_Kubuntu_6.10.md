---
title: "Grub Problem With Kubuntu 6.10"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by johnno56 on 2007-01-08
I have 2 hard drives. 200gb SATA (windblows xp pro) and 8gb IDE (Kubuntu).

I have just installed Kubuntu 6.10 on the 8gb IDE drive without a problem.

Restarted PC as per request of Kubuntu installation.

PC rebooted and started up Windblows without giving me the choice of which system to start.

Looks like Grub did not / would not write to HD0.

This is not my first time at using Linux. I have dabbled with Redhat, Fedora, Mandrake and ubuntu. In all cases of installation there were no problems with grub. But this is the first time that I have installed Linux with a SATA and an IDE drive.

(NB: Both drives are configured as "master" on there own channel)

Any suggestions / assistance would be greatly appreciated.

Regards

J

---

### Post by kebes on 2007-01-08
You could boot into the LiveCD and take a look at the file "/boot/grub/menu.lst" on your Linux partition. It's possible that because each drive is a "master", GRUB was only installed to the master boot record (MBR) of the 2nd hard drive.

You can edit that file to make some changes but I think you'll have to use the program "grub" or "grub-install" in order to install GRUB to the correct hard drive MBR. For instance:

grub-install /dev/sda


Check out the grub documentation:
[http://orgs.man.ac.uk/documentation/grub/grub_3.html](http://orgs.man.ac.uk/documentation/grub/grub_3.html)
[http://www.die.net/doc/linux/man/man8/grub.8.html](http://www.die.net/doc/linux/man/man8/grub.8.html)
[http://www.die.net/doc/linux/man/man8/grub-install.8.html](http://www.die.net/doc/linux/man/man8/grub-install.8.html)

---

### Post by bulldog on 2007-01-08
Just make your IDE drive the boot hdd,map your windows and your clear to go.
Mapping windows like this```
gksudo gedit /boot/grub/menu.lst
```
This opens your menu.lst in an editor,now change the windows entry like this one [the mapping hdd rules]
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

---

### Post by johnno56 on 2007-01-10
Thankyou Kebes and Bulldog for responding so quickly.

Since I was attempting a fresh install, I went with Bulldogs suggestion.

Modified Bios to boot to the IDE drive. Installed Kubuntu on the IDE drive. Kubuntu mapped the Windblows (SATA) drive. And grub did the rest.

Thanks again guys. All is now ok.

Regards

J

---

