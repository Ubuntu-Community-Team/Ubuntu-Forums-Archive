---
title: "Google Earth Installation problem"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by Sairin_Lote on 2008-01-07
I copy/paste from my console :

> sairinlote@gnu-dawn:~$ chmod +x GoogleEarthLinux.bin
sairinlote@gnu-dawn:~$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.2.205.5730..............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!


what's the matter, i don't even have AMD cpu :mad:

---

### Post by luisromangz on 2008-01-08
There are packages for Google Earth in medibuntu's repository. You might want to give those a try.

---

### Post by Sairin_Lote on 2008-01-08
yay!!! thanks it worked!!

i downloaded the repositeries from here : [https://help.ubuntu.com/community/Medibuntu#head-8c36e7d1cd435ccce98b66280d6bd2bd664b5de9](https://help.ubuntu.com/community/Medibuntu#head-8c36e7d1cd435ccce98b66280d6bd2bd664b5de9)

and then i downloaded google earth from here :
[http://packages.medibuntu.org/pool/non-free/g/googleearth/](http://packages.medibuntu.org/pool/non-free/g/googleearth/)

thanks a lot :)

---

### Post by fcigoi on 2008-01-27
I tried both ways, i.e. from Google Earth's website binary and from medibuntu's repositories and the installation worked both times but....when I try to start the program the Xserver crashes and I get the following message in syslog :

Jan 27 18:04:21 *****-desktop01 gdm[17334]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

Does anyone know the reason ?

---

