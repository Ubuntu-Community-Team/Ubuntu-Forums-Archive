---
title: "No More &quot;Desktop Settings&quot; after Natty Upgrade?"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by ACMarina on 2011-05-09
I've really been enjoying Natty so far, but I found myself a little issue this morning that I haven't been able to solve..

Every once in a while, I like to change my wallpaper.  I have my computer set up on a LED HDTV, and when the mood strikes me I like to find a new 1920x1080 wallpaper and adjust my mood.  

So I right click and go down to the "Desktop Settings" dealy and click it, right?  Nothing.  I do it a couple more times, and still nothing happens.

Okay... so I go into the settings manager and click on the desktop settings icon.  It opens a window but there's nothing there!

What'd I break, and how do I fix it?

---

### Post by ACMarina on 2011-05-12
Bump, anybody?  I'm googling like crazy but can't find anything..

---

### Post by ACMarina on 2011-05-16
Anyone?

---

### Post by ACMarina on 2011-05-26
C'mon, Ubuntufriends - don't make me go to the XFCE forums!

---

### Post by Toz on 2011-05-26
Can you open up a terminal window (Accessories->Terminal Emulator) and type in:```
xfdesktop-settings
```This will bring up the same Desktop Settings dialog. Can you post back any messages that appear in the terminal window?


Also, close the desktop-settings window, and back in the terminal window, type:```
ps -ef | grep xfwm | grep -v grep
```Please post back those results as well. If there are no results to this last command, you can try typing in:```
xfwm4 --replace &
``` to see if that helps.

---

### Post by ACMarina on 2011-05-27
Thanks for the reply!

xfdesktop-settings gets me the message "Segmentation Fault".

ps -ef (et:al) gives me - ```
jeff     13094 13089  0 May12 ?        00:17:14 xfwm4 --replace --display :0.0 --sm-client-id 2dd0f7c5e-0837-4aac-9af3-7d0c9f0292e9
```

Still nothing there..

---

### Post by zone z5 on 2011-05-27
Try right clicking your desktop and clicking "Change Desktop Background"

---

### Post by ACMarina on 2011-05-27
Nothing happens, z5..  If I go into the settings manager and drill down to the desktop submenu, it opens to a blank window.  I can't change any of my desktop settings.

---

### Post by Toz on 2011-05-27
> **ACMarina said:**
> xfdesktop-settings gets me the message "Segmentation Fault"

Try it again and post back the contents of your ~/.xsession-errors file (please use the code tags to enclose the file contents).

---

### Post by ACMarina on 2011-05-27
Here we go.. 

```
 /etc/gdm/Xsession: Beginning session setup...
Warning: Only changing the first 5 of 16 buttons.
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Warning: Only changing the first 5 of 16 buttons.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
Warning: Only changing the first 5 of 16 buttons.
ssh-agent is already running
xfdesktop[13110]: starting up
Failed to init the UI: Unknown option --sm-config-prefix
Warning: Only changing the first 5 of 16 buttons.

** (xfce4-session:13089): WARNING **: Unable to launch "drapes" (specified by autostart/drapes.desktop): Failed to execute child process "drapes" (No such file or directory)

** (xfce4-session:13089): WARNING **: Unable to launch "compiz --replace" (specified by autostart/Compiz.desktop): Failed to execute child process "compiz" (No such file or directory)

** (xfce4-session:13089): WARNING **: Unable to launch "zeitgeist-datahub" (specified by autostart/zeitgeist-datahub.desktop): Failed to execute child process "zeitgeist-datahub" (No such file or directory)
GNOME_KEYRING_CONTROL=/tmp/keyring-JtcgLb
SSH_AUTH_SOCK=/tmp/keyring-JtcgLb/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-JtcgLb
SSH_AUTH_SOCK=/tmp/keyring-JtcgLb/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-JtcgLb
SSH_AUTH_SOCK=/tmp/keyring-JtcgLb/ssh
xfce4-settings-helper: Another instance is already running. Leaving...

(polkit-gnome-authentication-agent-1:13180): polkit-gnome-1-WARNING **: Failed to register client: The name org.gnome.SessionManager was not provided by any .service files
** (nm-applet:13176): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:13176): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:13176): DEBUG: foo_client_state_changed_cb
** (nm-applet:13176): DEBUG: foo_client_state_changed_cb

(npviewer.bin:13477): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:13477): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:13477): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:13477): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:13477): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:13477): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

** (gnome-system-monitor:13559): WARNING **: SELinux was found but is not enabled.

(xfce4-settings-manager:13562): xfce4-settings-manager-DEBUG: geometry = (200,200)
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
** (nm-applet:13176): DEBUG: foo_client_state_changed_cb
** (nm-applet:13176): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:13176): DEBUG: foo_client_state_changed_cb
NOTE: child process received `Goodbye', closing down

