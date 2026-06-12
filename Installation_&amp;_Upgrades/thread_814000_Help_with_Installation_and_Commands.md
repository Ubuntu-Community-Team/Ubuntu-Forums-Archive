---
title: "Help with Installation and Commands"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by Cataleya on 2008-05-31
This newbie to Ubuntu and Linux needs help sorely with installation of drivers and files in generals. Am running 8.04 Edubuntu and finding the installation instruction on many sites refer to earlier versions-- apparently have different tags and options under Synaptic than are available with Version 8.04.  E.g. adding new repositories.  

So I find myself having to resort to terminal mode to install programs with commands that are foreign to me -- to get around the  drive, locate files, etc.  

There are the biggest problems I am having now just getting my laptop 
 to meet basic essential functions.

WIRELESS - Broadcom 4318, AMD 64 processor

 
1.  Have located and downloaded the Windows driver file.  If someone could walk me through installation -- locating the proper directory/library it should be opened in AND the command with proper syntax to unzip it, I would be most grateful.

2.  Adding third party repositories.  I don't find the option to do so under synaptic--how to get the full link off sites to add them.

3.  Adobe.  Need installation instructions.

If anyone can help with any of these problems, I would be most grateful

---

### Post by Partyboi2 on 2008-05-31
> 1. Have located and downloaded the Windows driver file. If someone could walk me through installation -- locating the proper directory/library it should be opened in AND the command with proper syntax to unzip it, I would be most grateful. Have you tried going to "Hardware Drivers" (System>Admin>Hardware Drivers) and check the Broadcom B43 wireless driver box, and reboot? Or if you are wanting to use ndiswrapper with the windows driver then maybe [[COLOR=Blue]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560") will be of use.

> Adding third party repositories. I don't find the option to do so under synaptic--how to get the full link off sites to add them.
You can add 3rd party repositories by opening up "Software Sources" (System>Admin>Software Sources) and clicking on the 2nd tab "3rd Party Software" Or you can also do this through Synaptic by selecting "Settings" at the top and choosing "repositories"

>  3.  Adobe.  Need installation instructions. One way is to go [[COLOR=Blue]here[/COLOR]]("http://www.adobe.com/products/acrobat/readstep2_allversions.html") and choose "Linux"  then "Linux-86 (deb) and download to Desktop. Then double click on the deb package after it has downloaded and install.

---

### Post by zvacet on 2008-06-01
Third party repo you probably want to have is **medibuntu**.To add it to your sources list type this in terminal

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

and after that 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This covers your last question because adobe reader is in medibuntu repo.You will find it in synaptic as acroread.

---

### Post by Pumalite on 2008-06-01
This might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

