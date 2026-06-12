---
title: "Conflict between Nvidia modules after kernel upgrade"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by BeatBoxRocker on 2006-06-17
I have upgraded my kernel from 386 to k7 but after installing it i noticed that the nvidia-kernel-common package was installed too. If i try to remove this package I must delete the new kernel.

Now X doesnt start due to this error: API Mismatch the Nvidia kernel module has the version 1.0-7174 but this X modules has the version 1.0-8756.

I have tried to reinstall the drivers from the Nvidia webpage (8756 & 8762) but after rebooting the computer it seems that the system uses the module from the package nvidia-kernel-common.

How could I fix this? Is there a way to use the Nvidia drivers built module instead of the one in the nvidia-kernel-common package?

Thanks in advance. Saludos!

---

### Post by thom_raindog on 2006-06-17
Did you install the drivers manually or out of the official repos? If they were installed manually I would remove them complete and use
[code]sudo apt-get install nvidia-glx]
to install the ones in the repo.. Might help.. and with dapper they are reallyreally up to date too :)

---

### Post by BeatBoxRocker on 2006-06-17
I installed the drivers manually.  I have tried to use the driver from the repos but it doesnt work too and a new error appears:

Version mismatch detected between the NVIDIA X driver and the NVIDIA GLX module.

X driver version: 1.0-8756
GLX module version: 1.0-8762

Thanks for the fast reply. Saludos!

---

### Post by tseliot on 2006-06-17
Try my script, it should solve your problem:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by BeatBoxRocker on 2006-06-17
Great Script! It have fixed the problem. Don't know how but it worked :)

Saludos!

---

### Post by SkyWasher on 2006-07-31
Thank you TSEliot this got me working too!

---

### Post by pudland on 2007-02-13
Your script worked like a charm!!!!

---

