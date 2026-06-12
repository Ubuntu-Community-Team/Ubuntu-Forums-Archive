---
title: "update failures"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by kinkdxm on 2007-11-17
sorry if this in not in the right category.

7.10 told me I had 28 ish new updates when I did them I got this at the end after it was installing them.

E: eog: subprocess post-installation script returned error exit status 139
E: evince: subprocess post-installation script returned error exit status 139
E: file-roller: subprocess post-installation script returned error exit status 139
E: gcalctool: subprocess post-installation script returned error exit status 139
E: gnome-menus: subprocess post-installation script returned error exit status 139
E: sound-juicer: subprocess post-installation script returned error exit status 139
E: evolution-common: subprocess post-installation script returned error exit status 139
E: evolution: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: gnome-session: subprocess post-installation script returned error exit status 139
E: gedit: subprocess post-installation script returned error exit status 139
E: gnome-about: subprocess post-installation script returned error exit status 139
E: gnome-games: subprocess post-installation script returned error exit status 139

---

### Post by zvacet on 2007-11-17
```
sudo aptitude -f install
```

or go to the **synaptic>edit>fix broken packages**

---

### Post by kinkdxm on 2007-11-17
cool thanks!

hmm i did that and i think it may not have worked. I dunno it's saying stuff about core dumps.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libqt4-core libqt4-gui par2 python-twisted-bin python-twisted-core 
  python-twisted-web python-zopeinterface 
The following partially installed packages will be configured:
  eog evince evolution evolution-common evolution-plugins file-roller 
  gcalctool gedit gnome-about gnome-games gnome-menus gnome-session 
  sound-juicer 
0 packages upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 25.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 110058 files and directories currently installed.)
Removing libqt4-gui ...
Removing libqt4-core ...
Removing par2 ...
Removing python-twisted-web ...
Removing python-twisted-core ...
Removing python-twisted-bin ...
Removing python-zopeinterface ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up eog (2.20.1-0ubuntu1) ...

(update-desktop-database:28134): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.20.1-0ubuntu1) ...

(update-desktop-database:28163): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.12.1-0ubuntu1) ...

(update-desktop-database:28187): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.12.1-0ubuntu1); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up file-roller (2.20.1-0ubuntu1) ...

(update-desktop-database:28205): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.20.2-0ubuntu1) ...

(update-desktop-database:28232): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit (2.20.3-0ubuntu1) ...

