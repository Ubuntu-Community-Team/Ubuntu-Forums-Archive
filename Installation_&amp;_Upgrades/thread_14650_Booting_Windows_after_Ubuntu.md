---
title: "Booting Windows after Ubuntu"
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by Kaddo on 2005-02-08
I have Windows running on my master HDD and Ubuntu on the slave.
The slave went up in smoke and now I can only boot on Windows using 
the boot floppy.
How can I fix that?
Helpful suggestions will be appreciated.

---

### Post by anomie on 2005-02-08
What is it you're trying to do? Get back to Windows and nothing else? If so, I believe the command is ```
fdisk /mbr
```

I seem to remember XP having a utility called something like ```
fixmbr
``` as well (from recovery console).

---

### Post by Xian on 2005-02-09
Yeah, if you are using XP then just boot from the install CD, and press the key "R" in the setup to start the restoration console. Select your XP installation from the list and enter a password (if you have one). Enter the command "fixmbr" at the input prompt and confirm. Then just use "exit" to restore the computer.

---

### Post by Kaddo on 2005-02-09
[QUOTE=anomie]What is it you're trying to do? Get back to Windows and nothing else? [/QUOTE]

For now, yes. 
I need something to work with and the environment tells me it has to be Windows.

---

### Post by Kaddo on 2005-02-09
[QUOTE=Xian]Yeah, if you are using XP then just boot from the install CD, and press the key "R" in the setup to start the restoration console. Select your XP installation from the list and enter a password (if you have one). Enter the command "fixmbr" at the input prompt and confirm. Then just use "exit" to restore the computer.[/QUOTE]

Thanks. 
I will do as recommended and report back soon.

---

