---
title: "Can I install Kubuntu 14.04 and keep all my current Ubuntu 14.04 settings"
date: 2014-09-15
forum: Installation &amp; Upgrades
---

### Post by pappo2 on 2014-09-15
I am currently running Ubuntu 14.04.1 and just received my latest Ubuntu User magazine with a copy of Kubuntu 14.04 on the DVD.
I would like to try out Kubuntu but keep my settings for samba, cups, etc...
I did not set this machine up with a separate root and home partitions, so am is it not possible ?

Thanks for any help

---

### Post by maxinstuff2 on 2014-09-15
Is it a livecd? You could just boot from it and try it out.

For your settings, it depends what other settings you include. If you just mean lower level stuff like drivers etc. then sure.

You could just do:
```
sudo apt-get install kubuntu-desktop
```

Which will install the entire Kubuntu desktop environment. You then select which DE you wish to use from the login screen.
Note that it isn't just KDE - you will get a load of other KDE-centric applications that replicate functionality you already have. But I feel it is better than dual booting if all you want to do is try it out.

It will be a bit bloated though with apps all over the place (duplicate text editors, email programs etc. etc.) :/

If you want to make the switch proper - then do this afterwards:
```
sudo apt-get remove ubuntu-desktop
```

I am fairly sure that will leave your ubuntu-specific config files behind as well in case you change your mind later on (You need to use --purge to delete config files.)
CUPS will be untouched, but someone more knowledgable than I will need to tell us whether samba will be affected. I'm not sure if it is linked to nautilus or if it is independant of DE (I have not used it).

---

### Post by fantab on 2014-09-15
You can install Kubuntu alongside Ubuntu and dual-boot.
Kubuntu comes with KDE
Ubuntu with mostly GTK...
If you keep settings from ubuntu, there is a possiblity of things breaking.

Also its not a good idea to install kubuntu-desktop on top of ubuntu. It will be a mess at some point.

The best is to keep trying Kubuntu from LiveDVD. When you are ready to install then either replace Ubuntu or install Kubuntu on its own partition...

My two cents...

---

### Post by mastablasta on 2014-09-15
> **maxinstuff2 said:**
> 
If you want to make the switch proper - then do this afterwards:
```
sudo apt-get remove ubuntu-desktop
```

I am fairly sure that will leave your ubuntu-specific config files behind as well in case you change your mind later on (You need to use --purge to delete config files.)
CUPS will be untouched, but someone more knowledgable than I will need to tell us whether samba will be affected. I'm not sure if it is linked to nautilus or if it is independant of DE (I have not used it).

this won't work since that is a meta package.it goes something like this: [http://www.psychocats.net/ubuntucat/?s=Pure+Kubuntu](http://www.psychocats.net/ubuntucat/?s=Pure+Kubuntu)
the problme is that the Psychocats doesn't have the time to update the blog anymore (a shame really) so i do not know the command to do the same with current version. i am sure you could look into same files and update this command to use the newer version and possibly some other things.

another option is to just add KDE package instead of kubutnu-desktop. what happens when you add the desktop is that it will work but you will have for example 2 network manager (one form kubuntu one from ubuntu) etc. 

found a guide (check bottom) to find and uninstall the packages: [http://askubuntu.com/questions/453841/how-to-remove-lubuntu-desktop-from-ubuntu-14-04-lts](http://askubuntu.com/questions/453841/how-to-remove-lubuntu-desktop-from-ubuntu-14-04-lts)

that way you could add kubuntu desktop and then do the uninstall of Ubuntu if you would prefer it.

---