(update-desktop-database:28255): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gedit (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-about (1:2.20.1-0ubuntu1) ...

(update-desktop-database:28270): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-about (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-games (1:2.20.1-0ubuntu1) ...

(update-desktop-database:28276): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-games (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-menus (2.20.1-0ubuntu1) ...

(update-desktop-database:28281): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-menus (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-session (2.20.1-0ubuntu1) ...

(update-desktop-database:28313): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-session (--configure):
 subprocess post-installation script returned error exit status 139
Setting up sound-juicer (2.20.1-0ubuntu1) ...

(update-desktop-database:28342): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 eog
 evince
 evolution-common
 evolution
 evolution-plugins
 file-roller
 gcalctool
 gedit
 gnome-about
 gnome-games
 gnome-menus
 gnome-session
 sound-juicer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up eog (2.20.1-0ubuntu1) ...

(update-desktop-database:28374): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit (2.20.3-0ubuntu1) ...

(update-desktop-database:28396): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gedit (--configure):
 subprocess post-installation script returned error exit status 139
Setting up sound-juicer (2.20.1-0ubuntu1) ...

(update-desktop-database:28422): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-games (1:2.20.1-0ubuntu1) ...

(update-desktop-database:28438): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-games (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-menus (2.20.1-0ubuntu1) ...

(update-desktop-database:28443): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-menus (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.20.2-0ubuntu1) ...

(update-desktop-database:28459): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.20.1-0ubuntu1) ...

(update-desktop-database:28488): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-session (2.20.1-0ubuntu1) ...

(update-desktop-database:28521): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-session (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.20.1-0ubuntu1) ...

(update-desktop-database:28552): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-about (1:2.20.1-0ubuntu1) ...

(update-desktop-database:28557): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gnome-about (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.12.1-0ubuntu1) ...

(update-desktop-database:28568): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.12.1-0ubuntu1); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 eog
 gedit
 sound-juicer
 gnome-games
 gnome-menus
 gcalctool
 evince
 gnome-session
 file-roller
 gnome-about
 evolution-common
 evolution
 evolution-plugins
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by zvacet on 2007-11-18
```
sudo dpkg --configure -a
```

or just try to install evolution-common with synaptic or from here 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=evolution-common&searchon=names&subword=1&version=feisty&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=evolution-common&searchon=names&subword=1&version=feisty&release=all")

---

### Post by jsbarnes1002 on 2007-11-20
I'm having this same problem.  Did you ever fix it?

---

### Post by Wd2048 on 2007-11-21
I'm having some similar problems... not exactly the same packages... I think it has to do with authority, from what i have been able to discern.

I could be way off, but basically the authorities didn't get set correctly with your new kernel when it loaded... I'm still trying to figure out how to fix it.

---

### Post by tonycm1 on 2008-01-01
I'm having the same problem

> tony@tony-laptop:~$ sudo apt-get -f install
[sudo] password for tony:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bluez-gnome
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 745kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 129774 files and directories currently installed.)
Removing bluez-gnome ...

(update-desktop-database:25407): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing bluez-gnome (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 bluez-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ 


Then I tried sudo dpkg --configure -a.... and got the same problem :(

> tony@tony-laptop:~$ sudo dpkg --configure -a
Setting up deluge-torrent (0.5.8-1) ...

(update-desktop-database:4668): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing deluge-torrent (--configure):
 subprocess post-installation script returned error exit status 139
Setting up kdebase-bin (4:3.5.8-0ubuntu2) ...

(update-desktop-database:5806): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kdebase-bin (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdebase-bin; however:
  Package kdebase-bin is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 deluge-torrent
 kdebase-bin
 k3b
tony@tony-laptop:~$ 


---

### Post by asan on 2008-01-02
I had similiar issues - this is what I did - this post.  Important that you sudo to root to do this.

[http://ubuntuforums.org/showthread.php?p=4034051#post4034051](http://ubuntuforums.org/showthread.php?p=4034051#post4034051)

Thom

---

### Post by tonycm1 on 2008-01-02
I'll give this a try when I get home after work

What exactly does this do though? (for my curiosity's sake)

> Ok guys - here's what seemed to fix this - simple - maybe not elegant - but works....

go to /tmp, delete (rm) .X0-lock
go in to terminal mode - or ctl & Alt & F1 (terminal)
sudo su (to root)
type " dpkg configure -a " w/o the quotes of course....

Seems there is some kind of permission error running it via update manager and synaptic once update manager has failed....

---

### Post by asan on 2008-01-02
the /tmp folder - home of most temporary files

rm (remove or delete) the .XO-lock  this file is for the x-server - your current or last session - for me it was my last session and it didn't work (the x-server) so deleting the .XO-lock file made it so the next time I logged in via the X-server it would 'create' a new session for me.

Ctrl & Alt & F1 together put in you terminal native mode.  You have to log in just like in a 'regular' linux environment.

sudo su - you have to be 'root' to execute the comands.  sudo = Pseduo Root user.

dpkg configure -a      [  basically configure a linux package (or in RedHat an - RPM file), other linux flavors I am not sure what they are called....]  You've seen the .conf files, this is what the program/code/RPM/package uses to decide how to 'act' with the particualr linux distro.  You need to Configure the Package....

Now, what I did was only w/Gnome & associated programs.  I did have segmentation faults and core dumps early on.  I re-ran synaptic and I fixed tzdata (see my earlier post) and that seemed to fix the core dumps and segment faults....  I do not know if this method will fix your issue - but I thought it might give you a starting point...

Thom

---

### Post by asan on 2008-01-02
Ahh-  I forgot to mention how to fix the tzdata...

I saw a few posts on this and it seems to depend on what 'frontend' you are using or the 'flavor' of the CD.  I was using the alternate CD.  For me, setting the time zone to Berlin, then restarting the server.  For others it seems setting the time zone to London worked.  sudo su dpkg configure -a and that fixed the tzdata package.  Then I set the correct time zone.  I then restarted the server again...and did the above.

Now - I did SEE a new tzdata package today on the updates - this perhaps fixes the original tzdata issue - I don't know as mine already worked..worth looking in to if you are still having issues.....

Thom

---

### Post by tonycm1 on 2008-01-06
Tried the last suggestion.... still no luck :(

I really dont want to have to re-install ubuntu from scratch.... any other ideas? This seems to all have started when I installed Deluge-Torrent :(

---

