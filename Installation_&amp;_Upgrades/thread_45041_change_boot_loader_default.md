---
title: "change boot loader default"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by chasesjr on 2005-06-28
Can I change the defaut in the boot loader from linux to winxp?     If so would you please explain how or lead me to help for same.

   Thanks much

   Chas

---

### Post by mingus on 2005-06-28
Open the file /boot/grub/menu.lst in a text editor.   Find the section titled "default num" and the parameter "default" . . . its value is probably set to 0.

Look down the file to the first boot stanza, which is probably Ubuntu.  Count the stanzas to Windows, replace the default value above with this number.  Now go back down to the stanzas and except for Windows, remove the line "savedefault."  Save the file.  That's it.

Probably wise to create a backup copy of the file before doing the edits.

---

### Post by apollo2011 on 2005-06-28
[QUOTE=chasesjr]Can I change the defaut in the boot loader from linux to winxp?     If so would you please explain how or lead me to help for same.[/QUOTE]

An easier way to do it would be to install Grubconf.  You can get the file [here](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb) .  Once you are done downloading, start a Terminal window and find the directory you saved it to, and type "sudo dpkg -i grubconf_0.5.1-4ubuntu2_i386.deb"  This will install the program.  When it is done installing, type "sudo grubconf".

---

### Post by chasesjr on 2005-06-28
[QUOTE=mingus]Open the file /boot/grub/menu.lst in a text editor.   Find the section titled "default num" and the parameter "default" . . . its value is probably set to 0.

Look down the file to the first boot stanza, which is probably Ubuntu.  Count the stanzas to Windows, replace the default value above with this number.  Now go back down to the stanzas and except for Windows, remove the line "savedefault."  Save the file.  That's it.

Probably wise to create a backup copy of the file before doing the edits.[/QUOTE]
 I can open the menu.lst in the text editor , but it wont allow me to change anything , do i need administrator privelege and if so how do get priveleges?

---

### Post by crummer32 on 2005-06-28
sudo gedit /boot/grub/menu.lst

that should do it

---

### Post by manicka on 2005-06-28
try using 

sudo gedit /boot/grub/menu.lst

---

### Post by manicka on 2005-06-28
Another easy way is to copy the entry for the windows partition to the top of the grub entries menu list. It will then appear at the top of the grub menu and become the default

---

