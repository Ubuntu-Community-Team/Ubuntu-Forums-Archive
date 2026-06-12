---
title: "Outstanding problems in Jaunty"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-01-11
I have the following collection of problems on my Satellite Pro Laptop

[LIST]
[*]Although the ATI driver is enabled I cannot enable Desktop effects. Now getting and error message about glxinfo crashing when try to enable.
[*]Cannot upload debug information, error about url not available
[*]Leaving the laptop in standby means a black screen from which I cannot recover. More, I cannot turn the machine off, pressing the power button results in a momentary power dip followed by the black screen again. Battery removal is the only option.
[/LIST]

Anyone recognise these as bugs, or am I the only one with these problems.
The rest of Jaunty is going really well.

---

### Post by aethralis on 2009-01-11
> **Peter09 said:**
> 
[LIST]
[*]Cannot upload debug information, error about url not available
[/LIST]


This is a bug in launchpad (see [https://bugs.launchpad.net/ubuntu/+source/launchpad-integration/+bug/311690](https://bugs.launchpad.net/ubuntu/+source/launchpad-integration/+bug/311690) ). The workaround is that you have to wait for some 10 secs or so and reload the page.

---

### Post by ShirishAg75 on 2009-01-11
aethralis. 
      the bug you have given and the issue they are saying are two different ones. That one is after the data has been submitted to the server/launchpad and it not being able to generate the report page. 

What these guys are talking about is not able to communicate with the server itself for some reason other than network/internet connectivity.

---

### Post by aethralis on 2009-01-11
There are indeed two separate problems, but to my knowledge the first one (not able to connect to the server) has been already addressed.

see [https://bugs.launchpad.net/ubuntu/intrepid/+source/python-launchpad-bugs/+bug/309307](https://bugs.launchpad.net/ubuntu/intrepid/+source/python-launchpad-bugs/+bug/309307)

---

