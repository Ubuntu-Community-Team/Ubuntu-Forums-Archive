---
title: "Ubuntu xserver problemS"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by m4n40 on 2008-02-04
Hi all,  i am complete noob to ubuntu i installed it 3 days ago and i spend the following days to try to make it work propely.. Here are my problems, first of all after i install and configure xserver, i reboot and the mouse freeze, it a very basic USB logitech mouse, i have try evry single configuration possibility all the same result.. Second problem is that the nvidia driver dosen t work either, after configuration of xserver i reboot and ubuntu tell me that it cannot reconize my graphic card (even though xserver reconized it during the instalation, it a basic geforce 7200) and then run with the default video driver. Very frustatrating i reistalled it 2 times always same issues. So here i am am back to my old windows xp, could any one help me out here i would really like to switch to ubuntu?
Thanks for the help and please excuse my english

---

### Post by Partyboi2 on 2008-02-04
You could use envy to install the nivida driver
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
was your mouse working before you reconfigured xserver?

---

### Post by m4n40 on 2008-02-04
thx for your answer Partyboi2 unfrotunatly i can t reach the adress you gave me. For the mouse yea it was working fine before i configure xserver.

---

### Post by PmDematagoda on 2008-02-04
You can try installing the Nvidia driver the following way:-

1) Boot Ubuntu in Recovery Mode(from here onwards you will be using the CLI).

2) Once you reach the terminal, install the required prerequisites for the Nvidia driver using:-
```
apt-get install build-essential
```

3) After that is done, get the driver using:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```

4) After the driver has been downloaded, execute the installer using:-
```
sh NVIDIA-Linux-x86-169.09-pkg1.run
```

5) After the installation is successful, configure the X-Server using:-
```
dpkg-reconfigure xserver-xorg
```

6) Then try out your new settings in root mode by entering:-
```
startx
```
or restart Ubuntu and then check it out on normal mode. Restart Ubuntu with this:-
```
reboot
```

---

### Post by m4n40 on 2008-02-05
Wow 
Thanks a lot for that very effective and clear answer PmDematagoda. It s indeed working. Someone should definitely do a clear post about the ubuntu and nvidia issue cause it s seems that a lot of people are getting trouble with it and i couldn t find anything clear tutorial (for noob) on the web..I still have that mouse problem tho, it s a classic logiteck usb mouse and once i reconfigure xserver it s not working anymore.. Any idee where that problem could come from?

---

### Post by m4n40 on 2008-02-05
Ok i fixed the mouse problem by repeating the driver installation without reconfiguring xserver afterward. So just on last question(at least for this post) Is my nvdia driver working proply even tho i didn t re run the xserver reconfiguration? 
Thx all for your help ~

---

### Post by PmDematagoda on 2008-02-06
If you allowed the Nvidia installer to configure the X-Server automatically or if you left your old xorg.conf intact then you will not need to reconfigure the X-Server again.

---

### Post by tghe-retford on 2008-03-27
PmDematagoda, your walkthrough worked perfectly for me. Thank you very much. :)

---

### Post by PmDematagoda on 2008-03-27
> **tghe-retford said:**
> PmDematagoda, your walkthrough worked perfectly for me. Thank you very much. :)

I have to warn you, the driver you installed is version 169.09 whereas the latest version is 169.12, so I would recommend that the wget command be:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```
so that there would be as few issues as possible.

---

