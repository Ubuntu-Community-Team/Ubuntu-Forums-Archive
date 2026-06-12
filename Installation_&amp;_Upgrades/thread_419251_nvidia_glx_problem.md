---
title: "nvidia glx problem"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by barath on 2007-04-22
I installed NVIDIA-Linux-x86-1.0-7184-pkg1.run  by

  sudo sh ./NVIDIA..........


then again started my xserver

   /etc/init.d/gdm start
  
gui started but in the nvidia glx settings found this error

 The OpenGL extension 'GLX' is not supported by
the X server or there was a problem retrieving
GLX information from the X server.

what to should i do to set it right ... how should i configure my xserver for glx
     


pls help 

thank you in advance

---

### Post by jdong on 2007-04-22
It is recommended to install NVIDIA drivers from the repositories. Start Restricted Manager via System->Adminsitration->Restricted Manager, then check the checkbox for NVIDIA drivers.

---

### Post by barath on 2007-04-22
i added the following code

Section "Extensions"
Option "Composite" "disable"
EndSection
   	
then the error went away


but know when i installed beryl

 sudo apt-get install  beryl emerald emerald-themes 

it installed it 
but when i typed beryl-manager 

the toolbox popped but i could not find any visual enhancements

---

