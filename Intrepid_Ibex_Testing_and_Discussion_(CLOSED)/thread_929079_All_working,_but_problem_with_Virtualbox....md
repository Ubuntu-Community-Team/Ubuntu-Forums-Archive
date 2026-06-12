---
title: "All working, but problem with Virtualbox..."
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by RheaHS on 2008-09-24
I can't start my Windows 2000 VM that was working fine before upgrade. Log isn't showing anything, but it gets to "Spawning Session" which I've never seen before and gets stuck on 0% without doing anything. Anyone else had this?

---

### Post by RheaHS on 2008-09-24
OK, I found a basic fix by changing to the open source edition. But however, it worked once before going back to the same problem.

---

### Post by bonsiware on 2008-09-24
I hink you have to recompile modules after a kernel upgrade:
```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by RheaHS on 2008-09-24
I've done that, with the restart command also, and it says it failed, and to use dmesg to explain the reason why.

```
rhea@rhea-laptop:~$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
```

---

### Post by dinxter on 2008-09-24
what error is given when you type 'dmesg' after 'vboxdrv restart'? and does 'vboxdrv setup' compile without errors?

---

### Post by RheaHS on 2008-09-24
what dmesg gives is a load of system stuff, and nothing to do with virtual box in any way. 
vboxdrv setup doesn't work at all. It gives me the commands to be used such as start, restart, etc. 

I've got the gutsy version installed now, and it's working on that, if a little slow. I guess I'll have to wait for an Ibex version to get it going correctly, as the VB forums suggested.

---

### Post by RheaHS on 2008-09-24
I'm thinking it must be an incompatibility with the new kernel version? But if running the recompile command doesn't work, the installation of a different version asks you to recompile as part of it.

---

### Post by dinxter on 2008-09-24
the last lines of dmesg will tell you the vboxdrv setup output, its sequential system stuff. vboxdrv wont give you the setup option if your using the ubuntu ose version, its an option for compiling the modules for the version from the virtualbox website ( the PUEL version ) 
it is most likely a kernel incompatibility as mentioned, the recent virtualbox versions fixed problems stopping the compiling of the modules for the newer kernels used in intrepid. i'd recommend making sure you've got the latest virtualbox version (2.02 i think?) and also removing the ubuntu ose version, it should work fine.

---

### Post by TitanKing on 2008-10-16
Have you tried:

sudo dpkg-reconfigure virtualbox-2.0 

This fixed mine...

---

### Post by bash on 2008-10-16
The issues I encountered was, that if you don't use the open-source version of Virtualbox, provided in the Repo's you will have to reinstall Virtualbox (or more precisely recompile the kernel module) everytime a kernel update comes along. The version provided in the repos uses DKMS to avoid that problem.

---

### Post by pentolino on 2008-10-21
> **TitanKing said:**
> Have you tried:

sudo dpkg-reconfigure virtualbox-2.0 

This fixed mine...

Mine too, I use binary version from Sun/Innotek  repositories; my current kernel is 2.6.24-21-generic 32 bit.
Thank you very much :-)


EDIT: ops, sorry for my off-topic, I came here through google and didn't see this is Intrepid forum. 
Nice to say it work with Hardy too anyway :-)

---

