---
title: "dual boot ubuntu 12.04 / win7, ubuntu does not boot anymore, boot-repair paste file"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by ronny-de-winter on 2014-02-07
Tried to recover with boot-repair without result: paste file: [http://paste.ubuntu.com/6889930/]("http://pasete.ubuntu.com/6889930/")

Can somebody help?
What can I do? Is there still hope for recovery?
Is there a way to recover files from the ubuntu system with a recovery linux on usb for example?

---

### Post by Erik1984 on 2014-02-07
The link you gave contains a typo I guess this is the right report: [http://paste.ubuntu.com/6889930/](http://paste.ubuntu.com/6889930/)

Looks like a complex situation as you use Wubi. If you have a linux usb you might try the following:
[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)

You can also try from Windows:
[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_the_Wubi_files_from_Windows.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_the_Wubi_files_from_Windows.3F)

---

### Post by ronny-de-winter on 2014-02-07
No luck so far:

Following the linux usb instructions:
$ sudo mkdir /win
$ sudo mount /dev/sda1 /win
$ sudo mkdir /vdisk
$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
/win/ubuntu/disks/root.disk: No such file or directory
$ ls /win
AUTOEXEC.BAT   CONFIG.SYS    diags   RAMDRIVE.SYS
AUTOEXEC.UP     CONFIG.UP      HIMEM.SYS
COMMAND.COM   COPYUP.BAT    oobedone.flg  

Tried the windows tools as well, but they complain that I need to be administrator while  am administrator ?!

Anybody some ideas what else I can try?

---

### Post by ronny-de-winter on 2014-02-07
ok I had the wrong sda, it was /dev/sda3
Now I can access my files. they are still intact.

However booted with an ubuntu live cd I cannot copy them to somewhere else. PC has no cdrom drive. How can I move the files to a save place?

Can I reinstall wubi and leaving my ubuntu homedir in tact?

---

### Post by oldfred on 2014-02-07
All of wubi is in root.disk. So if you just reinstall, it creates a new root.disk. You may be able to separately backup the data. But at this point if you want Ubuntu it may be time for a fully partitioned install. Wubi is more for an extended trial to see if you like it and easy uninstall, not long term use.

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

