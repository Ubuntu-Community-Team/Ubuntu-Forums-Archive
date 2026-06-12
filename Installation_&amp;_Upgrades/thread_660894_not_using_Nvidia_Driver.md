---
title: "not using Nvidia Driver"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by ShutItDown on 2008-01-07
can someone run me through how to reinstall my nvidia driver? it is not using it when i try to enable Extra Desktop Effects.

---

### Post by codesplice on 2008-01-07
The easiest way to handle the nvidia driver would likely be through Envy.

If you don't have it, get it at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ShutItDown on 2008-01-08
ehh i tried using that. when i unpacked it something said it was not supported because its proprietary.

---

### Post by PmDematagoda on 2008-01-08
Does the error prevent you from installing the driver?

---

### Post by ShutItDown on 2008-01-08
i clicked download envy and when i doubled click it, it would not let me use it. i know the graphics card is newer and isnt supported. but i dont know what else to do. im new to ubuntu so im this is very difficult. oh and on the site sudo envy --uninstall-all said its not a supported command.

---

### Post by PmDematagoda on 2008-01-08
Ok, try installing the Nvidia driver in a different way. Open the Restricted Drivers Manager in System>Administration>Restricted Drivers Manager, then select your card to be used, that should fix the problem.

---

### Post by ShutItDown on 2008-01-08
i just tried that and when i click enable it says enable accelerator then i get this

The software source for the package

   nvidia-glx-new

 is not enabled.

---

### Post by PmDematagoda on 2008-01-08
Could you post what Nvidia card you use?

---

### Post by ShutItDown on 2008-01-08
the ones we use here in class are 8400 GS cards.

---

### Post by codesplice on 2008-01-08
> **ShutItDown said:**
> i just tried that and when i click enable it says enable accelerator then i get this

The software source for the package

   nvidia-glx-new

 is not enabled.

Check your repos.  I don't remember which repo needs to be enabled to load this driver, but it's evidently not enabled.

---

### Post by ShutItDown on 2008-01-08
im sorry,, Repos? lol

---

### Post by PmDematagoda on 2008-01-08
Repos=Software repositories

Post your sources.list file using:-
```
cat /etc/apt/sources.list
```

---

### Post by ShutItDown on 2008-01-09
good news, i recieved a LINUX FORMAT magazine and with it came ubuntu disk with butt loads of updates and packages. It has a Nvidia package 1 for x86 and package 2 for 64 bit pc's. im reinstalling ubuntu as we speak because i chopped it all up trying to fix it and forgot the root password. i feel this is will fix my problems. i have to do some A+ test questions then i will be back on to update.

---

### Post by PmDematagoda on 2008-01-09
Good luck, I hope the reinstall goes well:).

---

### Post by oldsoundguy on 2008-01-09
An FYI .. I just installed a 5500 PCI (no AGP) in an old box (replaced an ATI that I could not get to work other than in basic 800 x 640 and NO pivot) .. 
I used Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Just click install and go grab a cup.
Come back and everything is ready!
The program is SUPPOSED to do ATI also, but it GOES TO THE SOURCE ( ATI) to get the drivers and supporting software.  G.I.G.O.!!  That is why the ATI card did not work as it was supposed to!
The software at nVidia is valid.

---

### Post by ShutItDown on 2008-01-11
the update cd wont auto run on this pc at school. like it wont tell me new updates are available. and when i go to run this file 'NVIDIA-Linux-x86_64-100.14.19-pkg2.run' it wont run for some reason. THAT IS ALL I NEED TO GET IT TO WORK AND IT WONT RUN IT. everything is fine on my laptop but once i put it on here its all messed up. why wont it run that file?

---

### Post by ShutItDown on 2008-01-11
i dont think its letting exe run. anyone know why?

---

### Post by PmDematagoda on 2008-01-11
Perhaps you will have to execute it manually. If you want to run the installer you will have to first kill the GUI using:-
```
sudo /etc/init.d/gdm stop
```
and execute the installer using:-
```
sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run
```

After that is done you can restart the GUI using:-
```
sudo /etc/init.d/gdm start
```

---

