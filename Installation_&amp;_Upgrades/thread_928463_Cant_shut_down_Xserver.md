---
title: "Cant shut down Xserver"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by InfSauce on 2008-09-24
Hello all, I am new to linux, and I'm having a ball here trying to figure it all out... But anyway, just going to get down to the meat and potatoes.... I'm trying to install the [**[COLOR="Blue"]NVIDIA-Linux-x86-173.14.12.pkg1.run[/COLOR]**]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run") driver for the Geforce 9600 GT graphics card. I been wrestling around with this for a few days now (amongst other things, like desperately trying to get "Eve" to run)... And I'm taking more steps back than forward it seems... I installed the most recent version of Ubuntu, the 8.0 something or other, and I cant get out of the Xserver, I tried the **Cnt-Alt-F1**, as well as **Sudo /etc/init.d/gdm stop**, but in spite of all this, the Xserver appears to remain running in the back ground, because when I try to install the driver using the command prompt, I still get the following error.

>  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Vivaldi Gloria on 2008-09-24
Why don't you install the driver using Hardware Drivers which is available in the system menu > admin. or you can use envy.

If you want to install it manually press esc during boot and choose recovery console which doesn't run X.

---

