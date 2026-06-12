---
title: "Trying to get nVidia drivers working"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by NewAuthority on 2010-01-30
Hey guys, have an irritating problem.
I'm not sure if this has been reported before, I tried looking and I did not think it has.
I just partitioned 20g's of space on my main drive and put ubutu 9.1 on it.  I checked for updates with software and hardware.  I went to System->Administration->Hardware Drivers and there I get the menu that has 2 nvidia accelerated graphics drivers (version 173 and 185).  It said that version 185 is recommended so I highlight it and hit the activate button.  It gets to about 55-60% on the load bar then this message pops up "SystemError: Failed to lock /var/cache/apt/archives/lock".

While I am new to linux and ubuntu, my friends are not and they don't have any idea on why this is happening.
In my search to see if this happened to anyone else, I saw some people using a program called envy. But I couldn't get that to install so kinda gave up on it.

nVidia Corporation G84 [GeForce 8600M GT] is the graphics card I am using on a Dell XPS M1530

any insight would help
thanks

---

### Post by NewAuthority on 2010-01-30
new update

now it doesnt even show a load bar it just pops up with 'SystemError: installArchives() failed'

---

### Post by knighthaq on 2010-01-30
try looking [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

had same problem.. also in order to save your settings after you get it loaded youl have to search and set permissions to be able to save your chosen resolution settings etc..

hope it helps you out 

p.s. make sure you uninstall the 185 driver first ,do not use recomended use current follow instructions in link..

 also go to system/admin synaptic package manager and get any required updates good luck

---

