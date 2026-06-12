---
title: "Apt-get broken"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by someone7663663 on 2007-03-22
Hi, i am having a problem with apt-get. I recently tried installing gtkpod to try to get my iPod to work and ran into a problem. Something went wrong in the install and it never installed, but thats not my main problem. Ever since i tried installing this, i keep getting an error with apt-get whenever i install anything, so i can't update the system or install any programs. 

> 
sudo apt-get install 3dchess
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsqlite0 libmono-sharpzip0.6-cil libwv-1.2-1 beagle kdebase-bin
  python-sqlite libmono-system-runtime1.0-cil libgsf0.0-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xaw3dg
The following packages will be REMOVED:
  kdebase-bin
The following NEW packages will be installed:
  3dchess xaw3dg
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 182kB of archives.
After unpacking 2920kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main xaw3dg 1.5+E-14ubuntu1 [149kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe 3dchess 0.8.1-12 [32.4kB]
Fetched 182kB in 3s (51.6kB/s)  
(Reading database ... 147380 files and directories currently installed.)
Removing kdebase-bin ...

(update-desktop-database:20450): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kdebase-bin (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 kdebase-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)


For some reason kedbase-bin wants to uninstall and that seems to be messing everything up, and i can't figure out any way to fix this. If anyone could help, that would be awesome.

---

### Post by zvacet on 2007-03-22
It seems that you have broken packages
> 5 not fully installed or removed.
synaptic>edit<fix broken packages  or
```
sudo dpkg  --configure -a
```

---

### Post by someone7663663 on 2007-03-22
When i do sudo dpkg --configure -a all i get is this:

> Setting up gtkpod (0.99.4-1ubuntu1) ...

(update-desktop-database:31047): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing gtkpod (--configure):
 subprocess post-installation script returned error exit status 139
Setting up kdebase-kio-plugins (3.5.5-0ubuntu3.3) ...

(update-desktop-database:31065): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing kdebase-kio-plugins (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of amarok:
 amarok depends on kdebase-kio-plugins; however:
  Package kdebase-kio-plugins is not configured yet.
dpkg: error processing amarok (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amarok-xine:
 amarok-xine depends on amarok (= 2:1.4.5-0ubuntu2~edgy1); however:
  Package amarok is not configured yet.
 amarok-xine depends on amarok; however:
  Package amarok is not configured yet.
dpkg: error processing amarok-xine (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gtkpod
 kdebase-kio-plugins
 amarok
 amarok-xine


still telling me about kdebase-bin and gtkpod, and amarok. Any other advice?

---

### Post by rjamorim on 2007-04-11
I'm having the same error. 

update-desktop-database -v outputs several errors like this:
File '/usr/share/applications/kde/kcmaccess.desktop' lacks MimeType key
and then segfaults as well.

---

### Post by heimo on 2007-04-11
someone7663663:

Try:
```
sudo mv /var/lib/dpkg/info/kdebase-kio-plugins.* /tmp/
sudo mv /var/lib/dpkg/info/gtkpod.* /tmp/
sudo aptitude update
sudo aptitude --purge remove kdebase-kio-plugins gtkpod
sudo aptitude install kdebase-kio-plugins amarok amarok-xine

```

---

### Post by Chemroydal Tissue on 2007-06-12
> **heimo said:**
> someone7663663:

Try:
```
sudo mv /var/lib/dpkg/info/kdebase-kio-plugins.* /tmp/
sudo mv /var/lib/dpkg/info/gtkpod.* /tmp/
sudo aptitude update
sudo aptitude --purge remove kdebase-kio-plugins gtkpod
sudo aptitude install kdebase-kio-plugins amarok amarok-xine

```

I had the same problem, only with mplayer. Seems there was a problem getting all of the files when I installed, though I don't remember there being any error messages. Still, this solution worked for me, and saved me some time poking about for an answer on my own (though I didn't need amarok). Thanks!

---

