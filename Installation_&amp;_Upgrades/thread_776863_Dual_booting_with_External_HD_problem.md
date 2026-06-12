---
title: "Dual booting with External HD problem"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Mohamed Fahim on 2008-05-01
Hi Guys,
  I have windows xp professional and Ubuntu Hardy heron installed in Internal Hard disk i tried installing Mint Linux in my External HD it installed fine now the problem is whenever i start my computer it first seeks whether external hard disk is on if not it shows Error when i switch on my external hard disk and start my computer it shows my external hard disk grub loader which has only Ubuntu Hardy heron and Mint Linux not my windows xp now i want to boot it from internal hard disk how to do it please let me know.

---

### Post by martrn on 2008-05-01
Here is the communtiy ubuntu documentation telling you how to reinstall grub.  [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

From the Section Where it says **Backup, Repairing and Reinstalling GRUB**

You can do it from the Command line and your ubuntu rescue CD by the following,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd1,0)". Use whatever your computer spits out for the following lines.
6. Type "root (hd1,0)", or whatever your harddisk + boot partition numbers are for Ubuntu.
7. Type "setup (hd1,0)", ot whatever your harddisk nr is.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

It might be best to remove your external removable drive while installing grub to the master boot record of your internal drive.

---

### Post by confused57 on 2008-05-01
When you type "find /boot/grub/stage1" from the live cd, as
martrn suggested, you'll probably get something like:
```
root (hd0,1)
root (hd1,0)
```

To reinstall Hardy's grub to the internal drive's mbr, you'll need to do:
```
root (hd0,1)
setup (hd0)
quit
```

Then you can add a configfile entry to boot Mint from Hardy's grub boot menu:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Your Mint entry would be something like:
```
title  Linux Mint
configfile (hd1,0)/boot/grub/menu.lst
```

---

### Post by Mohamed Fahim on 2008-05-01
Hi guys thank you verymuch it solve my problem thank you so much man

---

