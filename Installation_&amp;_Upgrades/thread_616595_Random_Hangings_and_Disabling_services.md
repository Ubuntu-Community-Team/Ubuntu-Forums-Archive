---
title: "Random Hangings and Disabling services"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by Apoorv on 2007-11-18
First of all, my hardware -

Intel Pentium 4 3.00 Ghz with HT
Intel D101Ggc Motherboard
256 Mb DDR RAM 400 Mhz 
ATI Radeon Xpress 200 On board graphics (Which takes about 32 MB of RAM from the 256 MB)


Because of the lack of RAM, I was unable to install from the live CD. Therefore, I installed my system from the alternate text install CD. 

Now it seems that the default system works just fine, without any problems. But as I start configuring (installing new apps, codecs, utilities) I have always been left with a system that hangs randomly, without any reason. Sometimes it runs fine over a period of several hours, at other times it may hang just after startup. It isn't event triggered, my system has hanged without any visible apps running. And it has run fine with about 20 apps running simultaneously. This problem has been there since the time of Breezy Badger, and still exists on Gutsy. It has stopped me from using Ubuntu as my mainstream OS.

Because this problem is not event triggered, I have a feeling that it is due to a startup service. Somebody had a similar problem and asked me to disable a service called powernowd. I did that, but still the problem prevails.

Now for the new problems. 

1) I installed Opera Kestrel (9.5 Beta), uninstalled it, and reinstalled the stable version 9.4. Now it doesn't work.

2) I have tried disabling many services using :
           a) System >> Preferences >> Sessions.
           b) System >> Administration >> Services
    I have no idea which ones got disabled actually, maybe some got disabled, some didn't, but some services which were surely not disabled (as I can see them running in the system tray) are - Network Monitor and Update Notifier.

3) I can't log out/shut down. When I click on the quit button on the top right corner, the system just freezes. Ctrl + Alt + Bckspace works, but Ctrl + Alt + Del doesn't (weird).



I also want to disable every possible service I can, I mean all services which are not necessary. 

Any kind of help would be highly appreciated.

---

### Post by Apoorv on 2007-11-19
Bump.

---

### Post by faktorqm on 2007-12-17
hi,  :KS

try this unistalling "powernowd" package or disabling this, for more information: 
[http://ubuntuforums.org/showthread.php?t=635508&goto=nextnewest](http://ubuntuforums.org/showthread.php?t=635508&goto=nextnewest)
(in spanish)

bye bye!

---

### Post by Sense on 2007-12-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/85370](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/85370) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I got the same problem and reported it here: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/85370](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/85370)
It's not only on one of the comptuers I manage, but at more. Uninstalling powernowd solves the problem.
But this is the first time I hear of this problem with an Intel proccessor. 
The problems I have weren't as complicated and much as yours, but maybe you'r having more trouble than I.

---

