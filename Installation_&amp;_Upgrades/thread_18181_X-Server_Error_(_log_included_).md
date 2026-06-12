---
title: "X-Server Error ( log included )"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by pugrit on 2005-03-05
i have problems with my X-Server and i followed some fo the insatructions i got from this forums.

heres the XFree86.0.log:

...

parse error on line 81 of section monitor in file /etc/x11/XF86config-4 "COLOR" is not a valid keyword in this section.

(EE) Problem parsing the config file
(EE) Error from XF86handleconfig()

fatal server error:

no screens found.

...

i want to explore and try to do things but i hesitate since, 1st this is my first time linux insatlation and second, im on dual boot and i dont want anything to happen to the xp since im sharing this computer with my brother and he has projects in the xp.

in the XF86config-4 file:

Section "Monitor"
        identifer "14" COLOR "   <-- line 81


how can i fix this and and satr my GUI?i tried startx but still the same. no GUI in startup.

Thanks.

---

### Post by doitashimashite on 2005-03-05
The double quote in the line

identifer "14" COLOR "

is likely to cause problems.

Try this:

identifer "14\" COLOR "

or this:

identifer "14 inch COLOR "

and make sure that you change the same string the same way elsewhere in the file.

---

### Post by pugrit on 2005-03-05
ok will try that. im sure my video card is compatible cause the live version works perfectly.

---

