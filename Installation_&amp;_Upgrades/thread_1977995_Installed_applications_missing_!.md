---
title: "Installed applications missing !"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-05-11
Hello Gurus. Here's the scenario.
I downloaded and installed 12.04 via USB. Installation showed bug  regarding software center or something like that and i continued after  reporting the bug. The installation completed. Had to make a hard  restart to use the new installed OS then.
Next, i didn't want to loose the installed applications of ubuntu 11.04  and so, when during the installation of 12.04, i simply used old /home  for the 12.04 without formatting it.

Now, i see my old /home being used. But, the thing is, even though i  have all my bookmarks safe and old settings as they were, i don't find  my applications installed in 11.04 present in 12.04. 

Eg. : Gparted shows up in the software center as being installed in my  current system. But when i search it in the dash home, i end up with no  results. I have no clue of what has happened. I had to install all of  the apps i used back in 11.04 again in this 12.04 which wasn't the  reason for using the old /home. 

Since this is the first time for me to transfer from Ubuntu as sole OS, i  got a bit confused here. Doesn't using the same /home for new  installation leave the programs installed in previous version of ubuntu  unaffected?? or should i have to re-install programs everytime i switch  from one version of ubuntu to other??  Is it not enough to use same /home in order to retain the applications installed in previous version of ubuntu or should there be something more to be done?

Thanks in advance.
Happy Linuxing.:razz:

---

### Post by wilee-nilee on 2012-05-11
I never have used a separate home so I don't know about things installed like gparted stil being present.  But unity I have found needs a reset on occasion to show stuff in that dash, at least for me anyway.

Try this hit alt-f2 and type in unity --reset to reset the unity desktop.

---

### Post by efflandt on 2012-05-11
Unless you have binaries or scripts that you keep in your home or personal ~/bin, system programs are in other paths in the main system, not in /home.  So if you install a new system, programs not installed by default would no longer be there.

If you upgrade (instead of install), your previous programs would likely still be there unless they were not compatible or had unmet dependencies, possibly due to something becoming obsolete.  But upgrading can be somewhat chancy as to whether everything will work, especially if you neglect to purge ppa repositories or installed or customized something directly instead of through deb packages.

---

### Post by nipunshakya on 2012-05-11
> **wilee-nilee said:**
> 
Try this hit alt-f2 and type in unity --reset to reset the unity desktop.
doing that gives the following output...and the cursor keeps blinking and blinking....as if some process is being still on progress....but nothing out yet..!!
SOmewhere in the middle, it says i should file a bug coz that never happens....and i didn't understand the rest...
Should the o/p be the same as expected below?

```

winuxuser@MagicBox:~$ sudo apt-get autoremove
[sudo] password for winuxuser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
winuxuser@MagicBox:~$ mail notifications
The program 'mail' is currently not installed.  You can install it by typing:
sudo apt-get install mailutils
winuxuser@MagicBox:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3c000af

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x36001fc

Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:2931): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0xe0009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0xe000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.glib-gobject <unknown>:0 invalid cast from `BamfWindow' to `BamfApplication'
ERROR 2012-05-11 19:53:09 unity <unknown>:0 bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed
WARN  2012-05-11 19:53:09 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 2
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 3
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 4
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 5
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 6
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 7
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 8
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 9
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 10
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 11
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 12
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 13
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 14
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 15
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 16
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 17
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 18
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 19
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 20
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 21
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 22
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 23
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 24
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 25
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 26
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 27
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 28
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 29
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 30
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 31
ERROR 2012-05-11 19:53:09 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2012-05-11 19:53:09 unity <unknown>:0 No listener with the specified ID: 32
WARN  2012-05-11 19:53:09 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window56623612
Initializing staticswitcher options...done
ERROR 2012-05-11 19:53:10 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-05-11 19:53:47 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for net.launchpad.lens.video: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/unity-lens-video/unity-lens-video exited with status 1
ERROR 2012-05-11 19:53:48 unity.dee <unknown>:0 dee_model_get_first_iter: assertion `DEE_IS_MODEL (self)' failed
ERROR 2012-05-11 19:53:48 unity.dee <unknown>:0 dee_model_get_last_iter: assertion `DEE_IS_MODEL (self)' failed
WARN  2012-05-11 19:53:48 unity.dash.homelens HomeLens.cpp:972 Unable to find a lens for activating ''. Using fallback activation.
WARN  2012-05-11 19:54:12 unity.glib.dbusproxy GLibDBusProxy.cpp:283 Calling method "GlobalSearch" on object path: "/com/canonical/unity/lens/files" failed: Timeout was reached
WARN  2012-05-11 19:54:30 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window65011718
WARN  2012-05-11 19:54:30 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application335844169

WARN  2012-05-11 19:54:30 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application335844169

WARN  2012-05-11 19:54:30 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application335844169

WARN  2012-05-11 19:54:30 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application335844169

