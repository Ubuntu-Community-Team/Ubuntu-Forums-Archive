---
title: "Needed: Information about kernal upgrades."
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by faceoftheearth on 2007-05-31
I recently updated to the newest officially available kernel. I stick with whatever the update manager gives me rather than the bleeding edge vanilla kernels simply because it's easy. Anyway, I have a question that could probably be answered given enough man page browsing and such. However, rather than trying to translate the gibberish in manpages which seems to be quite often written by non English speakers I thought I'd pose the question here because I know the people on this forum can answer the question succinctly and might even enjoy answering it. 

My question is this: How does the kernel update process affect currently installed programs. For the most part there are no problems with programs after an update, however some programs (I'm assuming those with kernel modules)  fail to work after the upgrade. For instance the Cisco VPN client (which needed to patch things to begin with) fails with a message about modules when I'm in a kernel different than that which I installed it to. 

So if each minor kernel update fskcs up programs I'm assuming there is a standard way to easily migrate programs or modules from one kernel to the next. It seems that anything less would be a bit of a waste of the user's time. 

Any information on the process is truly appreciated.

---

### Post by K0LO on 2007-05-31
Programs that you compile yourself like the Cisco VPN client are compiled for a specific kernel. When you upgrade the kernel you need to recompile the program.

A suggestion -- make a text file with the steps required to do the recompilation. Keep it where you can refer to it after a kernel update and then just do the steps over again.

For example, in my /home/Setup folder I have text files for how to recompile Cisco VPN client, how to re-map browser forward/back keys in Firefox (for when Firefox is updated), and how to recompile the alsa drivers for my unusual sound card. I refer to these instructions whenever these things are updated and stop working.

If you're ambitious then you can put all of the required steps in a script, and then for each new kernel update just run your script and let it update things for you.

---

