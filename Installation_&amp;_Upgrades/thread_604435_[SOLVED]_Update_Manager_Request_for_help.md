---
title: "[SOLVED] Update Manager: Request for help"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by geeree on 2007-11-06
The Update Manager blinked an icon in my task bar today saying 10 updates were available. But when I clicked on the icon to proceed with the updates, Update Manager said "Software index is broken: It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first." 

I ran Synaptic and also did that apt-get but that did not help. Could someone please explain what is going wrong and tell what could be done to get it right? 

Girish.

---

### Post by squirage on 2007-11-06
Hi,

Same here. It tells me I have updates but that I have broken dependencies. When I typed 

```
sudo apt-get install -f
``` in the terminal I got back:

```
Building dependency tree       
Reading state information... Done 
Correcting dependencies... Done 
The following packages were automatically installed and are no longer required: 
  libmpeg3-1 
Use 'apt-get autoremove' to remove them. 
The following extra packages will be installed: 
  libmiracle0.2.4 libmlt++0.2.4 libmlt-data libmlt0.2.4 libvalerie0.2.4 
The following NEW packages will be installed: 
  libmiracle0.2.4 libmlt++0.2.4 libmlt-data libmlt0.2.4 libvalerie0.2.4 
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded. 
1 not fully installed or removed. 
Need to get 0B/3236kB of archives. 
After unpacking 32.6MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
(Reading database ... 127768 files and directories currently installed.) 
Unpacking libvalerie0.2.4 (from .../libvalerie0.2.4_0.2.4-0ubuntu1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/libvalerie0.2.4_0.2.4-0ubuntu1_i386.deb (--unpack): 
 trying to overwrite `/usr/lib/libvalerie.so.0.2.4', which is also in package mlt 
Unpacking libmlt-data (from .../libmlt-data_0.2.4-0ubuntu1_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/libmlt-data_0.2.4-0ubuntu1_all.deb (--unpack): 
 trying to overwrite `/usr/share/mlt/modules/feeds/PAL/border.properties', which is also in package mlt 
Unpacking libmlt0.2.4 (from .../libmlt0.2.4_0.2.4-0ubuntu1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/libmlt0.2.4_0.2.4-0ubuntu1_i386.deb (--unpack): 
 trying to overwrite `/usr/lib/libmlt.so.0.2.4', which is also in package mlt 
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Unpacking libmiracle0.2.4 (from .../libmiracle0.2.4_0.2.4-0ubuntu1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/libmiracle0.2.4_0.2.4-0ubuntu1_i386.deb (--unpack): 
 trying to overwrite `/usr/lib/libmiracle.so.0.2.4', which is also in package mlt 
Unpacking libmlt++0.2.4 (from .../libmlt++0.2.4_0.2.4~svn1024-0ubuntu2_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/libmlt++0.2.4_0.2.4~svn1024-0ubuntu2_i386.deb (--unpack): 
 trying to overwrite `/usr/lib/libmlt++.so.0.2.4', which is also in package mlt++ 
Errors were encountered while processing: 
 /var/cache/apt/archives/libvalerie0.2.4_0.2.4-0ubuntu1_i386.deb 
 /var/cache/apt/archives/libmlt-data_0.2.4-0ubuntu1_all.deb 
 /var/cache/apt/archives/libmlt0.2.4_0.2.4-0ubuntu1_i386.deb 
 /var/cache/apt/archives/libmiracle0.2.4_0.2.4-0ubuntu1_i386.deb 
 /var/cache/apt/archives/libmlt++0.2.4_0.2.4~svn1024-0ubuntu2_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I upgraded to gutsy to see if I could get kdenlive working. The upgrade trashed my sound, screwed up youtube (flash video) in firefox and now rhythm box and all of my media players don't work. I even installed Listen and it would not work.

I removed and re-installed gxine, rhythmbox and kdenlive and theystill don't work. I had installed mlt and mlt++ under fiesty to get kdenlive going in the first place.

Right now I feel like a hamster on a wheel with this stuff.

---

### Post by squirage on 2007-11-06
Hey geeree,

  Try looking at the broken filter setting in synaptic, it may give you an idea of what specifically is causing the problem.

For me it was kdenlive. When I tried to either re-install or remove it gave me a similar error message with regards to the mlt and mlt++ dependencies. It would not overwrite them.

So I went back to the terminal and typed.

```
sudo apt-get --purge remove mlt mlt++ kdenllive
```

after rebooting I ran update manager from the taskbar icon and it ran those ten updates as they should.

Hope this helps you.

---

### Post by geeree on 2007-11-07
Thanks squirage, a sort of similar thing helped. 
```
sudo apt-get -f install
```
kept telling me about a dpkg failure with a package called Alexandria. (dpkg had failed to remove this pakage.) It turned out that the error was due to the post-removal script that dpkg ran after removing Alexandria. I corrected the script and everything is fine now. 

This article helped: [http://www.linux.com/articles/48910](http://www.linux.com/articles/48910); as also Cathal Mc Ginley ([http://www.gnostai.org/](http://www.gnostai.org/)) of Alexandria! 

Girish.

---

### Post by squirage on 2007-11-08
Hi geeree,

  I'm glad you found a solution, you may want to mark the thread as solved.

---

