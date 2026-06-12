---
title: "help meeeee please"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by abu3abdalla on 2006-12-26
hi all,


i am using ubuntu 6.10 but last time i saw the screen i had download some software application from add/remove application then the ubuntu ask me for restart the computer after i restart it the computer died 
i mean i cant see the Grub and it tell me that thier is a problem in "" inturupte "" (maybe i wrote it wrong) and i cant write any command 

i think that it cant load the grub but i do not know how to solve this problem so please help me as possible as you can 





thank u all


:confused: :confused: :confused:  relly i am in a big truble


:confused: :confused: :confused: :confused:

---

### Post by raldz on 2006-12-26
an interrupt error is an IRQ error.. a hardware conflict.. try restoring your BIOS in it's default setup or optimal setup.. then if you want to restore grub, follow these steps:

1. Insert the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "sudo grub"
4. type: "find /boot/grub/stage1"  or stage1.5
5. Type "root (hd0,6)", or whatever is the result from step 4
6. Type "setup (hd0)", or whatever your harddisk number is, this will install GRUB in the MBR.
7. Quit grub by typing "quit".
8. Reboot.

---

### Post by Sef on 2006-12-26
Check out [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

