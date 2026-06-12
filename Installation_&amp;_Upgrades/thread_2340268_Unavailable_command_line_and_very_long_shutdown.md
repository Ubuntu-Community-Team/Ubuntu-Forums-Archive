---
title: "Unavailable command line and very long shutdown"
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by regis-sarle on 2016-10-17
Hi,


I migrated mon workstation to 16.04 LTS last week. Since, I'm having two issues :

[LIST]
[*][ctrl]+[alt]+[Fx]where  x goes from 1 to 6, doesn't show anything ! I can't access to the command line (terminal is available in windows mode). The screen stays black with white static cursor in the top left. Ctr+alt+F7 allows me to go back to graphical mode. 
[*]Modeover, it's very long to shutdown (more than 2 minutes). With 14.04 LTS, it was very quick (about 15 secondes). I think the problem is linked because it doesn't show the operations but stays stuck on black screen with white static cursor in the top left. 
[/LIST]
I don't find any error in syslog when i try to open the commande line:

```
systemd[1]: Started Getty on tty6.
```
But I have a lots of error (about 100 every 10 minutes), but I don't think that they are related :

```
(tracker-miner-fs:2890): Tracker-CRITICAL **: Could not execute sparql: Subject `(null)' is not in domain `nfo:FileDataObject' of property `nfo:fileName'
gnome-session[2704]: (tracker-miner-fs:2890): Tracker-CRITICAL **:   (Sparql buffer) Error in task 0 of the array-update: Subject `(null)' is not in domain `nfo:FileDataObject' of property `nfo:fileName
gnome-session[2704]: (tracker-miner-fs:2890): Tracker-CRITICAL **: Could not execute sparql: Subject `urn:uuid:7baf0e5f-214f-9a39-697a-8c81da27db31' is not in domain `nfo:FileDataObject' of property `nfo:fileName'
```
If you have some idea, please share !

---

