---
title: "Grub Error After Updating to Windows 8.1"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by Cyb0rgz on 2013-10-24
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]All,
[/FONT][/COLOR]
[SIZE=3][FONT=arial][COLOR=#333333]I have Laptop which dualboots windows 8 and ubuntu 13.10 for more than 4 months. There is no problem so far. I have got a update for windows 8 i.e., Windows 8.1 Update and Updated the system.[/COLOR]
[COLOR=#333333]After updating to Windows 8.1, GRUB Menu is not displayed. After Powering on system directly booted into windows. On Changing the Boot order to Ubuntu, i got below error
[/COLOR]
error: unknown filesystem 
grub rescue>[/FONT][/SIZE]

[SIZE=3][/SIZE][FONT=arial][COLOR=#333333]I guess there is some problem in GRUB. I have few questions,
[/COLOR][/FONT][SIZE=3]
[/SIZE][/SIZE]
[LIST=1]
[*][SIZE=3][FONT=arial]I Assume, there is no problem with Windows 8.1 Bootloader, so Ubuntu Bootloader need to be repaired. Please confirm.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]How to fix this GRUB Issue?? (I am unable to boot into Ubuntu13.10. Am i need to use live CD?) Please guide me in step by step.[/FONT][/SIZE]
[/LIST]

---

### Post by oldfred on 2013-10-24
On update Window restored its defaults. Not sure if then it did something to partition table. Was this a reinstall that would rewrite BIOS partition table? Windows often does not see Linux partition and does not include them in your update to partition table. 
Often testdisk can restore missing partition table if that is the issue.

       sudo parted /dev/sda unit s print

      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by jared2 on 2013-10-24
I had the same issue on updating to 8.1, I'm not sure what the upgrade process did, but it broke it.  I ended up using the Ubuntu Boot Repair CD ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)), option 1.1.  It's a live CD that starts the Boot-Repair program automatically. It worked for me.

---

