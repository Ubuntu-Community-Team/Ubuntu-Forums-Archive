---
title: "Next step: full installation"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by ashleyjohnston on 2012-06-02
I am tiptoeing into Linux. I ran a live usb stick. Then I ran a dual boot system from wubi for a while. I now realized that I don't need windows on this machine. I am ready to have a full installation of ubuntu.

Is there a way to do get to a full installation without back up or file loss from ubuntu (I don't care about my windows files.)

Thx everybody.

---

### Post by TheFu on 2012-06-02
Probably not for a beginner.  Any files you want to keep, you need to backup.  I wouldn't trust any migration tool with important files. Backup, backup, backup.  It is pretty easy after all.

Here's some other thoughts [http://askubuntu.com/questions/635/how-to-convert-wubi-install-into-regular-install](http://askubuntu.com/questions/635/how-to-convert-wubi-install-into-regular-install)

If you are comfortable with Linux partitioning and names, then this [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) appears to be the answer you seek.

---

### Post by Frogs Hair on 2012-06-02
Migrating Wubi may be more work than backing up Ubuntu files and using the entire disk in a clean installation. There is just simply more that could go wrong with the migration option. If the migration fails you will need backup anyway.

---

### Post by bcbc on 2012-06-02
Migrating is easy using the script. The only work is to create the partitions. 

Migration doesn't modify Windows or Wubi, it will only migrate to an empty partition. You don't even have to install the grub bootloader to try it out (you can boot it from the Wubi grub menu).

People that say it's difficult or could break things obviously haven't tried it or understand what it does. It's designed for absolute beginners and it's designed to be fool-proof.

---

