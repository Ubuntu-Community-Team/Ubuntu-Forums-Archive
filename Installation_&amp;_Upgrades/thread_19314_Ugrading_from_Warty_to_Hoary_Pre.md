---
title: "Ugrading from Warty to Hoary Pre"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by Recked on 2005-03-11
Hello,

I have another post regarding the loss of screen resolution, but since I am really, really new to gnu/linux I was wondering if perhaps to fix I should just upgrade from Warty as I was able to get 1024X768 resolution.

Is there any documentation out there that I wasn't able to locate while searching that shows new folks like me how to complete this upgrade?

thank you

---

### Post by Gary Powers on 2005-03-11
I upgraded using the instructions at  ..  [http://ubuntuguide.org/](http://ubuntuguide.org/)  ..  (towards the bottom) and have not had problem one using Hoary for about three weeks.  I hope you will have the same success.

Gary

---

### Post by Recked on 2005-03-11
thanks a lot. Giving it a try now and keeping my fingers crossed!

---

### Post by bored2k on 2005-03-11
[QUOTE=Recked]thanks a lot. Giving it a try now and keeping my fingers crossed![/QUOTE]
 I download hoary files, now upgrading... I hope it goes OK :D.

---

### Post by saoday on 2005-03-11
Please help

I just upgraded to Hoary and I cant use synaptic because webmin didn't un-install properly.  


root@computer1 # apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  webmin-apache: Depends: webmin (>= 1.140) but it is not installable
  webmin-core: Depends: webmin but it is not installable
  webmin-inetd: Depends: webmin (>= 1.140) but it is not installable
  webmin-mysql: Depends: webmin (>= 1.140) but it is not installable
  webmin-proftpd: Depends: webmin (>= 1.140) but it is not installable
  webmin-xinetd: Depends: webmin (>= 1.140) but it is not installable
E: Unmet dependencies. Try using -f.

I tried all possibilities dpkg, install -f, and forumed all day.  It just wont go??  
Please help.

---

### Post by Gary Powers on 2005-03-12
Just tried to upgrade my second box to Hoary and have been unable (10PM Mountain time).  There were quite a few files held back. 

Gary

---

### Post by Recked on 2005-03-12
the package updates are still running on my old laptop. Hasn't died yet! I did a clean iso install to one of my desktop machines yesterday with no issue. Very impressed with Hoary so far. Sprung for Crossover and am hoping to be Windows free in a week or so.

Much to learn about linux printing as I am a photographer and scan/print a lot but I am sick of my Windows boxes getting contrantly hung day after day.

---

### Post by bored2k on 2005-03-12
[QUOTE=Recked]the package updates are still running on my old laptop. Hasn't died yet! I did a clean iso install to one of my desktop machines yesterday with no issue. Very impressed with Hoary so far. Sprung for Crossover and am hoping to be Windows free in a week or so.

Much to learn about linux printing as I am a photographer and scan/print a lot but I am sick of my Windows boxes getting contrantly hung day after day.[/QUOTE]
 Yahoo! Just upgraded to Hoary PRE. So far so good.

---

### Post by dolson on 2005-03-12
I decided to take the plunge myself. I should've done it on my laptop first, but oh well. :)

Crossing my fingers. At least I'll have all weekend to fix it if it breaks.

EDIT: Crap. I did the upgrade, but it sure was NOT flawless! Roughly the same as doing an update in Debian - not user-friendly anyhow. I managed to switch to X.org but I don't have my NVIDIA drivers loaded yet. The module didn't seem to want to load.

---

### Post by Recked on 2005-03-12
well unfortunately my hopes for having Hoary on my Toshiba 7020CT are almost gone completely. I have tried a clean install from iso with the resolution getting messed up and being left with only 640X480 and no other choices. I thought perhaps doing the apt-get dist-upgrade might solve the problem but after many hours now of updating the system comes back up in Hoary with the same exact resolution issues.

I guess Hoary is not ready for this laptop or vice versa???

If anyone has any suggestions I would appreciate any and all help.

thnx

---

### Post by mips on 2005-03-12
Have you guys tried manualy editing the /etc/X11/xorg.conf file ?

---

### Post by dolson on 2005-03-12
[QUOTE=mips]Have you guys tried manualy editing the /etc/X11/xorg.conf file ?[/QUOTE]

I'm not sure if you're asking me, but I got mine fixed. There was an update this morning and I dist-upgraded and it's working fine now. My problem was that the nvidia module wouldn't load, and there was a new kernel this morning... I guess someone matched up the wrong versions. :)

[http://ubuntuforums.org/showthread.php?t=19513](http://ubuntuforums.org/showthread.php?t=19513)

Not sure about that laptop thing though.

---

### Post by strawberry on 2005-03-18
I tried the upgrade with the last hoary preview cd this way:

logout from X,
login as root in first terminal,
#killall gdm,
#apt-cdrom add
#apt-update
#apt-get dist-upgrade

I gave the default answer to each question during the upgrade.

The result: after reboot I got at the gdm login screen where my login was succesful but the process stopped at the next step with a blank screen.

So I prefer the clear install to upgrade from now.  :-(

---

### Post by bored2k on 2005-03-18
[QUOTE=Recked]well unfortunately my hopes for having Hoary on my Toshiba 7020CT are almost gone completely. I have tried a clean install from iso with the resolution getting messed up and being left with only 640X480 and no other choices. I thought perhaps doing the apt-get dist-upgrade might solve the problem but after many hours now of updating the system comes back up in Hoary with the same exact resolution issues.

I guess Hoary is not ready for this laptop or vice versa???

If anyone has any suggestions I would appreciate any and all help.

thnx[/QUOTE]
 This has been solving several times on several threads.


Hint > Search button ;) .

---

### Post by strawberry on 2005-03-19
[QUOTE=strawberry]I tried the upgrade with the last hoary preview cd this way:

logout from X,
login as root in first terminal,
#killall gdm,
#apt-cdrom add
#apt-update
#apt-get dist-upgrade

I gave the default answer to each question during the upgrade.
  :-([/QUOTE]

Did I make a mistake at that upgrade process above? Is there anybody who managed to do the upgrade with hoary install cd? Thanks in advance  :)

---

### Post by strawberry on 2005-03-22
"Did I make a mistake at that upgrade process above? Is there anybody who managed to do the upgrade with hoary install cd? Thanks in advance "

There're few days issuing final version of hoary. Please help to clearify this matter...  [-o<

---

