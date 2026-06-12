---
title: "Custom Live USB stick with NO persistence"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by arich57 on 2013-02-25
Hi All,

I'm trying to help my girlfriend's family business stop having computer issues. Their employees seem to find every virus,worm, etc and it keeps bring down their computers- causing them to lost business (and me to fix them).

All the employees need to do is have internet for looking up parts and telnet to get to the inventory system. My thought was to build a custom live USB/iso Linux build that would have the printers installed already and then just start firefox directly in kiosk mode. I found a plugin for Firefox that allows for telnet access ([https://addons.mozilla.org/en-US/firefox/addon/bbsfox/?src=search](https://addons.mozilla.org/en-US/firefox/addon/bbsfox/?src=search)). I want to disable any persistences so that if they do get a virus/spyware/etc, all that has to happen is reboot the machine and it's back to the working, original image (almost like you get at a hotel or library).

I have googled around but can't find anything that shows how I can build a custom live boot linux imagine (plenty on how to make USB boot drives WITH persistence, none for disabling it- or I suck at googling). Or even a way to build a linux machine that has no persistences (just want to do a few tweaks to a base Ubuntu live ISO and use that).

Any suggestions or how to do this and make their (and my) life easier?

Thanks for your time and suggestions.

-Aaron
Boyfriend Tech Support Departement

---

### Post by blackbird34 on 2013-02-25
To build a custom live linux image I might suggest Remastersys. Test it thoroughly before you offer it to them and it ought to be fine. 
I would also suggest going with Firefox ESR (Extended Support Release) to avoid new firefox releases breaking your addon before you can find a replacement. 

[www.remastersys.com]("http://www.remastersys.com")

[[Ubuntuforums.org]("http://ubuntuforums.org/showthread.php?t=1967865")[] Remastersys 3.0.2-1 released supporting Ubuntu Lucid up to Precise]("http://ubuntuforums.org/showthread.php?t=1967865")

Regards :)

---

### Post by C.S.Cameron on 2013-02-25
+1 Remastersys for 12.04.2 LTS

---

