---
title: "DLink DWL-G510 RA1 not working in Fiesty"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by aminahmadi on 2007-05-11
So I decided it is a good idea to drop XP at my parents' in favour of Ubuntu because they mostly use the internet and not much more anyway. 

Everything went well except a crucial step and that is working on the wireless card, 
DWL G510 Rev A1. I have searched along a lot of found alot related to rev B which didn't work. 

ndiswrapper sounded like a good workaround but I failed to get it running, but I know there is alot about that out there. 


Any help would be appreciated,

---

### Post by p110011 on 2007-05-23
Yes I just got mine working with ndiswrapper and the windows xp driver from d-link.
It is mrv8k51.inf

Install ndiswrapper and then

sudo ndiswrapper -i/path_where_you_put_the_driver/Driver/manual/WinXP/mrv8k51.inf

---

### Post by jgrant83 on 2007-06-03
I thought you might have solved this by now but by selecting which wireless network to connect to (if yours allows this) and typing this into the terminal

sudo dhclient ra1

Works for me anyway ;)

---

