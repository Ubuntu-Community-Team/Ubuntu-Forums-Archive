---
title: "Root Directory Running out of space"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by maprx on 2007-04-02
I install Feisty on my part laptop HD.  My root directory had 5.5 g and now it has 1.0 g,  is there anyway to increase the size of the root, without a complete re-install?

---

### Post by hyperian on 2007-04-02
With a 5.5g HD you can hardly achieve much.
Either allocate more space, or clear unimportant files
using a file utility(like baobab) to make space.

---

### Post by dcstar on 2007-04-03
> **maprx said:**
> I install Feisty on my part laptop HD.  My root directory had 5.5 g and now it has 1.0 g,  is there anyway to increase the size of the root, without a complete re-install?

Boot off a CD that has **gparted** on it (the Fiesty Beta one don't......) and then you may be able to resize your existing HD partitions to make space to increase the size of your Ubuntu root partition.

---

### Post by maprx on 2007-04-16
> **hyperian said:**
> With a 5.5g HD you can hardly achieve much.
Either allocate more space, or clear unimportant files
using a file utility(like baobab) to make space.


I have a 55g partition, but the root is down to 1g

---

### Post by maprx on 2007-04-16
> **dcstar said:**
> Boot off a CD that has **gparted** on it (the Fiesty Beta one don't......) and then you may be able to resize your existing HD partitions to make space to increase the size of your Ubuntu root partition.

will that crash my system?

---

### Post by zvacet on 2007-04-16
No it will not.Take some space from another partition and make it allocated.After that expand your root to the alocated space and that is it.You don´t neded more than 10GB for root.

---

### Post by maprx on 2007-04-17
the partion i was goin to get from was from the /home,  however gparted will make that smaller, but how do I get   that extra space as the root. my root part is locked, so if I make my home part from 40 to 30, the 10 g extra will be avail to allocate?, do i have to do anything to that extra space to make it avail, when I resize?

---

### Post by zvacet on 2007-04-17
Your root is locked because it works.That is the reason you need Live Cd or Gparted liveCD.When you boot from disc your system doesn´t work and you can manipulate with it.If it is not much trouble to you download Gparted liveCd.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Space you take from home make allocate and after that just expand your root to it.That is all you have to do.

---

### Post by maprx on 2007-04-17
I tried using gparted, I can make the /home smaller, but the extra space, is not available for me to use in thew root.  its become unallocated space, and there does not seem to be a way to allocate it.  i have 4 primary partions,

---

### Post by Rogers on 2007-04-18
Why does your root have 55 gigs on it? Something is wrong with your FS.  Go to / type du -sh *  and look at the results.  There is no reason your root should ever grow more than a few gigs.  You /home is a different part according to prior posts? 

You can grow you root FS with resize2fs for ext3 or resize_reiserfs for reiser.

:popcorn:

---

### Post by Rogers on 2007-04-18
Post your output from du here and maybe we can help figure out whats using all of your space.

---

### Post by maprx on 2007-04-18
my total ubuntu partion is 55g  my root is 5g,  but it is now 1.3g

---

### Post by enthusaroo on 2007-04-19
I'd like to know an answer to this one too. I haven't installed Feisty YET. I will install very soon. I just need to know how much space to allocate for the Ubuntu "/" (root) partition for the Ubuntu install? Some people on the Internet say 2gb, while others say 5gb, and even some people on this forum still say 5gb is not enough, and it should be 8gb to 10gb of space. What is a "safe" size to install Feisty and plan ahead for the next two years to have enough space for updates and future installs of Ubuntu?

---

### Post by maprx on 2007-04-25
I did the 5g thing and I have only 1 g left.  I like to install alot of apps.  My 100g laptop is divided in 1/2.  one 1/2 to windows and the other to ubuntu.  All attempts to increase root have failed.  I can't allocate from the other partions even using gparted.  It is just not an option when I try.

---

### Post by maprx on 2007-04-25
> **Rogers said:**
> Post your output from du here and maybe we can help figure out whats using all of your space.

here it goes

8       ./.gnome/apps
8       ./.gnome/gnome-vfs
8       ./.gnome/application-info
28      ./.gnome
4       ./.kde/share/servicetypes
4       ./.kde/share/apps/konsole
12      ./.kde/share/apps/konqueror
4       ./.kde/share/apps/kicker/extensions
4       ./.kde/share/apps/kicker/applets
12      ./.kde/share/apps/kicker
4       ./.kde/share/apps/remoteview
64      ./.kde/share/apps/konqsidebartng/filemanagement/entries
68      ./.kde/share/apps/konqsidebartng/filemanagement
72      ./.kde/share/apps/konqsidebartng
4       ./.kde/share/apps/kbluetoothd/discovery_jobs
8       ./.kde/share/apps/kbluetoothd
4       ./.kde/share/apps/kfile
40      ./.kde/share/apps/kconf_update/log
44      ./.kde/share/apps/kconf_update
4       ./.kde/share/apps/krusader
20      ./.kde/share/apps/nsplugins
4       ./.kde/share/apps/kab
8       ./.kde/share/apps/RecentDocuments
12      ./.kde/share/apps/kwifimanager
8       ./.kde/share/apps/kdesktop
4       ./.kde/share/apps/kopete
8       ./.kde/share/apps/klipper
4       ./.kde/share/apps/kfm/bookmarks
8       ./.kde/share/apps/kfm
4       ./.kde/share/apps/kmail
4       ./.kde/share/apps/kabc/lock
8       ./.kde/share/apps/kabc
252     ./.kde/share/apps
52      ./.kde/share/mimelnk/video
52      ./.kde/share/mimelnk/audio
8       ./.kde/share/mimelnk/image
48      ./.kde/share/mimelnk/application
164     ./.kde/share/mimelnk
8       ./.kde/share/applnk
8       ./.kde/share/services
4       ./.kde/share/config/kresources/calendar
8       ./.kde/share/config/kresources/contact
16      ./.kde/share/config/kresources
8       ./.kde/share/config/session
360     ./.kde/share/config
800     ./.kde/share
8       ./.kde/Autostart
812     ./.kde
4       ./.java/deployment/ext
4       ./.java/deployment/security
4       ./.java/deployment/cache/6.0/40
44      ./.java/deployment/cache/6.0/56
4       ./.java/deployment/cache/6.0/12
4       ./.java/deployment/cache/6.0/14
4       ./.java/deployment/cache/6.0/53
4       ./.java/deployment/cache/6.0/39
4       ./.java/deployment/cache/6.0/52
4       ./.java/deployment/cache/6.0/10
4       ./.java/deployment/cache/6.0/27
4       ./.java/deployment/cache/6.0/11
4       ./.java/deployment/cache/6.0/15
4       ./.java/deployment/cache/6.0/59
4       ./.java/deployment/cache/6.0/6
4       ./.java/deployment/cache/6.0/8
4       ./.java/deployment/cache/6.0/50
4       ./.java/deployment/cache/6.0/41
4       ./.java/deployment/cache/6.0/61
4       ./.java/deployment/cache/6.0/23
4       ./.java/deployment/cache/6.0/46
4       ./.java/deployment/cache/6.0/29
4       ./.java/deployment/cache/6.0/57
4       ./.java/deployment/cache/6.0/5
4       ./.java/deployment/cache/6.0/18
4       ./.java/deployment/cache/6.0/44
4       ./.java/deployment/cache/6.0/muffin
48      ./.java/deployment/cache/6.0/43
4       ./.java/deployment/cache/6.0/0
4       ./.java/deployment/cache/6.0/37
4       ./.java/deployment/cache/6.0/16
4       ./.java/deployment/cache/6.0/21
4       ./.java/deployment/cache/6.0/tmp
4       ./.java/deployment/cache/6.0/55
4       ./.java/deployment/cache/6.0/24
4       ./.java/deployment/cache/6.0/9
4       ./.java/deployment/cache/6.0/47
4       ./.java/deployment/cache/6.0/45
4       ./.java/deployment/cache/6.0/20
4       ./.java/deployment/cache/6.0/51
4       ./.java/deployment/cache/6.0/26
4       ./.java/deployment/cache/6.0/22
4       ./.java/deployment/cache/6.0/58
4       ./.java/deployment/cache/6.0/31
4       ./.java/deployment/cache/6.0/25
4       ./.java/deployment/cache/6.0/32
4       ./.java/deployment/cache/6.0/30
4       ./.java/deployment/cache/6.0/62
92      ./.java/deployment/cache/6.0/49
4       ./.java/deployment/cache/6.0/54
4       ./.java/deployment/cache/6.0/34
4       ./.java/deployment/cache/6.0/13
4       ./.java/deployment/cache/6.0/60
4       ./.java/deployment/cache/6.0/3
4       ./.java/deployment/cache/6.0/42
4       ./.java/deployment/cache/6.0/2
4       ./.java/deployment/cache/6.0/35
4       ./.java/deployment/cache/6.0/33
4       ./.java/deployment/cache/6.0/1
4       ./.java/deployment/cache/6.0/28
4       ./.java/deployment/cache/6.0/38
180     ./.java/deployment/cache/6.0/17
4       ./.java/deployment/cache/6.0/36
4       ./.java/deployment/cache/6.0/63
4       ./.java/deployment/cache/6.0/7
4       ./.java/deployment/cache/6.0/4
4       ./.java/deployment/cache/6.0/19
4       ./.java/deployment/cache/6.0/48
620     ./.java/deployment/cache/6.0
624     ./.java/deployment/cache
4       ./.java/deployment/log
644     ./.java/deployment
648     ./.java
28      ./.frostwire/xml/schemas
8       ./.frostwire/xml/data
24      ./.frostwire/xml/misc
64      ./.frostwire/xml
44      ./.frostwire/themes/frostwire_theme
72      ./.frostwire/themes
232     ./.frostwire
32      ./google-earth/linux/xdg
20      ./google-earth/linux/mailto-scripts
60      ./google-earth/linux
48      ./google-earth/xml
8       ./google-earth/.manifest/scripts
228     ./google-earth/.manifest
8       ./google-earth/kvw
64      ./google-earth/resources/ja.locale
80      ./google-earth/resources/en_NZ.locale
76      ./google-earth/resources/en_CA.locale
76      ./google-earth/resources/en.locale
72      ./google-earth/resources/es.locale
76      ./google-earth/resources/fr.locale
72      ./google-earth/resources/it.locale
80      ./google-earth/resources/en_AU.locale
80      ./google-earth/resources/en_US.locale
80      ./google-earth/resources/en_GB.locale
72      ./google-earth/resources/de.locale
9316    ./google-earth/resources
48      ./google-earth/res/shapes
36      ./google-earth/res/pushpin
548     ./google-earth/res/paddle
848     ./google-earth/res/pal4
1044    ./google-earth/res/pal5
944     ./google-earth/res/pal3
848     ./google-earth/res/pal2
5844    ./google-earth/res
1092    ./google-earth/lang
57444   ./google-earth
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#comcast.net
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.comcast.net](www.comcast.net)
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#[www.youtube.com](www.youtube.com)
32      ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
36      ./.macromedia/Flash_Player/macromedia.com/support/flashplayer
40      ./.macromedia/Flash_Player/macromedia.com/support
44      ./.macromedia/Flash_Player/macromedia.com
8       ./.macromedia/Flash_Player/#SharedObjects/MU62YVV4/www.comcast.net/swf/fan/miniFan.swf
12      ./.macromedia/Flash_Player/#SharedObjects/MU62YVV4/www.comcast.net/swf/fan
16      ./.macromedia/Flash_Player/#SharedObjects/MU62YVV4/www.comcast.net/swf
24      ./.macromedia/Flash_Player/#SharedObjects/MU62YVV4/www.comcast.net
8       ./.macromedia/Flash_Player/#SharedObjects/MU62YVV4/www.youtube.com
8       ./.macromedia/Flash_Player/#SharedObjects/MU62YVV4/comcast.net
44      ./.macromedia/Flash_Player/#SharedObjects/MU62YVV4
48      ./.macromedia/Flash_Player/#SharedObjects
96      ./.macromedia/Flash_Player
100     ./.macromedia
592     ./.mcop/trader-cache
600     ./.mcop
4       ./.update-notifier
12      ./.config/menus
8       ./.config/gtk-2.0
8       ./.config/xfce4-session
4       ./.config/xfce4/xfwm4
4       ./.config/xfce4/orage
12      ./.config/xfce4/panel
16      ./.config/xfce4/mcs_settings
8       ./.config/xfce4/desktop
48      ./.config/xfce4
8       ./.config/Thunar
4       ./.config/autostart
92      ./.config
12      ./.cache/sessions
32      ./.cache/xfce4/desktop
36      ./.cache/xfce4
60      ./.cache
412     ./Incomplete
88      ./.metacity/sessions
92      ./.metacity
8       ./.update-manager
564     ./.gstreamer-0.10
464     ./.loki/installed/bin/Linux/x86
468     ./.loki/installed/bin/Linux
472     ./.loki/installed/bin
4       ./.loki/installed/locale
480     ./.loki/installed
484     ./.loki
4       ./.local/share/desktop-directories
32      ./.local/share/applications
4       ./.local/share/Trash/info
4       ./.local/share/Trash/files
12      ./.local/share/Trash
8       ./.local/share/mime/packages
20      ./.local/share/mime/application
44      ./.local/share/mime
96      ./.local/share
100     ./.local
212     ./.gnome2/yelp.d
8       ./.gnome2/share/cursor-fonts
8       ./.gnome2/share/fonts
20      ./.gnome2/share
4       ./.gnome2/nautilus-scripts
28      ./.gnome2/accels
4       ./.gnome2/keyrings
292     ./.gnome2
4       ./.apt-watch/archives/partial
236     ./.apt-watch/archives
4       ./.apt-watch/lists/partial
31680   ./.apt-watch/lists
31920   ./.apt-watch
8       ./.rhapsody
8       ./.streamtuner/cache/xiph
4       ./.streamtuner/cache/bookmarks
8       ./.streamtuner/cache/shoutcast
4       ./.streamtuner/cache/punkcast%2Ecom%2Epy
8       ./.streamtuner/cache/live365
8       ./.streamtuner/cache/basic%2Ech%2Epy
8       ./.streamtuner/cache/google%2Dstations%2Epy
4       ./.streamtuner/cache/preselections
8       ./.streamtuner/cache/local
64      ./.streamtuner/cache
92      ./.streamtuner
52      ./.evolution/mail/local
56      ./.evolution/mail
4       ./.evolution/memos/config
8       ./.evolution/memos/local/system
12      ./.evolution/memos/local
20      ./.evolution/memos
4       ./.evolution/calendar/config
8       ./.evolution/calendar/local/system
12      ./.evolution/calendar/local
20      ./.evolution/calendar
4       ./.evolution/cache
4       ./.evolution/tasks/config
8       ./.evolution/tasks/local/system
12      ./.evolution/tasks/local
20      ./.evolution/tasks
196     ./.evolution
188     ./.fontconfig
316     ./.automatix
4       ./.BitTornado/torrentcache
8       ./.BitTornado/datacache
148     ./.BitTornado/icons
4       ./.BitTornado/piececache
172     ./.BitTornado
12      ./.qt
160     ./.thumbnails/normal
164     ./.thumbnails
476     ./Shared
16      ./.nautilus/metafiles
96      ./.nautilus
3348    ./.debtags
4       ./.enlightenment/backgrounds
4       ./.enlightenment/cached/bgsel
12      ./.enlightenment/cached/pager
144     ./.enlightenment/cached/cfg
4       ./.enlightenment/cached/img
168     ./.enlightenment/cached
40      ./.enlightenment/menus_GNOME
88      ./.enlightenment/menus_Other
156     ./.enlightenment/icons
36      ./.enlightenment/menus_KDE
4       ./.enlightenment/themes
532     ./.enlightenment
8       ./.update-manager-core
12      ./.icons
8       ./.gconf/system/bluetooth/device/00:12:56:73:F2:60
12      ./.gconf/system/bluetooth/device
16      ./.gconf/system/bluetooth
8       ./.gconf/system/networking/wireless/networks/linksys
12      ./.gconf/system/networking/wireless/networks
16      ./.gconf/system/networking/wireless
20      ./.gconf/system/networking
40      ./.gconf/system
8       ./.gconf/apps/gnome-app-install
8       ./.gconf/apps/evolution/mail
8       ./.gconf/apps/evolution/memos
8       ./.gconf/apps/evolution/calendar/display
8       ./.gconf/apps/evolution/calendar/notify
8       ./.gconf/apps/evolution/calendar/memos
8       ./.gconf/apps/evolution/calendar/tasks
40      ./.gconf/apps/evolution/calendar
8       ./.gconf/apps/evolution/tasks
8       ./.gconf/apps/evolution/addressbook
80      ./.gconf/apps/evolution
8       ./.gconf/apps/gedit-2/preferences/ui/statusbar
12      ./.gconf/apps/gedit-2/preferences/ui
16      ./.gconf/apps/gedit-2/preferences
20      ./.gconf/apps/gedit-2
8       ./.gconf/apps/gnome-settings/gnome-nettool
8       ./.gconf/apps/gnome-settings/gnome-panel
20      ./.gconf/apps/gnome-settings
8       ./.gconf/apps/update-manager
8       ./.gconf/apps/bluetooth-manager
8       ./.gconf/apps/metacity/keybinding_commands
8       ./.gconf/apps/metacity/window_keybindings
8       ./.gconf/apps/metacity/global_keybindings
28      ./.gconf/apps/metacity
8       ./.gconf/apps/compiz/plugins/fade/screen0/options
12      ./.gconf/apps/compiz/plugins/fade/screen0
16      ./.gconf/apps/compiz/plugins/fade
20      ./.gconf/apps/compiz/plugins
8       ./.gconf/apps/compiz/general/allscreens/options
12      ./.gconf/apps/compiz/general/allscreens
16      ./.gconf/apps/compiz/general
40      ./.gconf/apps/compiz
8       ./.gconf/apps/panel/applets/applet_2
8       ./.gconf/apps/panel/applets/applet_5/prefs
16      ./.gconf/apps/panel/applets/applet_5
8       ./.gconf/apps/panel/applets/applet_4/prefs
16      ./.gconf/apps/panel/applets/applet_4
8       ./.gconf/apps/panel/applets/clock_screen0/prefs
16      ./.gconf/apps/panel/applets/clock_screen0
8       ./.gconf/apps/panel/applets/show_desktop_button_screen0
8       ./.gconf/apps/panel/applets/applet_1/prefs
16      ./.gconf/apps/panel/applets/applet_1
8       ./.gconf/apps/panel/applets/workspace_switcher_screen0/prefs
16      ./.gconf/apps/panel/applets/workspace_switcher_screen0
8       ./.gconf/apps/panel/applets/notificationarea_screen0
8       ./.gconf/apps/panel/applets/mixer_screen0
8       ./.gconf/apps/panel/applets/applet_0/prefs
16      ./.gconf/apps/panel/applets/applet_0
8       ./.gconf/apps/panel/applets/window_list_screen0/prefs
16      ./.gconf/apps/panel/applets/window_list_screen0
8       ./.gconf/apps/panel/applets/applet_6/prefs/check
12      ./.gconf/apps/panel/applets/applet_6/prefs
20      ./.gconf/apps/panel/applets/applet_6
8       ./.gconf/apps/panel/applets/trashapplet_screen0
8       ./.gconf/apps/panel/applets/applet_3/prefs
16      ./.gconf/apps/panel/applets/applet_3
192     ./.gconf/apps/panel/applets
8       ./.gconf/apps/panel/toplevels/bottom_panel_screen0/background
16      ./.gconf/apps/panel/toplevels/bottom_panel_screen0
8       ./.gconf/apps/panel/toplevels/top_panel_screen0/background
16      ./.gconf/apps/panel/toplevels/top_panel_screen0
36      ./.gconf/apps/panel/toplevels
8       ./.gconf/apps/panel/objects/object_0
8       ./.gconf/apps/panel/objects/object_5
8       ./.gconf/apps/panel/objects/object_3
8       ./.gconf/apps/panel/objects/object_4
8       ./.gconf/apps/panel/objects/yelp_launcher_screen0
8       ./.gconf/apps/panel/objects/menu_bar_screen0
8       ./.gconf/apps/panel/objects/session_dialog_screen0
8       ./.gconf/apps/panel/objects/firefox_launcher_screen0
8       ./.gconf/apps/panel/objects/object_1
8       ./.gconf/apps/panel/objects/object_2
8       ./.gconf/apps/panel/objects/evolution_launcher_screen0
92      ./.gconf/apps/panel/objects
8       ./.gconf/apps/panel/general
332     ./.gconf/apps/panel
8       ./.gconf/apps/nautilus/preferences
16      ./.gconf/apps/nautilus
8       ./.gconf/apps/totem
8       ./.gconf/apps/eog/ui
12      ./.gconf/apps/eog
584     ./.gconf/apps
8       ./.gconf/desktop/gnome/peripherals/keyboard/host-mike-laptop/0
12      ./.gconf/desktop/gnome/peripherals/keyboard/host-mike-laptop
16      ./.gconf/desktop/gnome/peripherals/keyboard
20      ./.gconf/desktop/gnome/peripherals
8       ./.gconf/desktop/gnome/url-handlers/chrome
8       ./.gconf/desktop/gnome/url-handlers/https
8       ./.gconf/desktop/gnome/url-handlers/gopher
8       ./.gconf/desktop/gnome/url-handlers/ftp
8       ./.gconf/desktop/gnome/url-handlers/http
44      ./.gconf/desktop/gnome/url-handlers
8       ./.gconf/desktop/gnome/applications/window_manager
12      ./.gconf/desktop/gnome/applications
8       ./.gconf/desktop/gnome/accessibility/keyboard
12      ./.gconf/desktop/gnome/accessibility
8       ./.gconf/desktop/gnome/background
100     ./.gconf/desktop/gnome
104     ./.gconf/desktop
732     ./.gconf
92      ./.gconfd
784     ./.Trash/mandriva-linux-2007-spring-free-dvd.x86_64
1488    ./.Trash
12      ./.mozilla/firefox/rm7hiyan.default/chrome
40      ./.mozilla/firefox/rm7hiyan.default/extensions/{FD61379B-066A-4afc-89DE-89FB24D907C2}/chrome
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{FD61379B-066A-4afc-89DE-89FB24D907C2}/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/{FD61379B-066A-4afc-89DE-89FB24D907C2}/defaults
72      ./.mozilla/firefox/rm7hiyan.default/extensions/{FD61379B-066A-4afc-89DE-89FB24D907C2}
384     ./.mozilla/firefox/rm7hiyan.default/extensions/{a8dd47cf-239f-48c4-8379-e6b4cbafdcfa}/chrome
416     ./.mozilla/firefox/rm7hiyan.default/extensions/{a8dd47cf-239f-48c4-8379-e6b4cbafdcfa}
112     ./.mozilla/firefox/rm7hiyan.default/extensions/gmailthis@lazyrussian.com/chrome/skin
24      ./.mozilla/firefox/rm7hiyan.default/extensions/gmailthis@ lazyrussian.com/chrome/content
220     ./.mozilla/firefox/rm7hiyan.default/extensions/gmailthis@lazyrussian.com/chrome
232     ./.mozilla/firefox/rm7hiyan.default/extensions/gmailthis@ lazyrussian.com
172     ./.mozilla/firefox/rm7hiyan.default/extensions/{582195F5-92E7-40a0-A127-DB71295901D7}/chrome
92      ./.mozilla/firefox/rm7hiyan.default/extensions/{582195F5-92E7-40a0-A127-DB71295901D7}/components
16      ./.mozilla/firefox/rm7hiyan.default/extensions/{582195F5-92E7-40a0-A127-DB71295901D7}/defaults/transforms
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{582195F5-92E7-40a0-A127-DB71295901D7}/defaults/preferences
28      ./.mozilla/firefox/rm7hiyan.default/extensions/{582195F5-92E7-40a0-A127-DB71295901D7}/defaults
312     ./.mozilla/firefox/rm7hiyan.default/extensions/{582195F5-92E7-40a0-A127-DB71295901D7}
880     ./.mozilla/firefox/rm7hiyan.default/extensions/{d8646e86-22ba-4f3d-8751-23c723ebd7b9}/chrome
944     ./.mozilla/firefox/rm7hiyan.default/extensions/{d8646e86-22ba-4f3d-8751-23c723ebd7b9}
24      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/skin/modern/images
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/skin/modern
32      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/skin
188     ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/content
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/en-US
32      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/locale/ru-RU
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/locale/it-IT
24      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-CN
32      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/locale/ja
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/nl-NL
24      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/zh-TW
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/locale/fr-FR
32      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/locale/uk-UA
32      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/el-GR
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/locale/pt-BR
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/locale/tr-TR
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale/es-ES
28      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome/chromeFiles/locale/de-DE
404     ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles/locale
628     ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/chrome/chromeFiles
632     ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/chrome
44      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/components
8       ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@kei.com/defaults
700     ./.mozilla/firefox/rm7hiyan.default/extensions/foxmarks@ kei.com
16      ./.mozilla/firefox/rm7hiyan.default/extensions/{5BFB67A0-BD75-11DA-A7CB-C9FB9590C853}/chrome
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{5BFB67A0-BD75-11DA-A7CB-C9FB9590C853}/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/{5BFB67A0-BD75-11DA-A7CB-C9FB9590C853}/defaults
44      ./.mozilla/firefox/rm7hiyan.default/extensions/{5BFB67A0-BD75-11DA-A7CB-C9FB9590C853}
100     ./.mozilla/firefox/rm7hiyan.default/extensions/{9c0a1a70-0e03-11da-8bde-f66bad1e3f3a}/chrome
120     ./.mozilla/firefox/rm7hiyan.default/extensions/{9c0a1a70-0e03-11da-8bde-f66bad1e3f3a}
132     ./.mozilla/firefox/rm7hiyan.default/extensions/{37E4D8EA-8BDA-4831-8EA1-89053939A250}/chrome
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{37E4D8EA-8BDA-4831-8EA1-89053939A250}/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/{37E4D8EA-8BDA-4831-8EA1-89053939A250}/defaults
156     ./.mozilla/firefox/rm7hiyan.default/extensions/{37E4D8EA-8BDA-4831-8EA1-89053939A250}
36      ./.mozilla/firefox/rm7hiyan.default/extensions/videodowloader@ videodownloader.net/chrome
8       ./.mozilla/firefox/rm7hiyan.default/extensions/videodowloader@videodownloader.net/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/videodowloader@videodownloader.net/defaults
60      ./.mozilla/firefox/rm7hiyan.default/extensions/videodowloader@ videodownloader.net
168     ./.mozilla/firefox/rm7hiyan.default/extensions/{d166ee2a-36bb-4f33-aff7-e85f912df509}/chrome
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{d166ee2a-36bb-4f33-aff7-e85f912df509}/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/{d166ee2a-36bb-4f33-aff7-e85f912df509}/defaults
196     ./.mozilla/firefox/rm7hiyan.default/extensions/{d166ee2a-36bb-4f33-aff7-e85f912df509}
88      ./.mozilla/firefox/rm7hiyan.default/extensions/{44d0a1b4-9c90-4f86-ac92-8680b5d6549e}/chrome
60      ./.mozilla/firefox/rm7hiyan.default/extensions/{44d0a1b4-9c90-4f86-ac92-8680b5d6549e}/components
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{44d0a1b4-9c90-4f86-ac92-8680b5d6549e}/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/{44d0a1b4-9c90-4f86-ac92-8680b5d6549e}/defaults
180     ./.mozilla/firefox/rm7hiyan.default/extensions/{44d0a1b4-9c90-4f86-ac92-8680b5d6549e}
144     ./.mozilla/firefox/rm7hiyan.default/extensions/{a7c6cf7f-112c-4500-a7ea-39801a327e5f}/chrome
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{a7c6cf7f-112c-4500-a7ea-39801a327e5f}/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/{a7c6cf7f-112c-4500-a7ea-39801a327e5f}/defaults
172     ./.mozilla/firefox/rm7hiyan.default/extensions/{a7c6cf7f-112c-4500-a7ea-39801a327e5f}
284     ./.mozilla/firefox/rm7hiyan.default/extensions/{3CE993BF-A3D9-4fd2-B3B6-768CBBC337F8}/chrome
48      ./.mozilla/firefox/rm7hiyan.default/extensions/{3CE993BF-A3D9-4fd2-B3B6-768CBBC337F8}/components
12      ./.mozilla/firefox/rm7hiyan.default/extensions/{3CE993BF-A3D9-4fd2-B3B6-768CBBC337F8}/defaults/preferences
236     ./.mozilla/firefox/rm7hiyan.default/extensions/{3CE993BF-A3D9-4fd2-B3B6-768CBBC337F8}/defaults
600     ./.mozilla/firefox/rm7hiyan.default/extensions/{3CE993BF-A3D9-4fd2-B3B6-768CBBC337F8}
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{50db75c3-89c0-4a6a-94fc-419e900326c2}/chrome
8       ./.mozilla/firefox/rm7hiyan.default/extensions/{50db75c3-89c0-4a6a-94fc-419e900326c2}/defaults/preferences
12      ./.mozilla/firefox/rm7hiyan.default/extensions/{50db75c3-89c0-4a6a-94fc-419e900326c2}/defaults
32      ./.mozilla/firefox/rm7hiyan.default/extensions/{50db75c3-89c0-4a6a-94fc-419e900326c2}
4240    ./.mozilla/firefox/rm7hiyan.default/extensions
5532    ./.mozilla/firefox/rm7hiyan.default/Cache
368     ./.mozilla/firefox/rm7hiyan.default/bookmarkbackups
8       ./.mozilla/firefox/rm7hiyan.default/gmanager
44      ./.mozilla/firefox/rm7hiyan.default/forecastfox/cache
8       ./.mozilla/firefox/rm7hiyan.default/forecastfox/errors
188     ./.mozilla/firefox/rm7hiyan.default/forecastfox/icons
256     ./.mozilla/firefox/rm7hiyan.default/forecastfox
18004   ./.mozilla/firefox/rm7hiyan.default
18024   ./.mozilla/firefox
2732    ./.mozilla/plugins
20764   ./.mozilla
701688  ./Desktop
4       ./.gnome2_private
865092  .

---

