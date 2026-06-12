---
title: "upgrade window lost during upgrade to 12.04"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by ubuntu_demon on 2013-01-28
I pressed alt-tab during the upgrade from 11.10 to 12.04 (using the graphical update manager tool). Now I see my background but nothing else. Everything is vanished. I don't see a taskbar, files, buttons or whatever. 

When I left for work this morning my disk was still working so I left it on. 

Is there a way to get back to the upgrade window(s) ? The update manager tool is probably waiting for user input. 

When I get back home tonight I'll first try alt-tab again. I will also try pressing the ALT key. Would there be any other way to get back to the upgrade window if alt-tab doesnt work ?

Unity is new for me because I have always used Ubuntu 10.04 and 10.10 so I don't know which keycombinations I should try. 

I am able to go to a ctrl-alt-f1 and type commands. 

I would rather not do a reboot.

I found multiple people with the same problem:
[http://ubuntuforums.org/showthread.php?t=2009377](http://ubuntuforums.org/showthread.php?t=2009377)
[http://answers.launchpad.net/ubuntu/+source/apt/+question/199964](http://answers.launchpad.net/ubuntu/+source/apt/+question/199964)
[http://askubuntu.com/questions/124829/should-i-restart-my-pc-if-unity-crashes-during-upgrade](http://askubuntu.com/questions/124829/should-i-restart-my-pc-if-unity-crashes-during-upgrade)

I reported a bug on launchpad : [http://bugs.launchpad.net/ubuntu/+source/unity/+bug/1107733](http://bugs.launchpad.net/ubuntu/+source/unity/+bug/1107733)

If I have to do a reboot what is the best strategy ? What's the best way to fix an incomplete upgrade ?

My plan if I can't get back to the upgrade window: 
0: go to control+alt+f1
1: look at the logs in /var/log/dist-upgrade
2: check reported ubuntu version with : lsb_release -a
3: check /etc/apt/sources.list. use [http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php) if needed.
4: stop (kill) the upgrade process. remove any lock files if needed.
5: finish configuring stuff with: sudo dpkg --configure -a
6: If lsb_release -a doesn't say 12.04 then do : sudo do-release-upgrade
7: if needed complete upgrade with:  
sudo apt-get update 
sudo apt-get -f install 
sudo apt-get -f upgrade  
sudo apt-get -f dist-upgrade
8: only if really needed automatically reconfigure all packages (takes a long time): sudo dpkg-reconfigure -phigh -a
9: do some cleaning up:
sudo aptitude clean
sudo apt-get clean
sudo apt-get --purge autoremove
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }')
10: to make sure all packages are updated:
sudo apt-get update
sudo apt-get dist-upgrade
11: sudo reboot and hope for the best


Anything I have missed? Does Ubuntu clean anything else after a succesful release upgrade ?  


Thanks!

---

### Post by ubuntu_demon on 2013-01-28
Solved. When I got back from work I could see the upgrade window but I still couldn't interact with it. I went to control-alt-f1 and did the cleaning up phase by hand.

---

### Post by ubuntu_demon on 2013-01-30
I continue to have problems. I couldn't work with Ubuntu after login (blank screen/automatic reboots/hangs).

Maybe it is related to my intel video chipset and/or compiz and/or unity ?

I have an intel video chipset (GMA 945?) but I can't check lshw/lspci right now for the exact information because I'm at work.

---

### Post by ubuntu_demon on 2013-01-30
I installed gnome-panel and I switched to using the x-swat ppa. 

When I try [http://askubuntu.com/a/127849](http://askubuntu.com/a/127849) I get a segmentation fault regarding icons. I also don't see most icons. And I have some other problems regarding window management and program crashes. 

I suspect my problems are somehow it's related to libgdk-pixbuf2.0-0.

unity_support_test is all good.

I'm going to try sudo dpkg-reconfigure -phigh -a

---

### Post by ubuntu_demon on 2013-01-31
I tried the following:

sudo apt-get install libgdk-pixbuf2.0-dev
sudo dpkg-reconfigure -phigh -a
sudo reboot

Then I tried the following from a gnome-classic-no-effects sesion in the terminal:

sudo su
gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache  
exit
gconftool-2 --recursive-unset /apps/compiz
unity --reset

[I]WARNING: Unity currently default profile, so switching to metacity while resetting the values
Window manager warning: Failed to load theme "Ambiance": Line 195 character 94: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/metacity-1/trough_left.png'
**
metacity:ERROR:ui/ui.c:754:meta_ui_get_default_window_icon: assertion failed: (default_icon)
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1a00004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2c00003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x400003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x400008

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2a007be

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2e000b3

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

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1516:46: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1521:55: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1525:58: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1529:55: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1533:64: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1537:67: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1595:73: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/scrollbar_handle_vertical.png'

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1612:64: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/scrollbar_handle.png'

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:769:55: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:773:55: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:777:67: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:781:64: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:785:64: Unrecognized image file format

(compiz:3528): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:789:76: Unrecognized image file format

(compiz:3528): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
WARN  2013-01-31 05:56:21 unity.favorites FavoriteStoreGSettings.cpp:139 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
ERROR 2013-01-31 05:56:22 nux.image GdkGraphics.cpp:68 Couldn't recognize the image file format for file '/usr/share/unity/5/dash_noise.png'
WARN  2013-01-31 05:56:22 nux.image GdkGraphics.cpp:80 No pixbuf loaded
Segmentation fault (core dumped)
[/I]

unity --reset-icons

[I]
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
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

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1516:46: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1521:55: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1525:58: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1529:55: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1533:64: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1537:67: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1595:73: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/scrollbar_handle_vertical.png'

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1612:64: Couldn't recognize the image file format for file '/usr/share/themes/Ambiance/gtk-3.0/assets/scrollbar_handle.png'

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:769:55: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:773:55: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:777:67: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:781:64: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:785:64: Unrecognized image file format

(compiz:3552): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:789:76: Unrecognized image file format

(compiz:3552): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
WARN  2013-01-31 05:57:31 unity.favorites FavoriteStoreGSettings.cpp:139 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
ERROR 2013-01-31 05:57:31 nux.image GdkGraphics.cpp:68 Couldn't recognize the image file format for file '/usr/share/unity/5/dash_noise.png'
WARN  2013-01-31 05:57:31 nux.image GdkGraphics.cpp:80 No pixbuf loaded
Segmentation fault (core dumped)[/I]

---

