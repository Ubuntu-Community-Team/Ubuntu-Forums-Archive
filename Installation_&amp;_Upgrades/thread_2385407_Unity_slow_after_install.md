---
title: "Unity slow after install"
date: 2018-02-20
forum: Installation &amp; Upgrades
---

### Post by leydar on 2018-02-20
I installed 16.04 on a no-os new novatech laptop. It has an i7, 32gb, Nvidia, 256gb SSD, 1tb HDD. Initially the install hung at the very end at the prompt to restart. I got around this by setting nomodeset and removing fast boot splash from the boot options. When it loaded unity I installed nvidia-current. It works but I have to drag the mouse across the screen and drop down menus are taking seconds to load. I've reinstalled a couple of times to no avail. I've also installed lubuntu which definitely runs faster but I think that's making the underlying problems.

I'll add more specific information when I get to work.

---

### Post by leydar on 2018-02-20
System spec:
[COLOR=#383A42][FONT=Arial]    Ubuntu 16.04.3 as sole OS on a Novatech Elite N1773[/FONT][/COLOR]
[COLOR=#383A42][FONT=Arial]    Linux 4.10.0-28-generic x86_64[/FONT][/COLOR]
[COLOR=#383A42][FONT=Arial]    [/FONT][/COLOR][COLOR=#383A42][FONT=Arial]i7-7700HQ @ 2.80Ghz[/FONT][/COLOR]
[COLOR=#383A42][FONT=Arial]    [/FONT][/COLOR][COLOR=#383A42][FONT=Arial]nvidia geforce gtx 1070[/FONT][/COLOR]
[COLOR=#383A42][FONT=Arial]    [/FONT][/COLOR][COLOR=#383A42][FONT=Arial]    [/FONT][/COLOR][COLOR=#383A42][FONT=Arial]vbios rev: 86.04.56.00.5c[/FONT][/COLOR]
[COLOR=#383A42][FONT=Arial]    [/FONT][/COLOR][COLOR=#383A42][FONT=Arial]    [/FONT][/COLOR][COLOR=#383A42][FONT=Arial]vbios date: 17/11/16[/FONT][/COLOR]
[COLOR=#383A42][FONT=Arial]
Initially it would hang at the final stage where a reboot was solicited. I set nomodeset as a boot option and escaped the reboot prompt to launch Unity. From here I ran:
    sudo apt-get update;
    sudo apt-get full-upgrade;
    sudo apt-get install nvidia-390/384/367/current
lsmod showed nouveau drivers before and nvidia after. With the nouveau drivers xwindows is dog slow and with the nvidia drivers it crashes and displays the login prompt. 

Is there a particular version of drivers that might work? Should I try running a different windows manager or dare I say it distro? It was usable with lubuntu and the standard video drivers for example.


[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-02-20
The first thing to do is fully update the system as at present you are using a 4.10 kernel which is no longer supported so run commands ```
sudo apt update
sudo apt full-upgrade
```
That should update everything including the kernel to 4.13.0-32, I think.

See if that improves things for you; that machine should fly as far as I can see, though I have no experience of nvidia cards, but I wonder with that gtx-1070 card whether a more recent kernel, and maybe even a newer OS, ie 17.10. would run better.

---

### Post by leydar on 2018-02-20
[FONT=Verdana]I have run update/full-upgrade but took the system spec prior to that :) Current kernel is 4.13.0-35[/FONT]
[FONT=Verdana]Using 17.10 leaves me in pretty much the same state with the nouveau drivers. When I install the nvidia the screen flashes on reboot.[/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by leydar on 2018-02-20
Following a suggestion on the Novatech forums I reverted to the nvidia-367 drivers. It seems to be working a treat so far.

---

### Post by ajgreeny on 2018-02-20
Great to know! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

