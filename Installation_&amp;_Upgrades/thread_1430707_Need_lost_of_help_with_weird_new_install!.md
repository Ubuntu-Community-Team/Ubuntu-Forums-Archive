---
title: "Need lost of help with weird new install!"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2010-03-15
I've had a heck of a time with this today. After installing I could not boot. In reading several posts I came to the conclusion that I needed nVidia drivers. I installed v173 nVidia drivers & after a few tries got it to boot. 
But, not somethings didn't work, like Hardware Drivers, Synaptic Package Manage wouldn't search & some software wouldn't open.
I tried to update in terminal* sudo apt-get update*, then *sudo apt-get upgrade* (I did this before installing v173). It says
dpkg: dependency problems prevent configuration of nvidia-glx-173:
 [I]nvidia-glx-173 depends on nvidia-173-kernel-source (>= 173.14.20); however:
  Package nvidia-173-kernel-source is not configured yet.
dpkg: error processing nvidia-glx-173 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-glx-173[/I]
I'm lost!

---

### Post by akand074 on 2010-03-15
Those NVidia drivers are old, go to System > Administration > Hardware Drivers and there should be version 185 there. Though it could be that its failing to update because your using the X server while your trying to update the graphics driver. Try this command:

```
*sudo* /etc/init.d/gdm stop
```

to stop the X server and then update through the command line, and then do: 

```
sudo startx
```

to start the X server again. Just a thought.

---

### Post by GARoss on 2010-03-15
> **akand074 said:**
> Those NVidia drivers are old, go to System > Administration > Hardware Drivers and there should be version 185 there. Though it could be that its failing to update because your using the X server while your trying to update the graphics driver. Try this command:

```
*sudo* /etc/init.d/gdm stop
```

to stop the X server and then update through the command line, and then do: 

```
sudo startx
```

to start the X server again. Just a thought.
Thanks,
```
*sudo* /etc/init.d/gdm stop
```
Screen went to the same black screen when I couldn't boot. Ask for name & PW. Startx booted to desktop. Still, **Administration > Hardware Drivers & Update Manager** don't work.

---

### Post by GARoss on 2010-03-15
Okay. I tried this again & this time booted to *Root*.
Still, Administration > Hardware Drivers & Update Manager don't work.

---

### Post by GARoss on 2010-03-15
[I]george@george-desktop:~$ sudo apt-get update
[sudo] password for george: 

Reading package lists... Done
george@george-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? [/I]

If I say yes it will try to cleanup the failed install of v185 from earlier. It gets to **Removing all DKMS Modules** & stalls - forever!

---

### Post by akand074 on 2010-03-17
Sorry for the delay! The codes I sent you were to bring you to the login screen so you can update from there where your graphics card isn't really in use. Run the same commands you did where it stalled forever in the black screen (you'll be logged in but without a desktop environment) if it works there you can just start the X server again with startx and your good to go.. if it works. Looks like a broken install and its having trouble reinstalling it. I wonder how this problem occurred in the first place

---

