---
title: "Trouble installing 32bit 14.04"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by irongolem0982 on 2014-10-27
hello everyone i am new to ubuntu and my first install went pretty well. but installing it on my second computer is a different story...

i used unetbootin to load the 32bit ubuntu iso to a flashdrive then i switched computers and booted it. it took about 2 minutes in the unetbootin screen then it switched to the ubuntu logo. i chose my language, selected install alongside, then i allocated exactly 20 gb for xp and the same for ubuntu. the resize took about 10 mins then the disk usage stopped (the flashdrive was still blinking) and it went to the desktop with a mouse and a bar at the top. then about 10 mins later the mouse went to a normal mouse. then the bar dissapeared. now all i have is a desktop with a mouse that does not move. 

my computers specs are:
2.4ghz intel pentium 4
ati graphics card (not sure what model)
256 mb ram (was planning to upgrade after the install)
40 gb hdd
other OS(s) windows xp pro 32bit

im confident I will get some answers!!!
Thanks in advance
David

---

### Post by grahammechanical on 2014-10-27
You should have upgraded the RAM before trying to install. Minimum system requirements

> 
[LIST]
[*=left]700 MHz processor (about Intel Celeron or better)
[*=left]512 MiB RAM (system memory)
[*=left]5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
[*=left]VGA capable of 1024x768 screen resolution
[*=left]Either a CD/DVD drive or a USB port for the installer media
[/LIST]


But Ubuntu uses the Unity user interface and the system requirements then become

> [COLOR=#333333][FONT=Ubuntu]* 1000 &#924;Hz processor (about Intel Celeron or better)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]* 1024 MiB RAM (system memory)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]* 3D Acceleration Capable Videocard with at least 256 MB[/FONT][/COLOR]


[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

And we have not yet got to the video adapter. Can it do hardware 3D video acceleration? In a Ubuntu live session open the terminal and run 

```
/usr/lib/nux/unity_support_test -p
```

You need to see something like this

> Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


My advice is to examine Xubuntu or Lubuntu as alternatives. But upgrade the RAM first.

Regards.

---

### Post by irongolem0982 on 2014-10-27
well that explains it somewhat. thanks for the reply. 

the video card can definitly do 3d video accel (i have previously used this card to play starcraft and portal 2)
i cant open terminal :(   i tried ctrl + alt + t and nothing happened, the mouse moves about 10 seconds AFTER i physically move it and there is no bar thingy at the top or a launcher.

my ram upgrade is at a halt because of where it is placed on the computer it is impossible to get to without a full teardown. 

i have concluded i am just going to go back to windows (as i have a computer with ubuntu that is already fulfilling my needs) so does anyone know how i should get it back to windows? has it already messed with the bootloader? do i need to remove the ubuntu partition?  do i need to get out my disks and do a format?

i was hoping to use ubuntu in place of windows xp (as it is out of date)

what is lubuntu and xubuntu? do they still have a user interface? can i still use all the same programs?

thanks
David

---

