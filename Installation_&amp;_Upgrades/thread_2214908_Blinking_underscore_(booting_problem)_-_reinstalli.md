---
title: "Blinking underscore (booting problem) - reinstalling ubuntu on laptop with windows."
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by dawid4 on 2014-04-03
I had windows and ubuntu dual boot. I wanted to reinstall ubuntu. Being not well-informed I just removed linux partition from win disc manager (!). Then I encountered windows booting problems which I solved with win install DVD. However, I cannot install any linux distribution from a bootable USB stick - I'm always encountering black screen with blinking underscore. Trying wubi.exe on windows the feedback was "A previous installation of ubuntu detected. Uninstall it before continuing" (I'm not quoting literally, but the sense). But I don't have ubuntu anymore.

I believe I should somehow remove all tracks of linux existence. Is it about registry entries? How can I do it?
My goal is to have dual-boot windows and ubuntu again.

Thank you for your response!

---

### Post by grahammechanical on 2014-04-03
When you first installed Ubuntu did you do so using Wubi.exe? Then as the error message says you should first use something like Windows Add/Remove programs to remove it. If your Windows OS is Windows 8, then you should not use Wubi.exe. It is incompatible with Windows 8.

Can you run a Ubuntu live session? Is that when you get the black screen with the blinking underscore? Or are you able to install but get the black screen with the blinking underscore when you reboot? It does make a difference to the help we can give.

Regards.

---

### Post by dawid4 on 2014-04-04
Thank you for your response.
I have windows 7 and I have removed ubuntu from add/remove programs which did not solve the problem. I'm not sure if I used wubi.exe while installing ubuntu for the first time.
The blinking underscore appears before even displaying ubuntu icon - installation process does not begin.

I guess there must be some track of previous ubuntu somewhere (maybe in the registry entries).

Regards.

---

### Post by oldfred on 2014-04-04
What video card/chip?

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[URL="http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it"]
[/URL]

---

