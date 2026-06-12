---
title: "what have i done wrong now! bad install?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by tom1979 on 2007-02-12
My ubuntus gone wrong, my first install worked sweet as a nut after the initial wiping on xp! i managed to partition and dual boot, i got my wireless working, and i was happy!

untill i was hacked, and forced to reinstall (ubuntu wasnt affected but i wanted a clean formatted hdd).

Now ive had no end of problems. at the startup grub? menu theres 6 ubuntu OS options... including 2 recovery modes and 2 server modes, as well as xp.

xp works fine, wireless works as expected. i cant get wirelss to work now in ubuntu, and every time i boot ubuntu i have to play around to get the wired internet settings to work and connect.

on top of this i keep getting errors along the lines of 'no authority to access this , did you run using sudo?'

now im only at the playing with settings stages, ive not time to sit and get too involved right now while windows is only a reboot away, so ive not played around and entered any commands i dont know about. 

What id like to know is how to easyly get a factory instal back that has functional wifi, and to get rid of the unwanted boot options! any ideas short of a reformat of partitions?

all i did on my original instal was run a full upgrade ticking all update boxes, then i ran automatix and again ticked all boxes :P

thanx in advance.

---

### Post by jackrobinson on 2007-02-12
> **tom1979 said:**
> My ubuntus gone wrong, my first install worked sweet as a nut after the initial wiping on xp! i managed to partition and dual boot, i got my wireless working, and i was happy!

untill i was hacked, and forced to reinstall (ubuntu wasnt affected but i wanted a clean formatted hdd).

Now ive had no end of problems. at the startup grub? menu theres 6 ubuntu OS options... including 2 recovery modes and 2 server modes, as well as xp.

xp works fine, wireless works as expected. i cant get wirelss to work now in ubuntu, and every time i boot ubuntu i have to play around to get the wired internet settings to work and connect.

on top of this i keep getting errors along the lines of 'no authority to access this , did you run using sudo?'

now im only at the playing with settings stages, ive not time to sit and get too involved right now while windows is only a reboot away, so ive not played around and entered any commands i dont know about. 

What id like to know is how to easyly get a factory instal back that has functional wifi, and to get rid of the unwanted boot options! any ideas short of a reformat of partitions?

all i did on my original instal was run a full upgrade ticking all update boxes, then i ran automatix and again ticked all boxes :P

thanx in advance.

nothing's gone wrong. There are multiple options on grub because you have multiple kernel images installed.
Search for linux-image in synaptic and uninstall all the ones which you are NOT using.
That will remove the extra options from grub.
for connecting to wifi, are you using network-manager?
Network manager needs to be correctly set up for wifi to work correctly. 
the info about sudo will come up when you run certain options as normal user which need to be run as root (nothing's wrong with that either).

---

