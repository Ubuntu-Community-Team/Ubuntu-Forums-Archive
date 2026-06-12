---
title: "sources"
date: 2020-07-11
forum: Installation &amp; Upgrades
---

### Post by olavh70 on 2020-07-11
What decides where ubuntu will look for sources -> /etc/apt/sources/ or /etc/apt/sources.list.d/ ?  How to prevent double sources same application/program which sudo apt-get update complains about. Should one choose one type of installation over the other? Like sudo apt-get install or dpkg in order to avoid double set of sources?

---

### Post by deadflowr on 2020-07-11
If proper list files are in the proper locations it looks at all of those.
The is done by apt.
I'm not sure if it's hardcoded or if a configuration file does this.

If you have double entries/duplicates then you need to remove the duplicate entries.

Use apt over dpkg.
dpkg is low-level, as it does the actual package installation.
But it does not handle downloading package and does not handle package dependency issues.
apt does both.

---

### Post by ActionParsnip on 2020-07-11
Easy, don't add duplicates. There is a main sources.list file but add-apt-repository likes to make files in /etc/apt/sources.list.d
You could just have all your sources in the usual sources.list file and it'd be exactly the same. Breaking it out into files just makes it easier to manage as you can delete a file and remove a source. If duplicates exist in any of the files then the package system will complain.

---

### Post by CatKiller on 2020-07-12
To aid in understanding, that kind of change is fairly common. It's not specific to apt.

Some application or framework is configured by a single configuration file and, at some point, that gets unwieldy to manage. Things are then amended so that the application or framework will read from both blah.conf and any similarly-formatted files in blah.conf.d, and combine them into one configuration at runtime. You'll find examples all over your install, xorg.conf.d being the other significant one.

---

### Post by grahammechanical on 2020-07-12
This is what the man page says:

> SOURCES.LIST.D
       The /etc/apt/sources.list.d directory provides a way to add
       sources.list entries in separate files.

The contents of this directory are not a copy of the apt directory. If an application has its own repository and the location file has the suffix .list then that file will end up in the apt/sources.list.d directory. On my system I have in that directory google-chrome.list and google-chrome.list.save and this is because I have google chrome installed.

I guess this is a way of avoiding the operating system's sources.list file from becoming even more complicated. I think that the files in apt/sources.d are not vital for the updating of the operating system as is the case with the information in the sources.list file itself.

Regards

---

### Post by michael2009 on 2020-09-02
I have a problem with duplicate sources when running apt-get update after using Ubuntuzilla to update my UbuntuGnome 14.04 repositories for the latest Firefox (ver. 80). 

Can anyone here help me remove these or solve the problem?

The terminal is showing this:

W: There is no public key available for the following key IDs:
CCC158AFC1289A29
W: Duplicate sources.list entry [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main amd64 Packages (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main amd64 Packages (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main i386 Packages (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main i386 Packages (/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages)

---

### Post by wildmanne39 on 2020-09-02
Hello michael2009, please start your own thread instead of posting in someone else's that way you and the OP of this thread can both get the help individual help you need.

Thanks

---

### Post by michael2009 on 2020-09-04
> **wildmanne39 said:**
> Hello michael2009, please start your own thread instead of posting in someone else's that way you and the OP of this thread can both get the help individual help you need.

Thanks

OK. Not my intention to crash someone else's thread, I just thought the thread was relevant to my problem, and looking for answers here. Will post a new thread anyway.

---

