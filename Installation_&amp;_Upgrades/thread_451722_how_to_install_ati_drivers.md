---
title: "how to install ati drivers?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by mookieit on 2007-05-22
i have downloaded the latest drivers,and i have no idea how to install them. 

thank you.

BTW,the program "envy" wont run,i get an error "dependency is not satifiable...",just saying this mabey you want me to use this program

---

### Post by myoungf1 on 2007-05-22
Did you get the .run file from the ATI website?

---

### Post by mookieit on 2007-05-23
as i said i downloaded the latest drivers,so yes i did download the .run file,i open it through the terminal,it uncopresses some things,and thats it,it dosnt do anything else....i guess i have to do something else.

---

### Post by myoungf1 on 2007-05-23
Yes next you need to click on the uncompressed files, they are .deb files and install those as well.  there are 5 files if I remember and you need the following installed at least:
xorg-driver-fglrx
fglrx-kernel-source
fglrx-amdcccle

After those have been installed you need to do the following from a terminal window:
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now

After the restart you should be up and running but do the two following in a terminal window to make sure not only the install worked but also if you have direct rendering:
fglrxinfo  (This should show ATI as the OpenGL Vendor)
glxinfo | grep direct (this should show direct rendering as yes)

---

