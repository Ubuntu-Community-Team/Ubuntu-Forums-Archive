---
title: "Ubuntu on an external hard drive"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by pookerpuff on 2007-07-29
ok well after finally installing xubuntu on an external drive i decided to switch over to ubuntu(do to the fact that xubuntu was giving me some strange dialog boxes with nothing in them),now my only problem is getting the GRUB to install on the external drive and not on my internal drive.when i installed xubuntu i simply changed the advanced settings from hd0 to hdb and it worked perfectly,but this time when i tried it it gave me and error and failed to install properly.when i try booting it gives me GRUB error 15,any ideas how to fix the GRUB?

---

### Post by Circuit99 on 2007-07-29
In  theory you can boot from external hard drive but the problem lies with your system bios.

Your system bios should have option to boot from external hard drive or external usb device or words to that effect.

grub error 15 means file not found

Check the link below: 

[http://orgs.man.ac.uk/documentation/grub/grub_14.html#SEC106](http://orgs.man.ac.uk/documentation/grub/grub_14.html#SEC106)
 

What could of happened is that grub wrote internal drive mbr instead of external mbr.

Boot up with a live CD of Knoppix to see what drives you can mount and see what has been installed.

Solution might be edit Grub, or replace mbr of internal drive, or install grub on external drive. You don't state what you have on internal drive or if you can boot onto internal drive.

If need info on grub check here

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

and this link on repair

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation)

You should be able to recover system, but what has happened?  

BACKUP DATA before decide do alter anything.


Use this link if you want to fix mbr for windows

[http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm)


Post a solution if you get one.


Good luck :guitar:

---

### Post by pookerpuff on 2007-07-30
sorry,on the internal drive im running vista and that boots up fine when i dont have the external drive  connected,which is what i want because i dont want to install the GRUB on the internal drive.

---