(npviewer.bin:15652): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:15652): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:15652): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:15652): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:15652): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:15652): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:22450): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:22450): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:22450): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:22450): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:22450): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:22450): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:24423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24423): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:24423): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24423): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
*** NSPlugin Viewer  *** ERROR: NPN_GetValue() invoke: Message timeout
*** NSPlugin Wrapper *** ERROR: NPP_DestroyStream() invoke: Broken pipe
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2119):invoke_NPP_URLNotify: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2235):invoke_NPP_DestroyStream: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2119):invoke_NPP_URLNotify: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2235):invoke_NPP_DestroyStream: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2119):invoke_NPP_URLNotify: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2235):invoke_NPP_DestroyStream: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2119):invoke_NPP_URLNotify: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2235):invoke_NPP_DestroyStream: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2119):invoke_NPP_URLNotify: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2235):invoke_NPP_DestroyStream: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2119):invoke_NPP_URLNotify: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** ERROR: NPObject 0xee8140 is no longer valid!

(npviewer.bin:24555): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24555): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24555): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24555): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24555): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:24555): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:32047): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:32047): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:32047): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:32047): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:32047): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:32047): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:32047): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed
npviewer.bin: /build/buildd/nspluginwrapper-1.2.2/src/npw-rpc.c:1190: do_send_NPObject: Assertion `npobj_id != 0' failed.
*** NSPlugin Wrapper *** ERROR: NPN_ReleaseObject() get args: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() wait for reply: Connection closed

(npviewer.bin:3665): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3665): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3665): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3665): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3665): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:3665): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
No bp log location saved, using default.
[000:002] Browser XEmbed support present: 1
[000:002] Browser toolkit is Gtk2.
[000:002] Using Gtk2 toolkit
[000:020] Warning(clientchannel.cc:553): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[000:021] Warning(clientchannel.cc:396): Could not initiate GoogleTalkPlugin connection
[000:021] Warning(optionsfile.cc:22): Load: Could not open file
[000:021] Warning(clientchannel.cc:523): Failed to get GoogleTalkPlugin path. Trying default.
[000:025] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[000:025] Waiting for GoogleTalkPlugin to start...

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
[001:106] Read port file, port=50387
[001:118] Initiated connection to GoogleTalkPlugin
[001:207] Socket connection established
[001:207] ScheduleOnlineCheck: Online check in 5000ms
[001:307] Got cookie response, socket is authorized
[001:307] AUTHORIZED; socket handshake complete
[006:217] HandleOnlineCheck: Starting check
[006:217] HandleOnlineCheck: OK; current state: 3
[179:143] Error(scriptinterface.cc:288): Passed a non-object for onmessasge_callback
[187:548] Warning(clientchannel.cc:553): Unreadable or no port file.  Could not initiate GoogleTalkPlugin connection
[187:549] Warning(clientchannel.cc:396): Could not initiate GoogleTalkPlugin connection
[187:549] Warning(optionsfile.cc:22): Load: Could not open file
[187:549] Warning(clientchannel.cc:523): Failed to get GoogleTalkPlugin path. Trying default.
[187:553] Started GoogleTalkPlugin, path=/opt/google/talkplugin/GoogleTalkPlugin
[187:553] Waiting for GoogleTalkPlugin to start...
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
[188:651] Read port file, port=56088
[188:653] Initiated connection to GoogleTalkPlugin
[188:752] Socket connection established
[188:752] ScheduleOnlineCheck: Online check in 5000ms
[188:852] Got cookie response, socket is authorized
[188:852] AUTHORIZED; socket handshake complete
[193:767] HandleOnlineCheck: Starting check
[193:768] HandleOnlineCheck: OK; current state: 3
[197:070] Error(scriptinterface.cc:288): Passed a non-object for onmessasge_callback
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed

(npviewer.bin:4147): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(npviewer.bin:4147): Gtk-WARNING **: Loading IM context type 'ibus' failed
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
NOTE: child process received `Goodbye', closing down
NOTE: child process received `Goodbye', closing down

(npviewer.bin:5339): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5339): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5339): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5339): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5339): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5339): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:5856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5856): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:5856): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

(npviewer.bin:5856): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:10226): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libxfce.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:10226): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:10226): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:10226): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(npviewer.bin:10226): GdkPixbuf-WARNING **: Error loading XPM image loader: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so: wrong ELF class: ELFCLASS64

(npviewer.bin:10226): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() wait for reply: Connection closed

(xfce4-terminal:14578): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

```

---

### Post by Toz on 2011-05-27
A few more things. 

1. Post back the results of:```
uname -a
```

2. When you run xfdesktop-settings at the command prompt, do you only get "Segmentation error", or does it display anything else?

3. Lets try the .xsession-errors thing again. This time, close all open programs and open two terminal windows. In the first window type:```
tail -f ~/.xsession-errors
``` (this will display a running contents of the file). In the second terminal window, type:```
xfdesktop-settings
```. Post back only the messages from the first terminal window that occur after you entered tail -f.

4. How did you install Natty? Was it a fresh install or an upgrade? If you upgraded, from which version?

---

### Post by Toz on 2011-05-27
And also, can you type the following in the terminal. ```
gdb -ex r -ex bt -ex continue -q --args xfdesktop-settings > log.log 2>&1
```

After the crash, it will look like this command is just hanging there and not taking input. Type in **quit** (the letters won't echo) and the gdb program will end. Then post back the contents of log.log.

---

