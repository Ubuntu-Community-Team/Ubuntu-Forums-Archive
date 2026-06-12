---
title: "Ubuntu really slow after installation"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-07-28
I recently installed ubuntu linux ,along with winXp to make a dual boot system, the installation went on smoothly but after 
installation i found that ,ubuntu is really slow . it takes a long time to respond to miouse clicks, graphical menus are really slow.

what could be the reason for this ?
is there any solution for this ?

I had given swap space equal to double the RAM size

---

### Post by overdrank on 2008-07-28
> **sulekha said:**
> I recently installed ubuntu linux ,along with winXp to make a dual boot system, the installation went on smoothly but after 
installation i found that ,ubuntu is really slow . it takes a long time to respond to miouse clicks, graphical menus are really slow.

what could be the reason for this ?
is there any solution for this ?

I had given swap space equal to double the RAM size

Hi and could you give us some system specs? Like the graphics, memory and so on.

---

### Post by sulekha on 2008-07-29
> **overdrank said:**
> Hi and could you give us some system specs? Like the graphics, memory and so on.

it is a core to duo machine, with on board sound, graphics, intel  965G chipset system.it is an assembled machine (I don't know the motherboard make) 

but the main fact is , earlier ubuntu 7.04 was running smoothly on that machine

---

### Post by overdrank on 2008-07-29
> **sulekha said:**
> it is a core to duo machine, with on board sound, graphics, intel  965G chipset system.it is an assembled machine (I don't know the motherboard make) 

but the main fact is , earlier ubuntu 7.04 was running smoothly on that machine

Ok and I am assuming this is a clean install if Hardy and not a upgrade from 7.04 Feisty? The intel graphics are usually not a issue but you may check the display config to insure the right driver is being used. ```
gksu displayconfig-gtk
``` **and how much memory is on the system**?

---

### Post by sulekha on 2008-07-30
> **overdrank said:**
> Ok and I am assuming this is a clean install if Hardy and not a upgrade from 7.04 Feisty? The intel graphics are usually not a issue but you may check the display config to insure the right driver is being used. ```
gksu displayconfig-gtk
``` **and how much memory is on the system**?


memory on the system is 512 mb, but when i do cat /proc/meminfo it is showing 507 mb only.

But i am keep getting advices on the lines  hardy heron is bug prone,
you are not the only one having issues with it, better downgrade to 7.04
and wait until 8.04 is stable, free of bugs, ready to use

---

### Post by overdrank on 2008-07-30
> **sulekha said:**
> memory on the system is 512 mb, but when i do cat /proc/meminfo it is showing 507 mb only.

But i am keep getting advices on the lines  hardy heron is bug prone,
you are not the only one having issues with it, better downgrade to 7.04
and wait until 8.04 is stable, free of bugs, ready to use

Ok I have one system with Hardy on the intel graphics and 512mb and it runs good. Not perfect but good. I do know that system monitor is deceiving in showing amount of memory because I have my onboard graphics set to share 64mb. You may look at your bios to see if you can adjust the amount shared or you can always use 7.04 or 7.10 if you wish. :)

---

### Post by sulekha on 2008-07-31
> **overdrank said:**
> Ok I have one system with Hardy on the intel graphics and 512mb and it runs good. Not perfect but good. I do know that system monitor is deceiving in showing amount of memory because I have my onboard graphics set to share 64mb. You may look at your bios to see if you can adjust the amount shared or you can always use 7.04 or 7.10 if you wish. :)

how to set onboard graphics to share 64mb. in an 8.04 system ?

---

