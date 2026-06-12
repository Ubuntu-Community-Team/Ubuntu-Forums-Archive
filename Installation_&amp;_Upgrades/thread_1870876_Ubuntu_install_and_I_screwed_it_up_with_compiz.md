---
title: "Ubuntu install and I screwed it up with compiz"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by dontkillthemetal on 2011-10-28
SOLVED


Hello everyone and thank you for taking the time to view my post.
If i am in the wrong thread  i apologize i am very new to forums/Ubuntu.

I got a live disc for Ubuntu 11.04 and installed/upgraded to 11.10.  I installed ccsm to play with compiz since i always loved the desktop effects on the old version.( I used to play with Ubuntu in my tech class).

I followed some random guide i found through google and it said to run the command "compiz --replace"

so i did it...and now the side bar and top menus are gone and all i have is compiz and a blank screen.  Can anyone teach me how to revert this?  I found a guide how to install it properly and will do that after words.

is there a way to fix this and revert it?  Or do i need to reinstall.

thanks again for looking and i hope u can help me!
Zack

---

### Post by dontkillthemetal on 2011-10-28
cant anyone help me?

---

### Post by pastalavista on 2011-10-28
Try the command: unity --replace and if that doesn't work, unity --reset (reset will undo all the changes you've made with compiz)

---

### Post by dontkillthemetal on 2011-10-28
it is running the process..ill post when it finally completes

---

### Post by dontkillthemetal on 2011-10-28
ok everyone so i did unity --replace and unity has come back.  if i restart will unity remain there?  i will also do unity reset if i should do that as well.  I thank you deeply you really saved me alot of stress.

is compiz fully suported like it used to be? i really miss the window options and the 3d cube.  If so can you provide a link to get things set up in the best way?

---

### Post by dontkillthemetal on 2011-10-28
ok so when i run unity --replace  i get this:

zack@Computer1:~$ sudo unity --replace
[sudo] password for zack: 
unity-panel-service: no process found
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
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
WARN  2011-10-28 03:41:01 glib.glib-gobject <unknown>:0 invalid (NULL) pointer instance

Screen geometry changed:
   0x0x1366x768

unity-panel-service: no process found
Initializing unityshell options...done
DEBUG 2011-10-28 03:41:02 glib <unknown>:0 Setting to primary screen rect: x=0 y=0 w=1366 h=768
WARN  2011-10-28 03:41:02 unity.favorites FavoriteStoreGSettings.cpp:138 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2011-10-28 03:42:02 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-28 03:42:02 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-10-28 03:42:02 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-28 03:42:02 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-10-28 03:42:02 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-28 03:42:02 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-10-28 03:42:02 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-28 03:42:02 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-10-28 03:42:02 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-10-28 03:42:02 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory



any clue whats going on?

---

### Post by pastalavista on 2011-10-28
Compiz is NOT fully supported on 11.10 and I've heard warnings it can conflict with Gnome3 Unity and be buggy and crash prone. I'm sticking with Natty for a while until Gnome3 gets its act together.

---

### Post by dontkillthemetal on 2011-10-28
ok well for now im looking to just undo the whole compiz thing but the process wont finish for unity --replace

and if/when it does it just goes back to compiz and is glitchy so i have to restart.  works fine while process is running in terminal tho

---

### Post by dontkillthemetal on 2011-10-28
SOLVED

all i needed to do and hopefully ths will work for anyone else:

if compiz is running press GO>computer

search HDD for terminal

open  gnome terminal

User: ccsm

and then just set your settings back to unity through ccsm.  it saved and now im back on unity

thanks for the help guys

---

### Post by Starfleet on 2011-10-28
Compiz screwed up my whole installation of 11.10. So the best thing, and quickest way for me was to reinstall. This is easy to do as you know. Mine is dual booted with 10.04LTS (which is a real gem and bug free of course). Glad you got yours going ok.

---

### Post by mörgæs on 2011-10-28
Good, please mark the thread 'solved' using 'thread tools'.

---

### Post by dontkillthemetal on 2011-10-30
sorry ive been away, its been marked. thank you

---

