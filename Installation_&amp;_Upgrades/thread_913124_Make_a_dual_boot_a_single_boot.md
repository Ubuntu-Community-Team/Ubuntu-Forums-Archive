---
title: "Make a dual boot a single boot"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by antknee869 on 2008-09-07
hi. Currently I have a Vista / Ubuntu 8.04 dual boot. Vista was installed first. I am considering just using Ubuntu. Is there a way to wipe the Vista partition and using the current Ubuntu  install? Or am I looking at a re-install of Ubuntu?
Thanks

---

### Post by listener on 2008-09-07
No reason to reinstall Ubuntu, that I can see.  You may want to access some of your data on the Vista partition before 'wiping' it though.  You can use it NTFS or re-format it and use it for data in Ubuntu.

---

### Post by overdrank on 2008-09-07
> **antknee869 said:**
> hi. Currently I have a Vista / Ubuntu 8.04 dual boot. Vista was installed first. I am considering just using Ubuntu. Is there a way to wipe the Vista partition and using the current Ubuntu  install? Or am I looking at a re-install of Ubuntu?
Thanks

Hi and you can use the live cd of Ubuntu and gparted to remove the partition and resize the Ubuntu partition. Or create a home partition, and whatever you like. :)

---

### Post by antknee869 on 2008-09-07
Ok, so that won't mess up my boot loader of I wipe the Vista partition. That is the only thing I am concerned with really. 
Thanks for the quick replies

---

### Post by men28 on 2008-09-07
It is not bad to have dual boot. You can define in grub starting ubuntu by default after 5 seconds. For this you have modify /boot/grub/menu.lst file.
Change two lines:
default 0
and
timeout 5

Before you modify this file of course make backup copy of it. And in order to modify this file you have root privileges. Do not change anything else in this file and it is good before any operations connected to dual/multiple boot have rescue cd or to have possibility to start ubuntu from cd.

---

### Post by antknee869 on 2008-09-07
Well, my Vista partion is not bootable now. I would just like to get rid of it. But I was just conecerned I would mess up my ability to boot either OS.

---

### Post by men28 on 2008-09-07
If you want there is possibility to repair your Vista installation.

1. Reboot from your Vista installation DVD;
2. Select your language settings;
3. On the next screen click "Repair Your Computer" link;
4. select your windows Vista partition;
5. then select "Command Prompt";
6. then type "chkdsk c: /R";
7. type exit and restart your computer.

---

