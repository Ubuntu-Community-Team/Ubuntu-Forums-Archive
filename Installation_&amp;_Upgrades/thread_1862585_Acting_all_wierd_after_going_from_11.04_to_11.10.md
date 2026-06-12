---
title: "Acting all wierd after going from 11.04 to 11.10"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by cacao on 2011-10-16
So basically i just went from 11.04 to 11.10
Now i boot into 11.10
When i click on shortcut to the home folder it just blinks for a while and does not pop-up any directory or anything.
when i open Ubuntu software center it's just stuck at Loading categories.
I cannot select my background.
If i open up the dash-home and for example i have my browser open, my browser will go over that search thing, and i won't be able to see anything..
Also i can't open the trash bin..
The bar at the top is just grey and shows the name of the selected item and my battery and wifi, nothing else.
this is quite annoying.. does anybody know a solution to these things? :confused::confused:

also i got this from compiz
> ~$ compiz --replace
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing move options...done
Initializing gnomecompat options...done
Initializing vpswitch options...done
Initializing place options...done
Initializing grid options...done
Initializing mousepoll options...done
Initializing session options...done
Initializing resize options...done
Initializing snap options...done
Initializing wall options...done
Initializing unitymtgrabhandles options...done
Initializing animation options...done
Initializing workarounds options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing fade options...done
Initializing ezoom options...done
Initializing scale options...done

Screen geometry changed:
   0x0x1440x900

Initializing unityshell options...done
DEBUG 2011-10-17 04:11:46 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1440 h=900
WARN  2011-10-17 04:11:46 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window46140293: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2011-10-17 04:11:46 glib <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window46140293: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist

WARN  2011-10-17 04:11:47 unity.launcher LauncherIcon.cpp:436 Unable to load '/opt/teamviewer/teamviewer/6/desktop/teamviewer.png' icon: Failed to open file '/opt/teamviewer/teamviewer/6/desktop/teamviewer.png': No such file or directory
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
WARN  2011-10-17 04:11:49 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-17 04:11:49 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-17 04:11:49 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-17 04:11:49 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-17 04:11:49 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-17 04:11:49 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-17 04:11:49 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-17 04:11:49 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-17 04:11:50 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-10-17 04:11:50 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
WARN  2011-10-17 04:11:51 unity.iconloader IconLoader.cpp:401 Unable to load icon . GThemedIcon application-x-xpinstall gnome-mime-application-x-xpinstall application-x-generic at size 64
compiz (core) - Warn: failed to receive ConfigureNotify event from request at 95767 (now: 396150)

compiz (core) - Warn: unhandled ConfigureNotify on 0x3600142!
compiz (core) - Warn: this should never happen. you shouldprobably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3600142!
compiz (core) - Warn: this should never happen. you shouldprobably file a bug about this.


---

### Post by nicksanta on 2011-10-18
I had this problem also. I fixed it by reinstalling the software center from command line:

sudo apt-get install --reinstall software-center

---

