---
title: "Cruft Remover killed my OpenOffice"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by zika on 2008-11-27
Hello,

Yesterday I've done some upgrade. After that I started Cruft Remover which suggested to remove uno-libs3. I said Yes. That killed my OpenOffice 3.0.

I've tried many things before I've learned from third machine what was the culprit and saved the third but not the second ... ;)

How to reinstall OpenOffice 3.0 on Intrepid64? 

Thanks!

---

### Post by LinuxGuy1234 on 2008-11-27
> **zika said:**
> Hello,

Yesterday I've done some upgrade. After that I started Cruft Remover which suggested to remove uno-libs3. I said Yes. That killed my OpenOffice 3.0.

I've tried many things before I've learned from third machine what was the culprit and saved the third but not the second ... ;)

How to reinstall OpenOffice 3.0 on Intrepid64? 

Thanks!

I'm not sure if one of these commands work, but try:
```

sudo apt-get install openoffice-3.0
sudo apt-get install openoffice3.0-{core,base,writer,math,impress}
sudo apt-get install openoffice-3.0-{core,base,writer,math,impress}

```

---

### Post by Skripka on 2008-11-27
> **LinuxGuy1234 said:**
> I'm not sure if one of these commands work, but try:
```

sudo apt-get install openoffice-3.0
sudo apt-get install openoffice3.0-{core,base,writer,math,impress}
sudo apt-get install openoffice-3.0-{core,base,writer,math,impress}

```

Currently all you can do for OOo3 is wait....you can try downloading the .deb archive and installing them that way...but that is it.

OOo3 is not in the official repos, and the OOo3 PPA repos have been pulled due to problems with GNOME and OOo3 (hopefully they'll be back up in a few days).

---

### Post by zika on 2008-11-27
I get this after trying ...

~$ sudo apt-get install openoffice-3.0
[sudo] password for viktor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice-3.0
~$ sudo apt-get install openoffice-3.0-{core,base,writer,math,impress}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice-3.0-core

I would settle even for reinstalling OpenOffice 2.* that came originally with Ibex. In Synaptic there are traces of OpenOffice 3.0 and when I try to check old OOffice I am warned that there are dependencies that makes that move illegal.

Any help will be greatly appreciated.

---

### Post by Skripka on 2008-11-27
> **zika said:**
> I get this after trying ...

~$ sudo apt-get install openoffice-3.0
[sudo] password for viktor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice-3.0
~$ sudo apt-get install openoffice-3.0-{core,base,writer,math,impress}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice-3.0-core

I would settle even for reinstalling OpenOffice 2.* that came originally with Ibex. In Synaptic there are traces of OpenOffice 3.0 and when I try to check old OOffice I am warned that there are dependencies that makes that move illegal.

Any help will be greatly appreciated.

You'll need to remove the OOo3 trace from Synaptic by hand.  There are some interdependencies of OOo and other defaults on Linux, so be careful what you remove.

---

### Post by zika on 2008-12-24
Watch it! Again today, after weeks of empy list, Cruft remover offered to me to erase uno-libs3. That's how the problem described above started. Of course, I refused but beware ... :smile:

---

