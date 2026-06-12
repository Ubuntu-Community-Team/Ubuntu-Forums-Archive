---
title: "[SOLVED] apt-get failed on some items and now errors on them every time."
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by amishphysicist on 2008-09-30
Heya,

I've had a nagging problem with apt-get.  I tried to install some fancy audio stuff a few weeks ago and a couple of items failed.  Since they failed, I figured I could just go into the add/remove programs gui and untick the offenders.  That failed too.

Now any time I apt-get anything, or install from the happy-fun-time add/remove gui, those two little bastards error out:

```
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                                                                                                      [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured

```

How can I tell ubuntu to put the axe to these?

thanks!

---

### Post by Partyboi2 on 2008-10-02
Open a terminal (Applications>Accessories>Terminal) and try
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by Torquemada28 on 2008-10-02
Thanks mate!

Your solution fixed my problem in [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=934707").

You're a bloody champion.

---

### Post by amishphysicist on 2008-10-02
Hmm. no luck there...

```
nlieby@nlieby-lin:~/code/xoom/mainline$ sudo dpkg --configure -a
[sudo] password for nlieby: 
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                                                                                        [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
nlieby@nlieby-lin:~/code/xoom/mainline$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                                                                                        [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Partyboi2 on 2008-10-02
Reading a bug report a person had success by stopping timidity manually first, so try
```
sudo killall timidity
```
```
sudo apt-get install
```

---

### Post by amishphysicist on 2008-10-02
Hmm. Still fails with the killall:

```
sudo killall timidity
[sudo] password for nlieby: 
nlieby@nlieby-lin:~/code/xoom/mainline$ sudo killall ubuntu-studio
ubuntu-studio: no process killed
nlieby@nlieby-lin:~/code/xoom/mainline$ sudo apt-get install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                                                                                                          ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
                                                                                                                                                                [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Partyboi2 on 2008-10-02
If you don't need timidity try removing it.
```
sudo apt-get remove timidity
```

---

### Post by amishphysicist on 2008-10-03
Sweet. That's what I was trying to do in the first place, but the add/remove GUI failed at ever getting rid of them.  
 
```

sudo apt-get remove timidity
[sudo] password for nlieby: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  timidity ubuntustudio-audio
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 1778kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 200278 files and directories currently installed.)
Removing ubuntustudio-audio ...
Removing timidity ...
 * Stopping TiMidity++ ALSA midi emulation...    
```

Thread solved!  You get 10 bro points.

---

