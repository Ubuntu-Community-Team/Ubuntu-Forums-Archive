---
title: "Removal of broken debian package"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Lazareth on 2007-09-22
Hiya,

I've had a little run-in with a corrupted package, which left me with that annoying message that a package has to be reinstalled, but it can't find the archieve.

I've tried numerous things now, but the absolute most aggressive sequence didn't work (and left me a little dazed - I'm a newb, so I can't understand it all)

Here is my very last attempt since I gave up.
```
lazareth@Moobuntu:~$ sudo dpkg --configure -a
lazareth@Moobuntu:~$ sudo dpkg --remove --force-remove-reinstreq cdemu-daemon
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 121400 files and directories currently installed.)
Removing cdemu-daemon ...
 * Stopping CDEmu daemon                                                         * Killing daemon...                                                     [ OK ] 
 * Removing kernel module...                                             [fail] 
                                                                         [fail]
invoke-rc.d: initscript cdemu-daemon, action "stop" failed.
dpkg: error processing cdemu-daemon (--remove):
 subprocess pre-removal script returned error exit status 1
 * Starting CDEmu daemon                                                         * Inserting kernel module...                                            [fail] 
                                                                         [fail]
invoke-rc.d: initscript cdemu-daemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cdemu-daemon

```

It's directly copy-paste from the console. This solution didn't work.
I*m out of ideas. Anyone?

---

### Post by Pumalite on 2007-09-22
Try:

sudo apt-get remove --purge <packagename>

---

### Post by Lazareth on 2007-09-22
Tried that before. The readout is as follows:

```
lazareth@Moobuntu:~$ sudo apt-get remove --purge cdemu-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package cdemu-daemon needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by Pumalite on 2007-09-22
How about:

sudo killall <packagename>

---

### Post by Lazareth on 2007-09-22
...followed by the actual removal. Yeah, tried it.

Readout as follows:
```
lazareth@Moobuntu:~$ sudo killall cdemu-daemon
cdemu-daemon: no process killed

```

---

### Post by Pumalite on 2007-09-22
How about this:

sudo apt-get --reinstall install <packagename>

---

### Post by Lazareth on 2007-09-22
That I didn't try. However, since it can't find the archive in the first place... (which is corrupt anyway)

```
lazareth@Moobuntu:~$ sudo apt-get --reinstall install cdemu-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package cdemu-daemon needs to be reinstalled, but I can't find an archive for it.

```

Besides, I have the stuff I need installed in manual installation form (not a debian package) which should work. I just need this removed first. Before you ask, I can't make that install over this one because it needs a dependency I can't install before I gain control over my apt-get again (and synaptic for that matter). apt-get -f install doesn't work for it.

---

### Post by Lazareth on 2007-09-22
*bump*

I'm going to bed now (so I won't be able to answer right away). I'll check in again asap when I wake.
If possible, is there a way to manually go in and cut off all references and delete all the files related to a package? If I can't get this fixed, I'll pretty much have to reinstall Ubuntu (which right now could be a problem), so I'm willing to try and kill it the brutal way before starting from scratch.

I'll still very much like a "clean" solution.

---

### Post by Pumalite on 2007-09-22
We'll see you tomorrow and I'll see if I can think of something.

---

### Post by meierfra on 2007-09-23
Somebody had a similar  problem and solved it by manually removing the corrupted package from the dpkg status file:

[http://forum.freespire.org/archive/index.php/t-3429.html]("http://forum.freespire.org/archive/index.php/t-3429.html")

---

### Post by Lazareth on 2007-09-23
Okay, the removal of entries worked for getting my apt-get to work again.
However, wouldn't this simply hide the problem? What about the broken installation itself. I wouldn't want it to come back and haunt me.

---

### Post by meierfra on 2007-09-23
Did you do "dpkg --purge cdemu-daemon" to remove the package? After that the package should be completely gone .  And if you need the package you should be able to reinstall.

---