```

---

### Post by jadtech on 2012-05-11
ok  so have tyou ran updates from the software updater yet ??  keep in mind all your old software needs to be updated  to run on 12.4 or at least most of it ..
also if you go to the dash and search for programs that were installed do  the Icons for them show up and if they do can you click and run them .. 

it could be a matter of dragging and dropping them  on the luncher

---

### Post by nipunshakya on 2012-05-11
> **jadtech said:**
> ok  so have tyou ran updates from the software updater yet ??  keep in mind all your old software needs to be updated  to run on 12.4 or at least most of it ..
also if you go to the dash and search for programs that were installed do  the Icons for them show up and if they do can you click and run them .. 

it could be a matter of dragging and dropping them  on the luncher

Hello sir. The first thing i did was to run update manager and update my softwares... i did that this time....

Searching in dash won't even show up any applications(not even the default ones installed too...)

My above reply including the output of code unity --reset was not understandable to me, however, at middle somewhere, it said i had a bug that needs to be reported...and still im confused about this thing...

---

### Post by jadtech on 2012-05-11
yeah I didnt see that post till later it took me a bit to  get my reply finished happens from time to time when have toddler :) 

looks like something got messed up  , since all your personal goodies are in the home directory might be to your benifit to try the install again  if you feel up to the adventure   or you could hang in there  someone may know of a fix for this .. 

though as pointed out using the old home wont save  any programs that are not default  they will be installed in usr directory so when install is done anything that is not default install will have to be  down loaded  once the dust settles ..

---

### Post by nipunshakya on 2012-05-11
Being clear that my previous installations of applications wont work in new OS, i installed gparted again. This time, searching it in bash shows the application, and i tried to run it. It prompts me for password too, but after the password input, the program doesn't seem to start.

if i try ```
sudo gparted
```
i get the following:
```
winuxuser@MagicBox:~$ sudo apt-get install gparted
[sudo] password for winuxuser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
winuxuser@MagicBox:~$ sudo gparted
/usr/sbin/gpartedbin: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
winuxuser@MagicBox:~$ 

```

any ideas?

---

### Post by jadtech on 2012-05-11
have you tried to go uninstall and purge Gparted  then go to the software center and  reinstall it ..

maybe you just need to fix permissions make the files read write and excutable create another user see if things change that way as well  ..

---

### Post by nipunshakya on 2012-05-11
> **jadtech said:**
> have you tried to go uninstall and purge Gparted  then go to the software center and  reinstall it ..
yes, i have did that too...three times in a row with restart each time....no luck either...

> **jadtech said:**
> maybe you just need to fix permissions make the files read write and excutable create another user see if things change that way as well  ..
i guess that there is some libraries missing(as said by above o/p while trying to run gparted)... so will creating another user be a reliable solution to that?
i just navigated through /usr/sbin but i didnt find 'gpartedbin' inside it.... maybe thats what is missing, and i need to have that in my system for gparted to run...any way to get that?

Thanks for your quick replies... :)

---

### Post by nipunshakya on 2012-05-21
I think there was a serious issue with my 12.04 installation iso previously. I didnt know that the /casper/filesystem.squashfs had errors(realized it after installation :( ) So, I did a fresh installation of ubuntu 12.04 with a new iso that i downloaded. Now, it seems that everything is fine till now... Thanks guys for your help and time...

Happy Linuxing

---

### Post by ravisghosh on 2012-05-23
> **WinuxUser said:**
> doing that gives the following output...and the cursor keeps blinking and blinking....as if some process is being still on progress....but nothing out yet..!!
SOmewhere in the middle, it says i should file a bug coz that never happens....and i didn't understand the rest...
Should the o/p be the same as expected below?


I am faced with exact same issue with some installed apps such as GIMP are not showing up in dash. However, when I press Alt+F2 and search for GIMP, it shows up there and starts without any issues. Also, I found .desktop file in the /usr/share/app-install/desktop folder.

I tried uninstalling GIMP and installing it back, but nothing changed.

Also, few apps still, such as doit.I'm, show up in dash even though they have been uninstalled ages back.

How can we get rid of uninstalled app and get the installed app in dash?

---

### Post by nipunshakya on 2012-05-23
> **ravisghosh said:**
> I am faced with exact same issue with some installed apps such as GIMP are not showing up in dash. However, when I press Alt+F2 and search for GIMP, it shows up there and starts without any issues. Also, I found .desktop file in the /usr/share/app-install/desktop folder.

I tried uninstalling GIMP and installing it back, but nothing changed.

Also, few apps still, such as doit.I'm, show up in dash even though they have been uninstalled ages back.[quote]

did u try to purge gimp first and install as jadtech suggested me to do with gparted?

```
**sudo add-apt-repository ppa:jmou/ppa **
``` then
 ```
**sudo apt-get update**
``` and finally```
**sudo apt-get install gimp**
```This will install GIMP 2.7.4

[QUOTE=ravisghosh;11962732]How can we get rid of uninstalled app and get the installed app in dash?

In the terminal, type 
```
sudo apt-get autoremove
```

---

### Post by ravisghosh on 2012-05-24
I used ppa:otto-kesselgulasch/gimp to get gimp 2.8. 

Strange thing is GIMP shows up in Gnome DE and FVWM without any issues, but it doesn't show up in Unity.

Also, equally strange all the uninstalled apps don't show up in GNOME or FVWM, but in Unity.

So, I guess it has something to do with unity.

---

### Post by Grand old man on 2012-06-15
I am using Mythbuntu 12.04 and after downloading programs (Synaptic & Firefox) they do not appear on the desktop or menus.

I am very puzzeled. Seems these programs are off limits or am I nuts.

Guidance please.

---

### Post by ravisghosh on 2012-06-16
> **Grand old man said:**
> I am using Mythbuntu 12.04 and after downloading programs (Synaptic & Firefox) they do not appear on the desktop or menus.

I am very puzzeled. Seems these programs are off limits or am I nuts.

Guidance please.

The reason for apps not showing up in dash was that the version in .desktop files was different from the version of the application installed.

Look for the .desktop files in the following locations:

/usr/share/app-install/desktop/
/usr/share/applications
/home/shantanu/.local/share/applications

For the first two locations, you need to open the file with root rights and and for the last one, you can simply double click and open it.

To open with root rights, use

> sudo gedit /usr/share/app-install/desktop/whatever.desktop

Then change the version in the file to match the version you have installed.

This should fix the issue.

---

