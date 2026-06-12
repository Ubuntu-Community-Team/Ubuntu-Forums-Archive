---
title: "wubi installation error from usb drive"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by improvent363 on 2011-12-07
I used [I]Universal USB Installer from pendriverlinux.com on a 4GB kingston usb flash drive. I have already installed win7 ultimate 64-ver on my PC and wanted to install ubuntu 11.10 along side but couldn't do it [also, tried ubuntu 11,04 live cd but that didn't work either which I also tried on a laptop].  All, I got was bunch of information on a black screen and it just stuck their.

Therefore, I tried installing wubi from the same USb flash drive [by clicking the wubi icon] and it gave me some error [I did not write down what the error was sorry]. However, I do see the ubuntu files on the Local Disk [C:] and on control panel "uninstall programs". But can't run it.

So, is their a trick to fixing this or do I need to uninstall it again and reinstall it?
[/I]

---

### Post by oldtimer7777 on 2011-12-07
Can you install Ubuntu the regular way without using Wubi from a pendrive instead?

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

You could try it that way first. 

> **improvent363 said:**
> I used [I]Universal USB Installer from pendriverlinux.com on a 4GB kingston usb flash drive. I have already installed win7 ultimate 64-ver on my PC and wanted to install ubuntu 11.10 along side but couldn't do it [also, tried ubuntu 11,04 live cd but that didn't work either which I also tried on a laptop].  All, I got was bunch of information on a black screen and it just stuck their.

Therefore, I tried installing wubi from the same USb flash drive [by clicking the wubi icon] and it gave me some error [I did not write down what the error was sorry]. However, I do see the ubuntu files on the Local Disk [C:] and on control panel "uninstall programs". But can't run it.

So, is their a trick to fixing this or do I need to uninstall it again and reinstall it?
[/I]

---

### Post by improvent363 on 2011-12-07
> **oldtimer7777 said:**
> Can you install Ubuntu the regular way without using Wubi from a pendrive instead?

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

You could try it that way first.


No I cannot [used ubuntu 10.04 CD and it didnt work on the PC nor the laptop]

My question is this: why is their a ubuntu folder on the hard drive and uninstall option on program installed menu if wubi wasn't installed properly? Can I not just uninstall ubuntu and retry wubi but this time try the official method of installing wubi?

---

### Post by Rubi1200 on 2011-12-07
Boot to Windows and uninstall whatever is there from Wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F)

Then download the wubi.exe and relevant Desktop ISO; place them in the same folder and run the executable again.

[LIST]
[*]For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
[*]For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)
[*]For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
[*]For 11.10 use [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)
[/LIST]

---

### Post by improvent363 on 2011-12-07
> **Rubi1200 said:**
> Boot to Windows and uninstall whatever is there from Wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F)

Then download the wubi.exe and relevant Desktop ISO; place them in the same folder and run the executable again.

[LIST]
[*]For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
[*]For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)
[*]For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
[*]For 11.10 use [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)
[/LIST]


Okay I will do exactly what you said, however can you tell me which version should I install? I will only be doing web surfing, checking emails, and reading news. So the lightest and most stable will be fine for me.

If this is related to my PC hardware, please let me know so I can tell you my system information!

---

### Post by Rubi1200 on 2011-12-08
If you are looking for something stable, then I recommend either 10.04 or 10.10

However, if you want light then you should go with something like Lubuntu or Xubuntu.

---

### Post by improvent363 on 2011-12-11
> **Rubi1200 said:**
> If you are looking for something stable, then I recommend either 10.04 or 10.10

However, if you want light then you should go with something like Lubuntu or Xubuntu.

It says here that:
The newest kernels have moved the video mode setting into the kernel.   So all the programming of the hardware specific clock rates and  registers on the video card happen in the kernel rather than in the X  driver when the X server starts. [ [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)]

So, can you please tell me which old version of ubuntu [or any other one linux] I should get if I don't want the above situation to happen?

---

