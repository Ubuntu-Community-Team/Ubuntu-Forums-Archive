---
title: "boot-repair not working"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by matttie.evans on 2013-12-23
Bit of a novice...

Windows 7 with Ubuntu 12.04 worked fine until I needed to reinstall Windows 7 thanks to a trojan leaving large holes in it. Now it will not boot to Ubuntu.

Tried online advice - boot in to live version (USB) and running Boot-Repair but no luck.

[http://paste.ubuntu.com/6622943/](http://paste.ubuntu.com/6622943/)

Any advice gratefully received.

Thanks

---

### Post by ajgreeny on 2013-12-23
Your problem is that you installed Ubuntu using wubi, ie, the Ubuntu OS inside your original windows OS as a virtual disk, which now, having reinstalled windows, is probably gone for good.

If you didn't reformat the whole windows system when you reinstalled, which may not even be possible (I don't have windows so don't know about that) it is just possible that you may find a large file somewhere in the new windows called root.disk which you can mount in Ubuntu (live DVD if necessary) and retrieve any files you need.

See [http://ubuntuforums.org/showthread.php?t=1564156](http://ubuntuforums.org/showthread.php?t=1564156) for more info on this and see if any other pages at the search facility here help:-
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=mount+wubi+disk+file&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=mount+wubi+disk+file&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by oldfred on 2013-12-23
It looks like you created a 99GB partition as sdb3 for wubi. Only because you had a separate partition did wubi not get overwritten.

But better to have Ubuntu installed to a partition not as wubi. Wubi does have a limit of 30GB so you cannot even use the entire 99GB. the last supported version of wubi is 12.04. Wubi does not work with gpt partitioned drives which all new UEFI systems use.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[URL="https://help.ubuntu.com/community/Wubi"]https://help.ubuntu.com/community/Wubi

      [/URL]
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    

       HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by fantab on 2013-12-23
When you re-installed Win7 you lost the files needed to 'boot' Wubi-Ubuntu, as they were in the previous Win7 install. With Wubi you were NOT truly dual-booting, but running Ubuntu as a windows program from inside Windows.  
I guess the 'trojan' was a blessing in disguise. 
I think its time you moved on and away from WUBI. The quote in the above post says it all.

Install Ubuntu directly to it own partition, and I recommend that you do clean and fresh install.
If you have data to rescue from earlier Wubi-Ubuntu then you can do so easily using Ubuntu Live DVD/USB, ie, if you still have 'uncorrupted' wubi partition.

---

### Post by hakuna_matata on 2013-12-23
I think that Boot-Repair doesn't create a menu entry for Ubuntu in "Windows Boot Manager". You can take a tool called [EasyBCD]("http://neosmart.net/EasyBCD/") to do so. [Here]("http://media.cdn.ubuntu-de.org/wiki/attachments/01/45/EasyBCD-Setting.png") is a picture which entry is necessary. It is entry #2. Maybe "Drive" is "E:\" for your Windows system. Don't forget to select a timeout greater zero if you want to see this menu.

---

### Post by matttie.evans on 2013-12-23
Thanks everyone. I'll reinstall without wubi as suggested. I was just trying to get around this if possible, but no loss of data.

Thanks again

---

