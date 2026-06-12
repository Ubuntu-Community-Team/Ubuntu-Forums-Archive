---
title: "desktop&#65293;cd installation pro. Help!"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by zjcim on 2006-06-01
i get a laptop ibm x24 with a dvd-rom

i downloaded the desktop-cd and burned it

after i boot computer with the install cd ,there are no problems
 

and i click the "install "on the desktop

choose the language time zone and partion the disk manunely

it is ok

but in the process copying files to the hardisk ,pc dead or freeze,no response

i reboot pc again,but installer program crashed when i do same jobs above before entering copying file to the disk .e.g excute  formating the disk

---

### Post by llamakc on 2006-06-01
Huh? You have downloaded an install cd or the livecd?

When most distros are installing you can check on the process with ctrl-alt-f2, -f3, -f4 to find the tty where the logs are being displayed.

Have you tried the auto-partition yet?

---

### Post by zjcim on 2006-06-02
i download the desktop cd ,it have live-cd & install cd

boot pc with this cd ,it will start the pc with live-cd style and will enter ubuntu deskop enviroment the you can choose install the system to the harddisk with "install " program placed  on the desktop

for i want to dual boot :windows xp with C primary logical D and e 

i partion disk with the pqmagic 8.0, i set the swap in the extenions partion after partion E,and set up another two primary partions labled / and /home

so ,wo partion structure is :a primary c with windows xp
                                      a extenion (primary) with logical D logical E logical linux swap
                                      a primary /
                                       a primary /home
and format them

Now i can delete the linux partions with windows xp disk manager tools with no problems ,but after i try to install ubuntu to the disk and the installer program crash (during this ,ubuntu format the partions again),i reboot the pc to windows xp ,and use the windows xp disk manager tools to delete the linux partions to reinstall ubuntu ,something strange happned ,windows not only delete all linux partons when i just delet one linux partion ,but also delete one logical partion :confused: :confused: :confused: :confused:

---

