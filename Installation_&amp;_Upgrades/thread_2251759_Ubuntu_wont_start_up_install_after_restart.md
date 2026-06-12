---
title: "Ubuntu wont start up/ install after restart"
date: 2014-11-06
forum: Installation &amp; Upgrades
---

### Post by marekkoerlemans on 2014-11-06
I tried to install ubuntu inside windows using a DVD, it got me to the screen where i can choose between install and try and then it got me to set up. After that is ask if i want to have ubuntu inside windows, erase windows and ubuntu only or something else. After i chose to imstall inside windows it said it had to restart and when clicked ok it says i have to remove the installation disk.

[problem start] however after i restarted and removed the installation disk it returns to windows, without even asking which i want to choose. How do I solve this?

[specs]
Windows 7 64b - ubuntu 14.04 LTS 64b
installation disk 4,7 gb dvd+rw(the drive and the image are good)

thanks in advance,
Marek

---

### Post by marekkoerlemans on 2014-11-06
Btw, i dont think ubuntu has installed anything.

---

### Post by grahammechanical on 2014-11-06
Was you running Windows when you inserted the Ubuntu DVD? If you installed Ubuntu inside Windows using wubi.exe, then the best advice would be use Windows Add/Remove programs and remove Ubuntu.

Wubi.exe is not longer being developed. It is not supported by Ubuntu developers any more and as very few of the members of the forum are running Ubuntu inside Windows there are very few us us able to give support based upon experience.

Please read this message from the Ubuntu forum staff

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Otherwise, you have to make clear that you installed using the "Install Alongside" option and not the "Install Inside" option.

Regards.

---

### Post by marekkoerlemans on 2014-11-06
I wasnt using wubi, because i already knew it wasnt supported anymore. But the tage litterally said inside windows. But maybe i have tried wubi before so it is already installed, i will check my pc

---

### Post by bcbc on 2014-11-07
If you have used all four primary partitions, then the installer cannot install a regular dual boot, so it offers to install "inside windows" as in with Wubi. It then copies Wubi to the windows start up folder. I guess when they stopped supporting Wubi they forgot to remove this feature from ubiquity (the ubuntu installer).

If this is your issue, then it looks like this: (and the fix is to remove one of your partitions manually, i.e. something else)
[IMG]http://i.stack.imgur.com/WSbMV.png[/IMG]

---

