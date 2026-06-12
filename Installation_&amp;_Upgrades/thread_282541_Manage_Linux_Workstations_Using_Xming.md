---
title: "Manage Linux Workstations Using Xming"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-10-22
Anyone uses Xming to manage xubuntu?

[http://blandname.com/2006/10/19/manage-linux-workstations-using-xming/]("http://blandname.com/2006/10/19/manage-linux-workstations-using-xming/")

[http://sourceforge.net/projects/xming]("http://sourceforge.net/projects/xming")

[http://freedesktop.org/wiki/Xming]("http://freedesktop.org/wiki/Xming")

Can you share your experiences?

---

### Post by airtonix on 2006-11-02
[B]update: Success! read below

[/B]I was hoping this would allow me to provide the use of gedit to my imprisoned windows devlopers in my team.....
Alas....setting up a further 5 computers on ubuntu seems too daunting to my supervisor.....
seesm to think that since spartacus was in chains , we can then all just accept microsoft as the standard of comparison when mentioning the concept of compability.....

absolutly laughable

anyway, I have xming running on my ms machine down in the dungeon.....strung up on the rack with Igor watchin it....

I just need to extract from it the secret of running **Gedit** within its foul soul.....any ideas peoples?


** Update : **

i found out how to do it....and its much simplier than I orginally thought.
[LIST=1]
[*]install Xming as per software authors instruction on the dozer machines.
[*]install putty as well....well install is a loose toerm, just get it onm you dozer machines.
[*]run putty.
[*]goto the config are for networking....and turn on X11 forwarding.
[*]modify your linux firewall to allow connections via the usual ssh port you use (default is port 22)...good idea here is to whitelist only the IP addresses of the dozer machines you will use to conenct.
[*]goto your superior magical paladin linux machine...(grin grin) and goto : 
 > system -> administration -> login window
[*]then from there enable TCP connections to the X server.
[*]then back at the dozer farm, run putty with the view to connect to the ip address of your linux machine.
[*]login and password as per usual with ssh connections.
[*]now here is the really simple part. type : 

> nautilus &the desktop should load, or maybe just the file manager...you can now use nautilus under windows, and if the desktop loaded its gnome operations as per usual.
[*]if only the desktop loaded, then you can still run commands from the terminal(putty window): 
> gedit & [/LIST]This is just off the top of my head and im not actually running windozer in front of me right now...but im pretty sure those are the steps you need to take care of.

---

