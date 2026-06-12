---
title: "a GRUBy situation ! ;)"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by l4z0r on 2006-09-16
a big howdi to ya' all..

ok, here's the deal.

I installed Ubuntu 6.06.1 through the Hybrid CD.
Everything ran fine (if u can define fine as 3 minor problems). The problem occured when the installer restarted the system.
Windows XP just started booting ! GRUB didnt initialize !

HELP!! 
should i try out this in the terminal (if any of the Hybrid CD) :

grub-install dev/sda0

Will it destroy my XP installation ? Or will it just install GRUB and allow me to choose the OSes as usual ? I dont want to lose my XP installation....

---

### Post by raldz on 2006-09-16
1. Insert the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "sudo grub"
4. type: "find /boot/grub/stage1"
5. Type "root (hd0,6)", or whatever is the result from step 4
6. Type "setup (hd0)", or whatever your harddisk number is, this will install GRUB in the MBR.
7. Quit grub by typing "quit".
8. Reboot.

if anything goes wrong, you could always restore XP's MBR setup by inserting the XP bootable CD and boot in recovery/rescue mode and type: C:\> FIXMBR

---

### Post by l4z0r on 2006-09-16
Hey bro,

thanks a lot.. it worked and GRUB was initialized as the Boot Loader.

Now another problem ->

When i select XP, it fails to boot saying this is not the Boot partition or something like that. I have to press C and then select the hda1,6 (the first option) for Windows XP to boot !

Apart from this, Ubuntu and XP can both boot. Now a little help bro'.  :cool:

---

### Post by raldz on 2006-09-16
open a terminal type this:

sudo gedit /boot/grub/menu.lst


then edit the parameters for your Windows XP, specify the right partition.. you said it was hda1?

---

### Post by l4z0r on 2006-09-17
Hey Raldz,

thanks d00d.

Well now, another interesting problem has popped up ](*,) 
When i select the option to boot Dapper, it shows me a Error 17 : (and some message here that i forgot) !


Today, i got frustrated, and i just kept on entering enter and all of a sudden it booted (weird) ! :rolleyes: 

Any help buddy ?

---

### Post by raldz on 2006-09-17
could you post here the content of your GRUB menu.lst? let me see if there are some discrepancy..

---

