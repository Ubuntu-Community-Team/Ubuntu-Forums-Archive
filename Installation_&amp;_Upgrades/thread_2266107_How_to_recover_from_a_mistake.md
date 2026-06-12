---
title: "How to recover from a mistake"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by mandarpowale on 2015-02-19
Hi ,

I have installed UBUNTU 14.04 LTS and updated all the files as asked by the OS, next I went to AMD's website and downloaded its v14.12 Proprietary drivers. I to used the  amd-driver-installer-14.501.1003-x86.x86_64.run file and it made my system freeze (after executing very slowly for almost 45 minutes). I had to reboot it. Now I've installed Steam and try to do a check for video driver update and it says 'Steam is unable to preform video driver detection on your system'.

How do I reverse the changes that might have happened while installing via the 'amd-driver-installer-14.501.1003-x86.x86_64.run' command.

How do I do the following?


[LIST]
[*][I]The display driver requires POSIX shared memory to be enabled on the system.
[/I]
[*][I]Kernal Sources package is no longer required if Kernel Header package is installed.
[/I]
[*][I]32-Bit packages must be installed for 64-Bit Linux drivers to install or work.
[/I]
[/LIST]

Also How do I install the proprietary drivers properly?

If you need any more info please mention so. 

Thanks in advance.

P.S:- I am using AMD Athlon II X2 260, Asus M4N68T-M LE-V2, 4GB DDRIII Gskill 1333MHz & Asus HD7750-1GD5-V2. (WINE IS NOT INSTALLED)

---

### Post by Renx on 2015-02-19
Did you by chance backup any of the files you modified prior to modifying them?

---

### Post by mandarpowale on 2015-02-19
I did not backup anything , how to do so?

---

### Post by steeldriver on 2015-02-19
Did you just run the installer without arguments, or did you run it in buildpkg mode?

It's  been a while since I messed with the AMD/ATI drivers, but I seem to remember the installer has an unistall option - have you tried running

```

./amd-driver-installer-14.501.1003-x86.x86_64.run --help

```

---

### Post by mandarpowale on 2015-02-19
I just ran the 'amd-driver-installer-14.501.1003-x86.x86_64.run' file, I will run the command you gave.

I have installed my /home on a bigger partition not near the root so when I run your command,


i get amd-driver-installer-14.501.1003-x86.x86_64.run: command not found

I just ran the 'amd-driver-installer-14.501.1003-x86.x86_64.run' file by double clicking on it, I will run the command you gave.

---

### Post by steeldriver on 2015-02-19
To run it with the --help option, you will need to use a terminal and navigate to the location of the file

---

### Post by mandarpowale on 2015-02-19
how to locate the file ? I am not completely familiar with linux filesystem

Just help me do the
 the following :



[LIST]
[*][I]Enable POSIX shared memory. 
[/I] 
[*][I]Ensure that Kernel Header package is installed.
[/I]  
[/LIST]

---

