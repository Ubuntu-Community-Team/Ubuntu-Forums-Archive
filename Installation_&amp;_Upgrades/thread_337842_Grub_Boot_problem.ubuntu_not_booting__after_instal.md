---
title: "Grub Boot problem.ubuntu not booting  after installing fedora"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by deepbluegene on 2007-01-13
Hi
i have just installed fedora 6. before that i had win xp and ubuntu 6.10 installed and everythin was working perfectly. now after installing fedora i can not boot to ubuntu.there is no entry in boot loader. i know i have made mistake somewhere as i am new to linux.
but now when i searched net for help i found that by editing menu.lst in boot/grub i can add ubuntu to the list but fedora is not allowing me to add any entry.

i used "sudo gedit menu.lst"

message i got that i am not sudoers and incident will be reported. how can i issue command as root to configure menu.lst?

i am currently in fedora. please advise me how to edit grub.
if you need more information please let me know.
please help

thanx

---

### Post by shane2peru on 2007-01-13
Do you know where you Ubuntu partition is located?  Should be hdx,y  - x bieng the harddrive number and y being the partition number.  You don't use sudo with Fedora, you need to use ```
su[code] and then you are in root, and you can [code]gedit /boot/grub/menu.lst
```  when you are done ```
exit
``` that will get you out of the root account.  You should probably backup your menu list before messing with it too much.  Just ```
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` after you have typed su, and that will back it up.

Shane

---

### Post by deepbluegene on 2007-01-15
Thanx for your response.

i have just solved my grub problem.

i did following

boot from ubuntu live cd

mounted both fedora and ubuntu

opened menu.lst from fedora and ubuntu.

copy pasted ubuntu entry from menu.lst of ubuntu to fedora menu.lst

and now boot loader is working perfectly well.

thanx again

---

