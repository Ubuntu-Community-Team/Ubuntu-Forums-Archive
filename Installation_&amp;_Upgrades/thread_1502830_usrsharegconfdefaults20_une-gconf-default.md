---
title: "/usr/share/gconf/defaults/20_une-gconf-default"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by dr_smit on 2010-06-06
I carried out instruction at [https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession](https://help.ubuntu.com/community/UbuntuNetbookEdition/ConvertGnomeSession) but mistakenly for 3D, upon carrying out for 2D, it said that the links exists so I deleted few things at '/usr/share/gconf/defaults/20_une-gconf-default' and went ahead for 2D codes.. 

I ended with no nautilus, no proper updating and these many errors..
Please help me solve this mess and be back to enjoying UNR to fullest..:guitar:

dr-smit@dr-smit-netbook:~$ sudo apt-get install -f
[sudo] password for dr-smit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  nautilus-data rhythmbox totem-common
Suggested packages:
  python-coherence rhythmbox-plugin-coherence
The following packages will be upgraded:
  nautilus-data rhythmbox totem-common
3 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
10 not fully installed or removed.
Need to get 723kB/6,683kB of archives.
After this operation, 115kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  gnome-do nautilus-data rhythmbox totem-common
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe gnome-do 0.8.3.1+dfsg-1ubuntu1 [497kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main totem-common 2.30.2-0ubuntu1 [226kB]                             
Fetched 723kB in 21s (33.7kB/s)                                                                                             
(Reading database ... 350978 files and directories currently installed.)
Preparing to replace gnome-do 0.8.3.1+dfsg-1ubuntu1 (using .../gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb) ...
Unpacking replacement gnome-do ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error processing /var/cache/apt/archives/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Preparing to replace nautilus-data 1:2.30.1-0ubuntu1 (using .../nautilus-data_1%3a2.31.1-0ubuntu1~ppa89_all.deb) ...
Unpacking replacement nautilus-data ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error processing /var/cache/apt/archives/nautilus-data_1%3a2.31.1-0ubuntu1~ppa89_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Preparing to replace rhythmbox 0.12.8-0ubuntu4 (using .../rhythmbox_0.12.8-0ubuntu5_i386.deb) ...
Unpacking replacement rhythmbox ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error processing /var/cache/apt/archives/rhythmbox_0.12.8-0ubuntu5_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Preparing to replace totem-common 2.30.1-0ubuntu1 (using .../totem-common_2.30.2-0ubuntu1_all.deb) ...
Unpacking replacement totem-common ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error processing /var/cache/apt/archives/totem-common_2.30.2-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for menu ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-do_0.8.3.1+dfsg-1ubuntu1_i386.deb
 /var/cache/apt/archives/nautilus-data_1%3a2.31.1-0ubuntu1~ppa89_all.deb
 /var/cache/apt/archives/rhythmbox_0.12.8-0ubuntu5_i386.deb
 /var/cache/apt/archives/totem-common_2.30.2-0ubuntu1_all.deb
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Packages (/var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Packages (/var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Packages (/var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_non-free_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-mozilla-daily_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_pidgin-developers_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_lucid_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
dr-smit@dr-smit-netbook:~$ sudo update-gconf-defaults
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dr-smit@dr-smit-netbook:~$ sudo ln -s /etc/xdg/xdg-une/autostart/maximus-autostart.desktop /etc/xdg/autostart/
ln: creating symbolic link `/etc/xdg/autostart/maximus-autostart.desktop': File exists
dr-smit@dr-smit-netbook:~$ sudo ln -s /etc/xdg/xdg-une-efl/autostart/netbook-launcher-efl.desktop /etc/xdg/autostart/
ln: creating symbolic link `/etc/xdg/autostart/netbook-launcher-efl.desktop': File exists
dr-smit@dr-smit-netbook:~$ sudo ln -s /usr/share/gconf/une/default/20_une-gconf-default /usr/share/gconf/defaults/
ln: creating symbolic link `/usr/share/gconf/defaults/20_une-gconf-default': File exists
dr-smit@dr-smit-netbook:~$ sudo ln -s /usr/share/gconf/une/mandatory/20_une-gconf-mandatory /usr/share/gconf/defaults/
ln: creating symbolic link `/usr/share/gconf/defaults/20_une-gconf-mandatory': File exists
dr-smit@dr-smit-netbook:~$ sudo update-gconf-defaults
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dr-smit@dr-smit-netbook:~$ ^C
dr-smit@dr-smit-netbook:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

---

### Post by dr_smit on 2010-06-06
Found a solution
[http://www.ubuntu-se.org/phpBB3/viewtopic.php?t=48648](http://www.ubuntu-se.org/phpBB3/viewtopic.php?t=48648)
Its in swedish I google translated it
Step 1 - Live boot 
Step 2 - Replace files that the link indicates from live boot

Now please help me do it by translating it to plain step by step English:)

---

### Post by dr_smit on 2010-06-10
I need a copy of Ubuntu Lucid installation - 20_une-gonf-default..
Please post it here

---

### Post by dr_smit on 2010-06-12
It all got sorted out after

~$ sudo aptitude update && sudo aptitude full-upgrade

Thanks for help..
SOLVED!

---

