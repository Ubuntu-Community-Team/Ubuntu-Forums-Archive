---
title: "Windows 7 to Ubuntu"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by ExScientiaVera on 2010-03-05
Hello there, fellas!

So, I just installed Ubuntu 9.10 in a different disk partition than where Windows 7 is currently installed. So, can I just go ahead and format the partition which contains Win7? Won't that compromise Ubuntu's integrity?

Thank you for your time.

---

### Post by wilee-nilee on 2010-03-05
So are you trying to get rid of W7, and you want to assure Ubuntu boots?

---

### Post by ExScientiaVera on 2010-03-05
> **wilee-nilee said:**
> So are you trying to get rid of W7, and you want to assure Ubuntu boots?

Yes. Can I do that safely?

---

### Post by 2uRcJQ34G1 on 2010-03-05
[FONT="Verdana"][SIZE="3"]If you format your windows partition, your windows and all other data on that partition will be **permanently** deleted. Furthermore, it will not compromise anything since everything is deleted. If in doubt while formatting choose the Ext3 filesystem format, since windows uses NTFS.[/SIZE][/FONT]

---

### Post by Post Monkeh on 2010-03-05
> **ExScientiaVera said:**
> Hello there, fellas!

So, I just installed Ubuntu 9.10 in a different disk partition than where Windows 7 is currently installed. So, can I just go ahead and format the partition which contains Win7? Won't that compromise Ubuntu's integrity?

Thank you for your time.

depending on where your bootloader is installed it may affect your ubuntu booting, but it won't damage it. you may have to boot using a live cd to restore grub so make sure you have an ubuntu cd handy just in case.

while it shouldn't affect your ubuntu install it's always a good idea to back your important documents up just in case anything goes wrong.

---

### Post by wilee-nilee on 2010-03-05
> **Post Monkeh said:**
> depending on where your bootloader is installed it may affect your ubuntu booting, but it won't damage it. you may have to boot using a live cd to restore grub so make sure you have an ubuntu cd handy just in case.

while it shouldn't affect your ubuntu install it's always a good idea to back your important documents up just in case anything goes wrong.

This is correct, and here is a link to a grub2 wiki step 11 is what you made need.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by Post Monkeh on 2010-03-05
> **wilee-nilee said:**
> This is correct, and here is a link to a grub2 wiki step 11 is what you made need.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

yes sorry i forgot to mention - there are loads of tutorials for restoring grub - but make sure you're reading one for grub2.

it's pretty easy to restore if you have to, don't get put off.

---

### Post by ExScientiaVera on 2010-03-05
Very well then, I've gathered all the information I need. Thank you for your time.

---

### Post by 2uRcJQ34G1 on 2010-03-05
Please mark this thread as SOLVED. Cheers.

---

