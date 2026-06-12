---
title: "upgrade 17.04 to 17.10 boot stuck at &quot;Started gnome display manager....."
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by wern1 on 2017-10-20
I upgrade from 17.04 to 17.10 but boot is stuck at

(ok) Started GNOME Display manager. script.neration........ance-master).p link was shut down....


Any help would be appreciated

---

### Post by eneiluj on 2017-10-21
Same for me.

[ OK ] Started OpenVPN service. Script Dispatcher Service...ystem changes.pp link was shut down.

There seems to be disk activity. Is it possible system is doing a filesystem check ?

---

### Post by rajatkn on 2017-10-22
Same problem here.. 
Can't start either gdm3 or lightdm.
Also tried reinstalling & configuring both.

---

### Post by igouy on 2017-10-22
You'll need to investigate the problem further.

One of the boot options will probably be:

   [FONT=Lucida Console]Advanced options for Ubuntu[/FONT]

:choose that, then choose:

   [FONT=Lucida Console]Ubuntu, with Linux 4.13.0-16-generic (recovery mode)[/FONT]

:and see if you can find any error messages in the logs in failsafe graphics mode.


So far I've managed to find a problem with missing NVidia packages, which led me to a networking problem seemingly caused by some resolvconf name-server mis-configuration. 

I've managed to fix the resolvconf problem enough to load the missing Nvidia packages -- but now I'm stuck at:

   [FONT=Lucida Console][ OK ] Started GNOME Display Manager.
    [ OK ] Started Hostname Service.[/FONT]

---

### Post by igouy on 2017-10-23
*fyi*  I'm about ready to accept that my 17.04 to 17.10 upgrade was a failure, and re-install 17.10 clean and then start doing all the other rework that will be needed. Good luck.

---

### Post by wern1 on 2017-10-26
Well, I got it somehow running again, but admit is was playing around without really knowing what I was doing. This just a a warning.
What I did was delete Nvidia "apt-get purge nvidia-*". I don't have an Nvidia-card but a Radeon card, so I have unfortunately no clue if this was/could be a reason. I just notice that other people also have problems upgrading from 17.04 to 17.10.
Now I have the following choices at login:

[FONT=arial]gnome[/FONT][FONT=arial]gnome unter xorg[/FONT]
[FONT=arial]gnome under xorg (without ubuntu picture)[/FONT]
[FONT=arial]ubuntu (standard)[/FONT]
[FONT=arial]ubuntu on xorg (without ubuntu picture)[/FONT]
[FONT=arial]ubuntu on xorg[/FONT]
[FONT=arial]unity (without ubuntu picture)[/FONT]
[FONT=arial]All first 5 choices do NOT work, but after a loop end up again at the login screen.
Choice No 6 "Unity" works and I have my system back up running. I will for the time being not fiddle around anymore but if upgrades do not solve the problem soon, then I will at some point do a new install of 17.10.[/FONT]

---

### Post by dino99 on 2017-10-26
Please do a separate partition install for each DE, dont mix them if you lokk at stability.

---

### Post by wern1 on 2017-10-26
Thanks. Ehhm. Actually I would prefer only having one DE - Ubuntu 17.10 with Wayland. I don't even know how I ended up with all the choices. I was able to delete "plasma" but don't dare to fiddle around with the rest for fear of loosing access again as my competence doing this is limited.

---

### Post by mörgæs on 2017-10-26
There have been some reports of problems running Ubuntu 17.10 with Nvidia. I don't know the details more than 'somehow related to Wayland'.

If everything else fails you could try a fresh install of Lubuntu 17.10 which has not yet implemented Wayland.

---

