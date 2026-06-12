---
title: "Synaptic, apt-get &amp; Add Remove all borked!"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by picard359 on 2010-07-13
Hi,

I have a new Karmic 9.10 install and it seems to have become unstuck due to a crash during an install. It refused to boot up and I have managed to repair it with a live CD.

The system is up and running but all future installs, updates and upgrades fail now. The error's are relating to missing 'schemas' and unconfigured dependencies, as below:

~$ sudo apt-get install metacity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
metacity is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up aisleriot (1:2.28.0-0ubuntu3) ...
Warning: /usr/share/gconf/schemas/aisleriot.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing aisleriot (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up brasero (2.28.2-0ubuntu1) ...
Warning: /usr/share/gconf/schemas/brasero.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing brasero (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up metacity-common (1:2.28.0-0ubuntu2) ...
Warning: /usr/share/gconf/schemas/metacity.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing metacity-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libmetacity0:
 libmetacity0 depends on metacity-common (>= 1:2.28); however:
  Package metacity-common is not configured yet.
 libmetacity0 depends on metacity-common (<< 1:2.29); however:
  Package metacity-common is not configured yet.
dpkg: error processing libmetacity0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on libmetacity0 (>= 1:2.25.8); however:
  Package libmetacity0 is not configured yet.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-gnome | compiz-kde; however:
  Package compiz-gnome is not configured yet.
  Package compiz-kde is not installed.
dpkg: error processing coNo apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
               mpiz (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on libmetacity0 (>= 1:2.25.8); however:
  Package libmetacity0 is not configured yet.
 metacity depends on metacity-common (>= 1:2.28); however:
  Package metacity-common is not configured yet.
 metacity depends on metacity-common (<< 1:2.29); however:
  Package metacity-common is not configured yet.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-metacity:
 python-metacity depends on libmetacity0 (>= 1:2.25.8); however:
  Package libmetacity0 is not configured yet.
dpkg: error processing python-metacity (--configure):
 dependency problems - leaving unconfigured
Setting up update-manager (1:0.126.10) ...
Warning: /usr/share/gconf/schemas/update-manager.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing update-manager (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for menu ...
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 aisleriot
 brasero
 metacity-common
 libmetacity0
 compiz-gnome
 compiz
 metacity
 python-metacity
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

Another symptom that I am facing is that stuff like Alt+Tab for changing windows etc does not work. That is probable because of the metacity troubles listed above. I was missing the max, min and close buttons when I recovered and I have manually added those back in through the gconf-editor but still I do not get the program logo's in the top left of the title bars. There is a circle where, for example, the Firefox logo should be.

Barring a helping hand, I am looking to a re-install but the cd on this old laptop is excruciatingly slow :(

Thanks in advance!

PiCaRd359

---

### Post by nitstorm on 2010-07-13
did u try this???

```

sudo apt-get install --fix-missing

```

---

### Post by picard359 on 2010-07-13
> **nitstorm said:**
> did u try this???

```

sudo apt-get install --fix-missing

```

Same result....

---

### Post by picard359 on 2010-07-14
Anyone?? :(

---

### Post by phillw on 2010-07-14
Hi,

if it is a new installation, my advice would be to back up your personal data (i.e. /home) and do a fresh install. Having a seperate /home partition is something advised to keep that area in case of any future crashes [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) has how to do that. 

Another option that *may* work would be to take out the packages that are complaining. It is not overly difficult, but you are going to be delving quite deeply into your system - So, again, a backup would be strongly advised. [http://forum.phillw.net/viewtopic.php?f=4&t=87](http://forum.phillw.net/viewtopic.php?f=4&t=87) has details of taking them out one by one. Starting with metacity, but I'd go for a clean re-install on a new system; that way you'd know you had a 'clean' system with a seperate /home to make things a little easier for backing up in future.

Regards,

Phill.

---

