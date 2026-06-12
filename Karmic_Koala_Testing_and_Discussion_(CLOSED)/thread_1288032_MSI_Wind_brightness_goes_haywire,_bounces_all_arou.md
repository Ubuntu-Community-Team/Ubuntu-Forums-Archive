---
title: "MSI Wind brightness goes haywire, bounces all around"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bandofmercy on 2009-10-10
has anyone else had this problem?  i can't find any evidence of it.  It begins at the gdm for me with the notification basically stuck in the upper right bouncing back and forth a notch... sometimes i can make it go away by quickly using my keyboard function and dimming keys to change it.  then it stops.  sometimes I can't, including right now after the last update i did.  it isn't just the flickering screen... it really slows my typing down.  this took me like 5 minutes.  any ideas?

---

### Post by skeve on 2009-10-11
Same problem here, exept the system is not that slow.
And I can stop flickering after changing brightness with hardware buttons several times

---

### Post by sealskej on 2009-10-11
Same problem here. :(

---

### Post by go7Ul1ai on 2009-10-11
Same problem here, when this occurs I can't click buttons or anything so I can't shut down my PC etc. This has been happening to me since 8.04, I've filed a bug report on it but no one wants to fix it for me.

Lee

---

### Post by discordian on 2009-10-11
Can confirm. You can "stop" it by killing the gnome-power-manager process, and restarting will _sometimes_ solve the problem. Funnily enough, using for example powersave to suspend it to RAM and then waking it up again did stop the flickering, too.

discordian

---

### Post by robbieo11 on 2009-10-11
go into power management and set display brightness for ac powerto lowest setting  that did for me

---

### Post by izi on 2009-10-12
confirm here too

I only have to open the main menu (ALT+F1) and this stops. any ideas?

---

### Post by kuzniarpawel on 2009-10-13
Confirmed it constantly changes brightness on MSI Wind U100. Responsiveness is quite good. Launching different apps sometimes solves the problem for example: launching terminal - but this behaviour is not reproducible.

Killing gnome-power-manager solves the problem.

---

### Post by Hfr on 2009-10-14
[FONT=Arial][SIZE=2]Hello


 I'm currently using Ubuntu 9.10 beta on my [/SIZE][/FONT]   [FONT=Arial][SIZE=2]**Netbook**[/SIZE][/FONT][FONT=Arial][SIZE=2] „MSI Wind U100-1616XP Luxury Edition 0011221-SKU201".[/SIZE][/FONT][FONT=Arial][SIZE=2]


[/SIZE][/FONT]                                  [FONT=Arial][SIZE=2]Therefore  I've got your problem as well :confused:
[/SIZE][/FONT]
[FONT=Arial][SIZE=2] but with 9.04 it had worked out of the box.[/SIZE][/FONT][FONT=Arial][SIZE=2]


[/SIZE][/FONT]     [FONT=Arial][SIZE=2]I suppose you may run in the same problem - what could we do or where to create an open topic?[/SIZE][/FONT][FONT=Arial][SIZE=2]


[/SIZE][/FONT]     [FONT=Arial, sans-serif][SIZE=2][FONT=Arial]Thanks in advance[/FONT] :-)[/SIZE][/FONT]

---

### Post by fog on 2009-10-14
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/415023](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/415023)

---

### Post by Hfr on 2009-10-17
Hello
 

 Thanks for having looked for a solution formerly :) -  I dare say it could be up again :confused:.

  I've this problem never seen using Ubuntu 9.04 but now with Ubuntu 9.10 Beta.
 

 My hardware:
  Netbook „MSI Wind U100-1616XP Luxury Edition 0011221-SKU201" (gekauft 31.3.09)
 

 I 've seen other related topics:
 
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/415023](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/415023)
 [URL="https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/415023"]
[/URL]
 [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/150086](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/150086)
 [URL="https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/415023"]
[/URL]
  Is someone looking after this bugs before Ubuntu 9.10 will finalized soon?
 

  Best Regards from Munich (Germany)

---

