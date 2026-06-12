---
title: "A couple of questions about upgrading to Hoary"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by Diego F. on 2005-03-31
I want to upgrade my warty to hoary and I have two questions:

- Can I make the upgrade using Synaptic or the apt-get dist-upgrade has to be run in console? In that case, can be done in the Gnome session?

- Can I download the ISO, burn it and get the proccess done using a CD instead of the Internet download?

---

### Post by arctic on 2005-03-31
yes you can. please use the search tool. there have been dozens of posts on that topic. ;)

---

### Post by Psquared on 2005-03-31
[QUOTE=Diego F.]I want to upgrade my warty to hoary and I have two questions:

- Can I make the upgrade using Synaptic or the apt-get dist-upgrade has to be run in console?** In that case, can be done in the Gnome session?**

- Can I download the ISO, burn it and get the proccess done using a CD instead of the Internet download?[/QUOTE]

I would like to know the answer to the part that put in "bold" above too. I have searched but I cannot find the answer. To put it in my words, do you have to be at run-level 3 (no X or gui running) to do the dist-upgrade or can you do it with Gnome running and then just reboot to finish the process?

---

### Post by Diego F. on 2005-03-31
Well, I have some time now and I'll do it with apt-get dist-upgrade.

I'll tell you later  :wink:

---

### Post by Psquared on 2005-03-31
[QUOTE=Diego F.]Well, I have some time now and I'll do it with apt-get dist-upgrade.

I'll tell you later  :wink:[/QUOTE]

Are you going to do it with Gnome running or are you going to boot to a prompt without X running?

Please let me know how you do it and if you are successful. I am really stumped here. ](*,)

---

### Post by Diego F. on 2005-03-31
I did it in a Gnome session. The installation was done succesfully, but I have some issues now. I'll ask in other threads.

---

### Post by arctic on 2005-03-31
i also updated with gnome running although it is much better to do it from a shell terminal. most problems that occur when updating while running gnome can be solved by rebooting and running synaptic again. it could be that some packages did not install properly.

oh... and when asked to replace certain files, always use "Y", in order to replace all warty files with hoary ones. ;)

---

### Post by Psquared on 2005-03-31
[QUOTE=arctic]i also updated with gnome running although it is much better to do it from a shell terminal. most problems that occur when updating while running gnome can be solved by rebooting and running synaptic again. it could be that some packages did not install properly.

oh... and when asked to replace certain files, always use "Y", in order to replace all warty files with hoary ones. ;)[/QUOTE]

What is the best way to get to a shell terminal? Telnet 3 or reboot to runlevel 3? I assume you are talking about with X not running at all??

---

### Post by jery_wang2002 on 2005-03-31
[QUOTE=arctic]i also updated with gnome running although it is much better to do it from a shell terminal. most problems that occur when updating while running gnome can be solved by rebooting and running synaptic again. it could be that some packages did not install properly.

oh... and when asked to replace certain files, always use "Y", in order to replace all warty files with hoary ones. ;)[/QUOTE]
 This makes Ubuntu rocks.

The last time I tried to upgrade fc3 to fc4 testing using synaptic, it leaves my system in a messy state. I am now using Ubuntu. Never try warty to hoary since I install Hoary Array CD 7 straight away. But keep updating every day without any single problem since then. I think mine should be RC by now (is it?).

Ideally, any distro should never ask the user to reinstall (--reformat--) the hardisk just because there is new version coming up. 

Imagine how a user has to reformat the hardisk every 6 months just to enjoy the new version of the distro. That is unacceptable.

---

### Post by audax321 on 2005-04-01
Psquared,

   I've tried to get into init 3 and from what I've read, Debian based distros don't have this run level... the only other way to do this is kind of weird, but edit your XF86Config and make some line invalid and make X crash after you reboot. This will give you a console prompt (same as init 3 becuase there is no X running). Then just do your upgrade, change back the config file, and reboot...

---

### Post by Psquared on 2005-04-01
[QUOTE=audax321]Psquared,

   I've tried to get into init 3 and from what I've read, Debian based distros don't have this run level... the only other way to do this is kind of weird, but edit your XF86Config and make some line invalid and make X crash after you reboot. This will give you a console prompt (same as init 3 becuase there is no X running). Then just do your upgrade, change back the config file, and reboot...[/QUOTE]

Ughh .... I don't like the sound of that. I am much to tidy to make something crash on purpose.  8-[ 

I think I will try the way suggested above. Run the upgrade in Gnome, reboot and run again .... maybe a couple of times to see if I can get everything to install. It's a really strange error and I have searched over and over again and I can't seem to find anyone with a similar problem. It maybe my laptop.

---

### Post by audax321 on 2005-04-01
I actually upgraded my laptop with gnome running and didn't have any problems. BTW, making X crash doesn't really mess anything up and its not a hardcore going to eat your system files and break things type of crash. It just gives an error saying that X couldn't start and you should check your configuration (which you know you messed up on purpose anyway) and gives you a console prompt. Also since hoary is going to replace XF86 with X.org, it doesn't really matter anyway. I install my video card drivers like that  :wink:

---

