---
title: "I can not install Ubuntu"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by Celswolf on 2010-10-27
Down after several distributions of Linux (Arch Linux, Ubuntu, Kubuntu, Xubuntu), failure to install any power or run the LiveCD I focus only on one: Desktop Edition Ubuntu 10.10.

In Win XP with Wubi you install on a formatted partition and defragmented without problems, reboot the machine and the Possibility for me to choose Ubuntu at startup.
The problem is here: Ubuntu loading screen and white and 5 points after a while I get this error:
> 
BusyBox v1.15.3 (Ubuntu 1:1.15.3 - 1ubuntus) built-in shell (ash)
Enter 'Help' for a list of built.in command

(initrams) Could not find the ISO ubuntu/install/installation.iso

This could also happen if the file system is not clean because of an oprationg system crash , an interrupted boot process, an impropper shutdown, or unpluggins of removable device whithout first unmounting or ejection it.

To fix this, simply reboot into Windows, let it full start, log, in, run 'chkdsk /r',  then gracefully shutdowm and reboot back into windows
after this you should be able to reboot again and resume the installation.

Try the [B] chdsk / r [/ B] but still with the same problem
PS: Blame the google translator for bad English
------------------------------------------------------------

Despues de bajar varias distribuciones de linux (Arch Linux , ubuntu, Kubuntu , Xubuntu),el no poder instalar ninguna ni poder ejecutar el LiveCD me voy a centrar solo en una sola: Ubuntu 10.10 Desktop Edition.

En Win Xp con Wubi lo instalo en una particion formateada y desfragmentada sin problemas, reinicio la maquina y me da la posiblilidad de elejir Ubuntu en el arranque.
El problema viene aca: carga la pantalla de Ubuntu y 5 puntos blanco y despues de un rato me sale este error:
> 
BusyBox v1.15.3 (Ubuntu 1:1.15.3 - 1ubuntus) built-in shell (ash)
Enter 'Help' for a list of built.in command

(initrams) Could not find the ISO ubuntu/install/installation.iso

This could also happen if the file system is not clean because of an oprationg system crash , an interrupted boot process, an impropper shutdown, or unpluggins of removable device whithout first unmounting or ejection it.

To fix this, simply reboot into Windows, let it full start, log, in, run 'chkdsk /r',  then gracefully shutdowm and reboot back into windows
after this you should be able to reboot again and resume the installation.

Intente hacer el **chdsk /r** pero sigue con el mismo problema

---

### Post by Silent Warrior on 2010-10-27
I'm not sure what you're asking... You start the computer with the Ubuntu-CD in the drive, and...?

---

### Post by Celswolf on 2010-10-27
I choose ubuntu in the boot screen and then a few seconds this message
> 
BusyBox v1.15.3 (Ubuntu 1:1.15.3 - 1ubuntus) built-in shell (ash)
Enter 'Help' for a list of built.in command

(initrams) Could not find the ISO ubuntu/install/installation.iso

This could also happen if the file system is not clean because of an operating system crash , an interrupted boot process, an impropper shutdown, or unpluggins of removable device whithout first unmounting or ejection it.

To fix this, simply reboot into Windows, let it full start, log, in, run 'chkdsk /r', then gracefully shutdowm and reboot back into windows
after this you should be able to reboot again and resume the installation.

---

