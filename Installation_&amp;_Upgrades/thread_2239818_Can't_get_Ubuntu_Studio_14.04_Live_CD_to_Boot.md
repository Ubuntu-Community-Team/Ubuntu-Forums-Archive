---
title: "Can't get Ubuntu Studio 14.04 Live CD to Boot"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by minstrelstokg on 2014-08-16
Hi all,

A little while back I had taken some updates on my  desktop computer on which I have installed Ubuntu Studio 14.04. I  haven't used the computer in a couple months mostly out of frustration  in researching a cure back then but I've decided to take it on for round  two. I don't know if something happened during those updates that  caused my issue or not but I ended up getting a message about "No init  found. Try passing init= bootarg." I looked around online a bit to see  that it happens from time to time and that one way to fix the situation  is to boot into the Live CD and run a couple of commands from terminal.  I've been screwing around with this for hours tonight and the Live CD  that I have won't boot up but hangs for some reason when I choose the  selection Try Ubuntu Before Installing. Come to think of it, even when I  made the Live CD it never worked properly. I ended up having to step  from 12.04 on up to 14.04 one release at a time to get her running on my  computer. Tonight I've almost exhausted the options as well as my brain  trying to get my CD to boot. Is there anything I should try in  particular in getting my Live CD to work? I've tried quite a few combinations of the different kernel options and it hangs every time. Is there another way to fix my init= bootarg issue from where I'm sitting now? Thanks for listening.

---

### Post by claracc on 2014-08-16
In order to get a working copy to install ubuntu studio, you will have to check various steps:

First of all you will have to download the proper iso image of ubuntu studio 14.04 and burn it to a DVD ( CD capacity in not enough). Please, see: [https://help.ubuntu.com/community/UbuntuStudio/InstallingUbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio/InstallingUbuntuStudio)

Before to burn the .iso download to a DVD, you will check the integrity of the download: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then you will burn the .iso to the DVD, there are different ways depending on the system and program used: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And, at last, you will have to check the integrity of the burned DVD: [https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

---

### Post by minstrelstokg on 2014-08-18
Thanks for the quick reply. I followed these tutorials to the tee over the weekend but still managed to get the same results. Granted I didn't fool around too much with changing any of the kernel parameters but I just can't manage to keep it from hanging.

---

