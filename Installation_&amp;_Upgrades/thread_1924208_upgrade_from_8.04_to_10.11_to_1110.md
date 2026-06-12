---
title: "upgrade from 8.04 to 10.11 to 11/10"
date: 2012-02-12
forum: Installation &amp; Upgrades
---

### Post by trevorm0tws on 2012-02-12
Hi all still new to linux as specially the ubuntu i started like many on 8.04 light was very impressed so on my dell laptop i up graded to the 11.10 and works fine and stable.
now am trying to up grade my large tower computer from 8.04 ubuntu.
it will not accept the next version up, let a lone trying to install the 11.10.
from a iso disc it all up loaded to the computer but when it resets I get the black screen with lines of comms lines and loads of numbers. then it just sits there not moving any further.
so i have to re load the 804 light again from scratch.
the computer is a asrock board at 64 bit, 
3gig cpu, 1gig memory, 
nvidia 128 meg display card.
am not a gamer just general usage wondering if its to do with the display card.
as when i try to load the next ubutu version higher than 8.04 to 10.04 then noticed the graphics on the screen went real wierd looking in the initial install same place every time on the install.
any help would be appreciated and bare in mind am not a wizo on linux but open minded at 53 years old never to old to learn new tricks hi, but will say dumped windows years ago.
thank you Trevor

---

### Post by ottosykora on 2012-02-12
I would in such situation try just run few versions from the live CD. Doing that, you can fast asses if the version will work on the particular hardware without problems or if some adjustments have to be done.

In the past , there were some problems with some versions on older hardware, particular graphic adapters were not full compatible out of the box.

Also when you 'start all over' and you have x64 board, then take the 64 bit version, could work better sometimes.

Try the 10.04lts from live cd first, see what problems are there, if none, the go for the higher versions.

But the live cd are here to test your system and save your time by that.

---

### Post by 2F4U on 2012-02-12
The black screen issue may be resolvable by adding nomodeset to the grub kernel parameters:

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

The screen issue with 10.04 may be solved by adding the proprietary graphics driver once the installation is finished. Unfortunately, there is no way to test the proprietary drivers during the installation.

---

