---
title: "Google Earth Installation"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by jollyrancher on 2012-09-02
Hi All,

I am trying to install Google Earth on my 12.04 x64 Ubuntu, but there seems to be some issues:

I tried following the recommendations in _[this thread]("http://ubuntuforums.org/showthread.php?t=1548880")_.  In particular, I installed medibuntu.  However, contrary to this thread there is no option to install google earth as a medibuntu package in the Synaptic Package Manager.  

So I then tried to install the googleearth-package, the utility which allows you to build your own Debian package of Google Earth.  I then executed the "sudo make-googleearth-package --force" in /usr/bin, which worked.  So I installed the package "sudo dpkg -i googleearth_6.0.3.2197+0.7.0-1_amd64.deb" which produced:

> Selecting previously unselected package googleearth.
(Reading database ... 330570 files and directories currently installed.)
Unpacking googleearth (from googleearth_6.0.3.2197+0.7.0-1_amd64.deb) ...
dpkg: error processing --force (--install):
 cannot access archive: No such file or directory
Setting up googleearth (6.0.3.2197+0.7.0-1) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'

When I open up the google earth program, only the loading screen appears.  Nothing happens after that.

Does any one know where I went wrong?

i.e. 

1) Why didn't google earth show up in the synaptic package manager after installing medibuntu, and
2) Why doesn't it execute using the debian package builder?  Is it related to the unknown media output?

Thanks in advance,

---

### Post by Petro Dawg on 2012-09-02
Maybe give this a try...

Open the terminal and run the following command to download the Google 6.2 package

```
wget http://dl.google.com/dl/earth/client/current/google-earth-stable_current_amd64.deb
```

run the below command to install Google 6.2

```
sudo dpkg -i google-earth-stable_current_amd64.deb
```

Run below command in case of any dependency issue

```
sudo apt-get install -f
```

I just tried it and it worked for me, hopefully works for you too.

---

### Post by jollyrancher on 2012-09-03
Thanks Dawg.... Unfortunately this didn't work.  It ended up being a driver issue I think.  Seems to be working now!  But I appreciate your help.

---

