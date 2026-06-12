---
title: "install opera using 16.04 32 bit"
date: 2017-03-30
forum: Installation &amp; Upgrades
---

### Post by gibbywilson on 2017-03-30
firstly i apologize if this has been "solved" in other threads but I just can't seem to find a solution for my system - 16.04 32 bit

I have tried several times to follow other installation guides using the terminal and they all fail

Could someone please walk me through how to install the latest opera browser (and for it to update automatically)

I am a newbie but I can copy and paste code :)

Thanks

Gibby

---

### Post by howefield on 2017-03-31
An idea of how they "fail" would be useful, some one might be able to tell you why.

I would go here and download the relevant .deb package to the downloads folder, in your case the file ending in "_i386.deb" then install with apt.

```
sudo apt install --no-install-recommends ~/Downloads/opera-stable_44.0.2510.857_amd64.deb 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'opera-stable' instead of '/home/hugh/Downloads/opera-stable_44.0.2510.857_amd64.deb'
The following package was automatically installed and is no longer required:
  libmagickcore-6.q16-2
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libpango1.0-0 libpangox-1.0-0
Recommended packages:
  pepperflashplugin-nonfree
The following NEW packages will be installed
  libpango1.0-0 libpangox-1.0-0 opera-stable
0 to upgrade, 3 to newly install, 0 to remove and 38 not to upgrade.
Need to get 44.9 kB/52.1 MB of archives.
After this operation, 182 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libpangox-1.0-0 amd64 0.0.2-5 [41.7 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libpango1.0-0 amd64 1.40.4-1 [3,258 B]
Get:3 /Data/Downloads/opera-stable_44.0.2510.857_amd64.deb opera-stable amd64 44.0.2510.857 [52.1 MB]
Fetched 44.9 kB in 0s (46.0 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libpangox-1.0-0:amd64.
(Reading database ... 181005 files and directories currently installed.)
Preparing to unpack .../libpangox-1.0-0_0.0.2-5_amd64.deb ...
Unpacking libpangox-1.0-0:amd64 (0.0.2-5) ...
Selecting previously unselected package libpango1.0-0:amd64.
Preparing to unpack .../libpango1.0-0_1.40.4-1_amd64.deb ...
Unpacking libpango1.0-0:amd64 (1.40.4-1) ...
Selecting previously unselected package opera-stable.
Preparing to unpack .../opera-stable_44.0.2510.857_amd64.deb ...
Unpacking opera-stable (44.0.2510.857) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu2) ...
Processing triggers for bamfdaemon (0.5.3+16.10.20160929-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up libpangox-1.0-0:amd64 (0.0.2-5) ...
Processing triggers for shared-mime-info (1.8-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.15-1) ...
Setting up libpango1.0-0:amd64 (1.40.4-1) ...
Setting up opera-stable (44.0.2510.857) ...
update-alternatives: using /usr/bin/opera to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/man1/x-www-browser.1.gz because associated file /usr/share/man/man1/opera.1.gz (of link group x-www-browser) doesn't exist
update-alternatives: using /usr/bin/opera to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
update-alternatives: warning: skip creation of /usr/share/man/man1/gnome-www-browser.1.gz because associated file /usr/share/man/man1/opera.1.gz (of link group gnome-www-browser) doesn't exist
Processing triggers for libc-bin (2.24-7ubuntu2) ...
```

I've used the --no-install-recommends option so it doesn't try to install pepperflash as I use adobe-flashplugin from the Partners repository.

You will also during the installation be prompted to answer whether or not you want Opera to be updated along with the rest of the system, selecting yes will add the Opera repository information to your sources.

---

### Post by gibbywilson on 2017-03-31
Thanks 

that has worked

---

### Post by howefield on 2017-04-01
> **gibbywilson said:**
> Thanks 

that has worked

Cool, glad you got it, feel free to mark the thread as solved.

I missed the download link from my post above, it is [https://ftp.opera.com/pub/opera/desktop/](https://ftp.opera.com/pub/opera/desktop/) click through to linux then scroll down to the latest version which is currently 44.0.2510.857.  

Can be useful to know this site as the automatic download can sometimes offer the wrong package, eg .rpm instead of .deb package.

---

