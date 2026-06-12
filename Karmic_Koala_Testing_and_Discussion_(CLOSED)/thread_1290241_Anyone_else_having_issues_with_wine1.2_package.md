---
title: "Anyone else having issues with wine1.2 package?"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by beastrace91 on 2009-10-13
Hey All,

So I am trying to install the Wine Beta package on Karmic and it keeps giving a cannot connect to server error - I've tried the software center, synaptic, and terminal. Here is the output from the later of the three ```
jeff@eeetop:~$ sudo apt-get install wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-assistant libmuparser0 libuser-perl gdesklets-data libqt4-test
  libqwt5-qt4 python-numeric libcarp-clan-perl python-utidylib
  python-gtkmozembed libqt4-xmlpatterns libtidy-0.99-0 libqt4-help python-qt4
  python-soappy python-sip4 python-feedparser hddtemp python-rsvg
  libdate-manip-perl libwww-search-perl libfile-slurp-perl python-fpconst
  python-evolution python-wnck liborigin0 libqt4-scripttools python-chardet
  libqwtplot3d-qt4 libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmpg123-0 libopenal1 ttf-symbol-replacement ttf-tahoma-replacement
  wine1.2-gecko
The following packages will be REMOVED:
  wine wine-gecko
The following NEW packages will be installed:
  libmpg123-0 libopenal1 ttf-symbol-replacement ttf-tahoma-replacement wine1.2
  wine1.2-gecko
0 upgraded, 6 newly installed, 2 to remove and 107 not upgraded.
Need to get 9,875kB/18.5MB of archives.
After this operation, 26.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://us.archive.ubuntu.com karmic/universe ttf-symbol-replacement 1.1.30-0ubuntu4
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic/universe ttf-tahoma-replacement 1.1.30-0ubuntu4
  404  Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com karmic/universe wine1.2 1.1.30-0ubuntu4
  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.1.30-0ubuntu4_all.deb  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-tahoma-replacement_1.1.30-0ubuntu4_all.deb  404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.1.30-0ubuntu4_i386.deb  404  Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

apt-get update went off with out a hitch as did installing the "stable" version of Wine (which works for now) but I would like the latest release. Any suggestions on how I can get this working? (I would like to avoid compiling from source as this is on my netbook with limited hard drive space.

Thanks,
~Jeff

---

### Post by RavenHollow on 2009-10-13
Add Wine repository to Synaptic or download / install manually.  Instructions on the Wine website here:  [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) ...

Had some graphics issues with 1.1.30, so am still running 1.1.29.  Would be interested to hear how 1.1.31 works for ya.

Best,
-- Jake

---

### Post by LKjell on 2009-10-13
Did you try another mirror?

---

### Post by dino99 on 2009-10-13
Every time i have such problem, first i clean the cache:

sudo aptitude clean / autoclean
sudo apt-get autoremove

then, try again

sudo aptitude update
sudo aptitude install -f
sudo aptitude safe-upgrade

---

### Post by Regenweald on 2009-10-13
Try aptitude. My install went fine, but the new utorrent simply will not work. The system tray integration is problematic also.

---

### Post by beastrace91 on 2009-10-13
> **RavenHollow said:**
> Add Wine repository to Synaptic or download / install manually.  Instructions on the Wine website here:  [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) ...

Last I checked (day or so ago) that repo did not work for Karmic. Has this changed/do you know somewhere that has .deb files posted I can install with?...

@dino99 I'll give clearing the cache a try.

~Jeff

---

### Post by beastrace91 on 2009-10-13
Clearing the cache also did not work. I guess I'll just hang tight until until Karmic "releases" at the end of the month and gets a listing in the official Wine repo

~Jeff

---

### Post by RavenHollow on 2009-10-13
The repositories work for me, showing 1.1.31 is available.  There is no Karmic specific arg yet, so use jaunty instead.

You can get the packages manually here:  [http://wine.budgetdedicated.com/apt/pool/main/w/wine/](http://wine.budgetdedicated.com/apt/pool/main/w/wine/).  Download the correct .deb (32 or 64 bit) and then issue dpkg -i <wine_1.1.31~winehq0 ... .deb> to install.

Let me know how 1.1.31 works for ya.

-- Jake

---

