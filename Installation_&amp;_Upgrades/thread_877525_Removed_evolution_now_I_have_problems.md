---
title: "Removed evolution now I have problems"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by Martym on 2008-08-01
So I removed evolution last night and now I have several issues becuae it took gnome-applets, gnome-panel, ubuntu desktop, fast user switching alacarte, ekiga and libdataserverui1.2-8 with it.  I reinstalled the gnome stuff and tried to reinstall ubuntu-desktop but it decided to change that to Ubuntu-studio.

so today I took my laptop to a meeting and it would not boot.  I had to go to the recovery mode then choose boot normally.  I have lost the icons for my mounts and I cannot re-install Evolution or ubuntu-desktop to get things back to how they were.

Through Synaptic, installing Evoultion I get the following:

```

evolution:
 Depends: evolution-data-server but it is not going to be installed

evolution-data-server:
  Depends: libedata-book1.2-2 (>=2.22.3) but 2.22.2-0ubuntu2 is to be installed
  Depends: libedata-cal1.2-6 (>=2.22.3) but 2.22.2-0ubuntu2 is to be installed
  Depends: libegroupwise1.2-13 (>=2.22.3) but 2.22.2-0ubuntu2 is to be installed
  Depends: libgdata-google1.2-1 (>=2.22.3) but 2.22.2-0ubuntu2 is to be installed
  Depends: libgdata1.2-1 (>=2.22.3) but 2.22.2-0ubuntu2 is to be installed

```

Oh yeah I was trying to install the data-server at the same time.

When I try to install ubuntu-desktop I get something similar:

```
ubuntu-desktop:
 Depends: ubuntu-sounds but it is not going to be installed
 Recommends: ekiga but it is not going to be installed
 Recommends: evolution but it is not going to be installed
 Recommends: evolution-exchange but it is not going to be installed
 Recommends: evolution-plugins but it is not going to be installed
```

Please help me get things back to normal.

---

### Post by pytheas22 on 2008-08-01
Does this work:
```

sudo apt-get install evolution
```

If not, please post the output of the whole thing?

---

### Post by Linja on 2008-08-01
Sounds like your software sources are messed up. Check Admin > software sources to make sure that you have not got any development repositories enabled. Next thing you can try is open Synaptic and choose Edit > Fix broken.

Do not remove evolution-data-server. In fact, I'm surprised it let you. You can remove all the evolution stuff (I do too) but that one part is too crucial to the proper functioning other applications to be ripped out.

---

### Post by Martym on 2008-08-02
Yeah I was a bit surprised myself about the data server.  I did manage to get things back to (mostly) normal using the apt-get.  I had to add ubuntu-desktop and ubuntu-sounds in the command so that is no longer a problem.  I am still having an issue with the laptop not wanting to boot.  I get an Ubuntu Studio splash screen (which I will replace with mine later) and then a blank screen with only an occasional bit of HD activity.

When I tried to remove evolution all I selected was Evolution and the Web calendar.  It took everything else with it and I was too distracted to realise it was a mistake until after the fact.

I do not see and dev sources on the list.

Thank you both for the help, it is appreciated

---

