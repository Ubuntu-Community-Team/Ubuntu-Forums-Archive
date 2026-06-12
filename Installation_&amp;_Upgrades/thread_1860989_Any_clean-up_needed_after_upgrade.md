---
title: "Any clean-up needed after upgrade?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Jeinhor on 2011-10-15
The other day I installed 11.04 and then upgraded to the latest beta (11.10 beta 2). I then had some problems where I couldn't boot into 11.10 beta 2, but to my surprise I could still boot into 11.04 using the GRUB boot menu.

That's neat, but is there some way to delete all older versions of Ubuntu so that I only have the latest? If I upgrade from Ubuntu 11.04 to Ubuntu 11.10 (final), will Ubuntu 11.04 be left on my HDD as well?

Thanks in advance!

---

### Post by Jeinhor on 2012-04-24
I am still wondering this, especially now when I soon will be upgrading from Ubuntu 11.10 to Ubuntu 12.04. 

Anyone?

---

### Post by dog-soldier on 2012-04-24
if it was me i would do a clean install. burn the iso to disc or thumb drive and start fresh.
thats what i have always done and never had a problem.

---

### Post by 23dornot23d on 2012-04-24
Do this in a terminal on both systems ..... and post back the results please .....

**lsb_release -a**
[B]uname -a
[/B]
for example this is what mine returns ...... *( it will let you know if you are running two
versions .... or different kernels .... 
I suspect its different kernels .... as a upgrade will leave older kernel links in the 
grub menu .....

> 
keith@keith-K53SV:~$[COLOR=Blue]**lsb_release -a**
[/COLOR]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise
keith@keith-K53SV:~$ 
keith@keith-K53SV:~$ [COLOR=Blue]**uname -a**[/COLOR]
Linux keith-K53SV 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux




---

### Post by YannBuntu on 2012-04-24
> **Jeinhor said:**
> is there some way to delete all older versions of Ubuntu so that I only have the latest?

If you upgrade, you will only have the latest system. BUT the old kernels (and maybe some other stuff as upgrade is not always perfect) will remain. 2 options to get a clean system:
- either a fresh install, as recommended by dog-soldier.
- or a reinstall which preserves the settings, see [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) 

> **Jeinhor said:**
> If I upgrade from Ubuntu 11.04 to Ubuntu 11.10 (final), will Ubuntu 11.04 be left on my HDD as well?

same answer as above.

---

### Post by Jeinhor on 2012-04-24
I suspected there might be some files left..

Here's the output of the requested commands:

```

dev@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
dev@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by 23dornot23d on 2012-04-25
If you need to remove older kernels you can ...

but it is usually the case that 2 are left ... just as a way of getting in say the latest one does not work as well ......

There are a few tools for tidying up ..... [COLOR=Red]**First read what they will do**[/COLOR]

[[COLOR=Blue]_**Bleachbit**_[/COLOR]]("https://www.google.com/search?client=ubuntu&channel=fs&q=Bleachbit++ubuntu+11.10&ie=utf-8&oe=utf-8") .....
[[COLOR=Blue]_**Gnome-Tweak-tool **_[/COLOR]]("http://www.n00bsonubuntu.net/content/install-guide-gnome-tweak-tool-on-ubuntu-11-10/")
[[COLOR=Blue]_**Computer Janitor**_[/COLOR]]("https://www.google.com/search?client=ubuntu&channel=fs&q=Computer+Janitor+ubuntu+11.10&ie=utf-8&oe=utf-8")

I have heard differing reports on each of these ..... but they are tools to clean up and if
they work ok for you they are a lot simpler than doing it manually .....

Some of the more manual things ...

[[COLOR=Blue]_**apt-get clean**_[/COLOR]]("https://www.google.com/search?client=ubuntu&channel=fs&q=apt-get+clean+ubuntu+11.10&ie=utf-8&oe=utf-8")
apt-get autoclean
[[COLOR=Blue]_**apt-get autoremove**_[/COLOR]]("https://www.google.com/search?client=ubuntu&channel=fs&q=apt-get+autoclean+ubuntu+11.10&ie=utf-8&oe=utf-8")

But with all of the above [COLOR=Red]**First read what they will do**[/COLOR] ....... 
then use only if you are
sure that you need the space ...... 

( my philosophy is not to remove things - until I come to my last 1 Gig ..... )

But this is entirely up to you and what works best for you ...... ;)

Hope this helps in some way .... there is always the manual way but again it
needs care ..... and some reading up ..... if in doubt leave things till you need
some space .... but have the clean up packages installed ready to use.

sudo apt-get install bleachbit
sudo apt-get install computer-janitor
sudo apt-get install gnome-tweak-tool


Following my own advice below .....
```

keith@keith-Aspire-7730ZG:~/.config$ [COLOR=Red]sudo apt-get install bleachbit[/COLOR]
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  menu
Suggested packages:
  menu-l10n
The following NEW packages will be installed:
  bleachbit menu
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 772 kB of archives.
After this operation, 3,546 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://fr.archive.ubuntu.com/ubuntu/ precise/universe menu i386 2.1.46ubuntu1 [445 kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ precise/universe bleachbit all 0.9.1-1 [327 kB]
Fetched 772 kB in 1s (580 kB/s)
Selecting previously unselected package menu.
(Reading database ... 247578 files and directories currently installed.)
Unpacking menu (from .../menu_2.1.46ubuntu1_i386.deb) ...
Selecting previously unselected package bleachbit.
Unpacking bleachbit (from .../bleachbit_0.9.1-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up menu (2.1.46ubuntu1) ...
Processing triggers for menu ...
Setting up bleachbit (0.9.1-1) ...
Processing triggers for menu ...
keith@keith-Aspire-7730ZG:~/.config$ [COLOR=Red]sudo apt-get install computer-janitor[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  computer-janitor
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 34.6 kB of archives.
After this operation, 336 kB of additional disk space will be used.
Get:1 http://fr.archive.ubuntu.com/ubuntu/ precise/main computer-janitor all 2.1.0-0ubuntu8 [34.6 kB]
Fetched 34.6 kB in 0s (121 kB/s)          
Selecting previously unselected package computer-janitor.
(Reading database ... 247918 files and directories currently installed.)
Unpacking computer-janitor (from .../computer-janitor_2.1.0-0ubuntu8_all.deb) ...
Processing triggers for man-db ...
Setting up computer-janitor (2.1.0-0ubuntu8) ...
keith@keith-Aspire-7730ZG:~/.config$ [COLOR=Red]sudo apt-get install gnome-tweak-tool[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-tweak-tool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
keith@keith-Aspire-7730ZG:~/.config$ 


```

---

