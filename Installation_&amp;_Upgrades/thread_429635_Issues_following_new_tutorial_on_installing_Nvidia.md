---
title: "Issues following new tutorial on installing Nvidia driver for 8800gtx, help?"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Jonathan123 on 2007-05-01
So I am trying to install some Nvidia drivers for my 8800gtx so I can start using Maya.

However, I am getting stuck on this tutorial.

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

Basically,

I get to the bottom where it says,

> Change the DISABLED_MODULES=”" to DISABLED_MODULES=”nv”

. . .and I can't enter in any text for "nv" and it just says "E35" and gives a red error message.

How do I enter in the simple "nv."  I completely abandoned Windows so I can finally make the switch (except for programs that aren't Linux-compatible).

Thanks for your help!  :)

---

### Post by GoGrazy on 2007-08-26
> **Jonathan123 said:**
> So I am trying to install some Nvidia drivers for my 8800gtx so I can start using Maya.

However, I am getting stuck on this tutorial.

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

Basically,

I get to the bottom where it says,



. . .and I can't enter in any text for "nv" and it just says "E35" and gives a red error message.

How do I enter in the simple "nv."  I completely abandoned Windows so I can finally make the switch (except for programs that aren't Linux-compatible).

Thanks for your help!  :)

Hi!

I am newbie in linux but i find site that maybe help you.
[http://www.petefreitag.com/item/504.cfm](http://www.petefreitag.com/item/504.cfm)
In that site explains basic commands for vi program.
I used nano to change file.
I just replaced vi to nano. "sudo nano /etc/default/linux-restricted-modules*"
Use your arrow keys to move cursor right place and edit line.
To Quit and save press ctrl and x then it ask if you want accept changes. "press y."
Then it shows the path of the file press enter.
close konsole.
:)

---

