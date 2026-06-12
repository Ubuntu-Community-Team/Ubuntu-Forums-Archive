---
title: "system monitor and keepass2 no longer open after upgrade to 16.04"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by Frank Haverkort on 2016-10-14
After I upgraded to 16.04, I cannot open the system monitor or the program keepass2 anymore. For example when I open the system monitor using dash, the system monitor's icon appears in the panel on the left side of my screen, and a small triangle indicates that the program is running. But no window appears. I can click on the icon in an attempt to see a window but nothing happens. I have a similar issue with the program keepass2. With keepass2 initially a screen opens, asking for a password, but when the password is entered the screen disappears (as it should) but the new screen showing the password database does not show up. Again, the keepass2 icon is still present and active but there simply is no window present anymore. 

I have already tried running these programs from the commandline to see if any informative error message would appear. This is not the case. When I open the system monitor from the commandline (as gnome-system-monitor),  it seems to run fine and no error messages appear (but I see no window). Running keepass2 from the commandline gives the following, which does not look like an error message to me:
frank@thuis:~$ keepass2
SendMessage (77594668, 0x112c, 0x4, 0x4)


Before I upgraded to 16.04 the system monitor and keepass2 were working fine, but sometimes I would have this same issue with the pdf viewer evince. Sometimes double clicking on a pdf file would open it with evince (the default viewer), and sometimes an icon would appear in the panel but no window would open.

Hope you guys can help!

---

### Post by howefield on 2016-10-15
Try reinstalling the package. eg

```
sudo apt install --reinstall gnome-system-monitor
```

---

### Post by Frank Haverkort on 2016-10-15
Thanks for the idea, but unfortunately the problem still remains after reinstall of gnome-system-monitor and restarting the computer... Even though reinstall seemed to go fine:

frank@thuis:~$ sudo apt install --reinstall gnome-system-monitor
Pakketlijsten worden ingelezen...
Boom van vereisten wordt opgebouwd...
De statusinformatie wordt gelezen...
0 opgewaardeerd, 0 nieuw geïnstalleerd, 1 opnieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
Er moeten 151 kB aan archieven opgehaald worden.
Na deze bewerking zal er 0 B extra schijfruimte gebruikt worden.
Ophalen:1 [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) xenial-updates/main i386 gnome-system-monitor i386 3.18.2-1ubuntu1 [151 kB]
151 kB opgehaald in 0s (335 kB/s)
(Database wordt ingelezen ... 371555 bestanden en mappen momenteel geïnstalleerd.)
Uitpakken van .../gnome-system-monitor_3.18.2-1ubuntu1_i386.deb wordt voorbereid...
Bezig met uitpakken van gnome-system-monitor (3.18.2-1ubuntu1) over (3.18.2-1ubuntu1) ...
Bezig met afhandelen van triggers voor man-db (2.7.5-1) ...
Bezig met afhandelen van triggers voor libglib2.0-0:i386 (2.48.1-1~ubuntu16.04.1) ...
Bezig met afhandelen van triggers voor desktop-file-utils (0.22-1ubuntu5) ...
Bezig met afhandelen van triggers voor mime-support (3.59ubuntu1) ...
Bezig met afhandelen van triggers voor gnome-menus (3.13.3-6ubuntu3.1) ...
Bezig met afhandelen van triggers voor bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Instellen van gnome-system-monitor (3.18.2-1ubuntu1) ...

---

### Post by howefield on 2016-10-15
Ok, let's look at KeePass for a minute.

Try moving ~/.config/KeePass/KeePass.config.xml to another folder, say your Documents just for safe keeping. Open up KeePass and it will generate a new file. If it fails you can always move the original file back.

---

### Post by Frank Haverkort on 2016-10-16
I moved the Keepass config file but Keepass still behaves in the same way as before: starting Keepass2 from the commandline does not produce any errors, on the commandline the program does not terminate, but no window appears.

---

### Post by Frank Haverkort on 2016-12-10
I eventually "solved" this issue, so let me mention that here for future reference. After formatting my hard drive and installing Ubuntu 16.10, my problem of programs that will not open disappeared. 

Note that before I installed Ubuntu 16.10, I had tried whether a fresh install of Ubuntu 16.04 (after formatting the hard drive) would work. It did not. Maybe my hardware didn't combine well with Ubuntu 16.04? I'm running an AP Velocity II PC. Have tried googling whether this hardware has any issues with Ubuntu 16.04 but did not find anything.

---

### Post by ScientificProp on 2016-12-31
Well, that not very encouraging to hear! I just installed 16.04 LTS on a new system I'm setting up, but I've been using Keepass2 for many years - and plan to continue using it. I've been wondering why the 16.04 Software Manager cannot 'find' Keepass2. Sounds like I'd be better off installing 16.10?

---

### Post by bearlake on 2017-01-01
> **ScientificProp said:**
> Well, that not very encouraging to hear! I just installed 16.04 LTS on a new system I'm setting up, but I've been using Keepass2 for many years - and plan to continue using it. I've been wondering why the 16.04 Software Manager cannot 'find' Keepass2. Sounds like I'd be better off installing 16.10?

I have many computers running 16.04 and keepass2 without any issues.

Your in good hands with 16.04

---

### Post by Keith_Helms on 2017-01-01
I'll second that.  I have a couple of systems running 16.04 and no problem with Keepass2 on either of them.

---

### Post by deadflowr on 2017-01-01
> I've been wondering why the 16.04 Software Manager cannot 'find' Keepass2. 
It available in the repos, just that the new software manager gnome-software seems to have odd indexing problems/anomalies, here and there.
Here's a bug that might give you some idea of what others have seen:
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1579415]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1579415")

I think most find the oddness of the new manager compared to the old manager to be enough to simply install packages through apt-get or install synaptic.

I know that, except for a few packages to make sure the software manager functions, I mostly use apt-get to install things, since a terminal is fast to open.
(Neither the new software center nor the old one handled installing multiple applications at once very well, but in fairness that's not what it's about.
It's not something to go 'I need all these programs installed now, in one fell swoop'. It's more for Users to find a single new package they might want to try and install it; which it does very well)

---

### Post by ScientificProp on 2017-01-02
thanks for the info that Keepass2 can work with 16.04LTS, I'll try installing it. I read the other 'bug report', which is consistent with my observation. The Software Manager doesn't 'see' Keepass2, but I was able to find in using Synaptic. So, I'll try installing it from there. There were some other programs/applications that I could not find with Software Manager, but I don't remember which.

---

### Post by elicoten on 2017-05-11
Regarding KeePass please see the my comment on this [bug report]("https://bugs.launchpad.net/ubuntu/+source/keepass2/+bug/1239454/comments/9") which fixed it for me. It used to happen much more frequently on Ubuntu a few years ago. Now this is the first time literally in a couple of years its happened and it took me a while to remember/rediscover how to fix it.

Hope his help

---

