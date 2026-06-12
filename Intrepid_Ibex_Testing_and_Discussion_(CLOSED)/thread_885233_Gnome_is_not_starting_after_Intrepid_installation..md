---
title: "Gnome is not starting after Intrepid installation."
date: 2008-08-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DayOldPorridge on 2008-08-09
The error message is the standard "your session lasted less than 10 seconds" dialog box, and when I click 'see log file' it lists a whole bunch of things that failed, but unfortunately I didn't copy it all.  xD  At the moment I'm not using the laptop this happened on, so I can't reboot and see the message again right now.  But has anyone else had this problem when they upgraded to Intrepid?

---

### Post by PmDematagoda on 2008-08-09
It would be very useful if you could obtain and post the error messages that are turned up.

---

### Post by wien on 2008-08-11
I'm having the same problem. My .xsession_errors file (which is displayed in the error box DayOldPorridge mentioned) contains:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
** (gnome-session:6190): DEBUG: GsmXsmpServer: SESSION_MANAGER=local/uppercut:/tmp/.ICE-unix/6190

** (gnome-session:6190): DEBUG: GsmManager: setting client store 0x1187400
** (gnome-session:6190): DEBUG: GsmManager: append_default_apps ()
** (gnome-session:6190): DEBUG: GsmManager: Looking for: gnome-settings-daemon.desktop
** (gnome-session:6190): DEBUG: GsmManager: Found in: /etc/xdg/autostart/gnome-settings-daemon.desktop
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/gnome-settings-daemon.desktop
** (gnome-session:6190): DEBUG: GsmManager: read gnome-settings-daemon.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App1 to store
** (gnome-session:6190): DEBUG: GsmManager: Looking for: gnome-wm.desktop
** (gnome-session:6190): DEBUG: GsmManager: Found in: /usr/share/gnome/autostart/gnome-wm.desktop
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/gnome/autostart/gnome-wm.desktop
** (gnome-session:6190): DEBUG: GsmManager: read gnome-wm.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App2 to store
** (gnome-session:6190): DEBUG: GsmManager: Looking for: gnome-panel.desktop
** (gnome-session:6190): DEBUG: GsmManager: Found in: /usr/share/applications/gnome-panel.desktop
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/applications/gnome-panel.desktop
** (gnome-session:6190): DEBUG: GsmManager: read gnome-panel.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App3 to store
** (gnome-session:6190): DEBUG: GsmManager: Looking for: nautilus.desktop
** (gnome-session:6190): DEBUG: GsmManager: Found in: /usr/share/applications/nautilus.desktop
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/applications/nautilus.desktop
** (gnome-session:6190): DEBUG: GsmManager: read nautilus.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App4 to store
** (gnome-session:6190): DEBUG: GsmManager: append_autostart_apps (/home/erik/.config/autostart)
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /home/erik/.config/autostart/pidgin.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /home/erik/.config/autostart/pidgin.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App5 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /home/erik/.config/autostart/tomboy.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /home/erik/.config/autostart/tomboy.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App6 to store
** (gnome-session:6190): DEBUG: GsmManager: append_autostart_apps (/usr/local/share/gnome/autostart)
** (gnome-session:6190): DEBUG: GsmManager: append_autostart_apps (/usr/share/gnome/autostart)
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/gnome/autostart/at-spi-registryd-wrapper.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /usr/share/gnome/autostart/at-spi-registryd-wrapper.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App7 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/gnome/autostart/gnome-keyring-daemon-wrapper.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /usr/share/gnome/autostart/gnome-keyring-daemon-wrapper.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App8 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/gnome/autostart/gnome-wm.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /usr/share/gnome/autostart/gnome-wm.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App9 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/gnome/autostart/gnome-login-sound.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /usr/share/gnome/autostart/gnome-login-sound.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App10 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/gnome/autostart/gnome-settings-daemon-helper.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /usr/share/gnome/autostart/gnome-settings-daemon-helper.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App11 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /usr/share/gnome/autostart/gnome-session-splash.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /usr/share/gnome/autostart/gnome-session-splash.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App12 to store
** (gnome-session:6190): DEBUG: GsmManager: append_autostart_apps (/usr/share/gdm/gnome/autostart)
** (gnome-session:6190): DEBUG: GsmManager: append_autostart_apps (/etc/xdg/autostart)
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/gnome-settings-daemon.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/gnome-settings-daemon.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App13 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/gnome-at-session.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/gnome-at-session.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App14 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/smart-notifier.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/smart-notifier.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App15 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/user-dirs-update-gtk.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/user-dirs-update-gtk.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App16 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/pulseaudio-module-xsmp.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/pulseaudio-module-xsmp.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App17 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/bluetooth-applet.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/bluetooth-applet.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App18 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/gnome-volume-manager.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/gnome-volume-manager.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App19 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/gnome-power-manager.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/gnome-power-manager.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App20 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/redhat-print-applet.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/redhat-print-applet.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App21 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/trackerd.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/trackerd.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App22 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/nm-applet.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/nm-applet.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App23 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/jockey-gtk.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/jockey-gtk.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App24 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/evolution-alarm-notify.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/evolution-alarm-notify.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App25 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/tracker-applet.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/tracker-applet.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App26 to store
** (gnome-session:6190): DEBUG: GsmAutostartApp: setting desktop filename to /etc/xdg/autostart/update-notifier.desktop
** (gnome-session:6190): DEBUG: GsmManager: read /etc/xdg/autostart/update-notifier.desktop

** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/App27 to store
** (gnome-session:6190): DEBUG: GsmManager: GSM starting to manage
** (gnome-session:6190): DEBUG: GsmManager: starting phase APPLICATION

** (gnome-session:6190): DEBUG: app /org/gnome/SessionManager/App7 is disabled by AutostartCondition
** (gnome-session:6190): DEBUG: GsmManager: Skipping disabled app: /org/gnome/SessionManager/App7
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App8
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-keyring-daemon-wrapper.desktop: command=/usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper startup-id=10d500387171b5782012184652468464400000061900007
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6286
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App11
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-settings-daemon-helper.desktop: command=/usr/lib/gnome-session/helpers/gnome-settings-daemon-helper startup-id=10d500387171b5782012184652469760700000061900010
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6288
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App13
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-settings-daemon.desktop: command=/usr/lib/gnome-settings-daemon/gnome-settings-daemon startup-id=10d500387171b5782012184652469976100000061900012
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6289
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App1
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-settings-daemon.desktop: command=/usr/lib/gnome-settings-daemon/gnome-settings-daemon startup-id=10d500387171b578201218465246118200000061900000
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6291
** (gnome-session:6190): DEBUG: GsmXsmpServer: accept_ice_connection()
** (gnome-session:6190): DEBUG: GsmXSMPClient: Setting up new connection
** (gnome-session:6190): DEBUG: GsmXSMPClient: New client '0x118a210 []'
** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/Client1 to store
** (gnome-session:6190): DEBUG: GsmManager: Client added: /org/gnome/SessionManager/Client1
** (gnome-session:6190): DEBUG: GsmXSMPClient: Initializing client 0x118a210 []
** (gnome-session:6190): DEBUG: GsmXSMPClient: Client '0x118a210 []' received RegisterClient(10d500387171b5782012184652468464400000061900007)
** (gnome-session:6190): DEBUG: GsmManager: Adding new client 10d500387171b5782012184652468464400000061900007 to session
** (gnome-session:6190): DEBUG: GsmXSMPClient: Sending RegisterClientReply to '0x118a210 [10d500387171b5782012184652468464400000061900007]'
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a210 [10d500387171b5782012184652468464400000061900007]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   Program = 'gnome-keyring-daemon-wrapper'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   CloneCommand = '/usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper' 
** (gnome-session:6190): DEBUG: GsmXSMPClient:   RestartCommand = '/usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper' '--sm-client-id' '10d500387171b5782012184652468464400000061900007' 
** (gnome-session:6190): DEBUG: GsmXSMPClient:   UserID = 'erik'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   ProcessID = '6286'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   RestartStyleHint = 2
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a210 [gnome-keyring-daemon-wrapper 10d500387171b5782012184652468464400000061900007]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   _GSM_DesktopFile = 'file:///usr/share/gnome/autostart/gnome-keyring-daemon-wrapper.desktop'
** (gnome-session:6190): DEBUG: GsmAutostartApp: (pid:6288) done (status:0)
** (gnome-session:6190): DEBUG: GsmAutostartApp: (pid:6289) done (status:0)
** (gnome-session:6190): DEBUG: GsmAutostartApp: (pid:6291) done (status:0)
** (gnome-session:6190): DEBUG: GsmManager: ending phase APPLICATION

** (gnome-session:6190): DEBUG: GsmManager: starting phase APPLICATION

** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App9
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-wm.desktop: command=gnome-wm startup-id=10d500387171b5782012184652468497600000061900008
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6294
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App2
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-wm.desktop: command=gnome-wm startup-id=10d500387171b5782012184652462303800000061900001
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6296
No value set for `/apps/gnome-session/gnome-wm/preferred_window_manager'
No value set for `/apps/gnome-session/gnome-wm/preferred_window_manager'
Window manager warning: Failed to read saved session file /home/erik/.config/metacity/sessions/10d500387171b5782012184652462303800000061900001.ms: Failed to open file '/home/erik/.config/metacity/sessions/10d500387171b5782012184652462303800000061900001.ms': No such file or directory
** (gnome-session:6190): DEBUG: GsmXsmpServer: accept_ice_connection()
Window manager warning: Failed to read saved session file /home/erik/.config/metacity/sessions/10d500387171b5782012184652468497600000061900008.ms: Failed to open file '/home/erik/.config/metacity/sessions/10d500387171b5782012184652468497600000061900008.ms': No such file or directory
** (gnome-session:6190): DEBUG: GsmXSMPClient: Setting up new connection
** (gnome-session:6190): DEBUG: GsmXSMPClient: New client '0x118a2a0 []'
** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/Client2 to store
** (gnome-session:6190): DEBUG: GsmManager: Client added: /org/gnome/SessionManager/Client2
** (gnome-session:6190): DEBUG: GsmXsmpServer: accept_ice_connection()
** (gnome-session:6190): DEBUG: GsmXSMPClient: Setting up new connection
** (gnome-session:6190): DEBUG: GsmXSMPClient: New client '0x118a330 []'
** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/Client3 to store
** (gnome-session:6190): DEBUG: GsmManager: Client added: /org/gnome/SessionManager/Client3
** (gnome-session:6190): DEBUG: GsmXSMPClient: Initializing client 0x118a2a0 []
** (gnome-session:6190): DEBUG: GsmXSMPClient: Client '0x118a2a0 []' received RegisterClient(10d500387171b5782012184652462303800000061900001)
** (gnome-session:6190): DEBUG: GsmManager: Adding new client 10d500387171b5782012184652462303800000061900001 to session
** (gnome-session:6190): DEBUG: GsmXSMPClient: Sending RegisterClientReply to '0x118a2a0 [10d500387171b5782012184652462303800000061900001]'
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a2a0 [10d500387171b5782012184652462303800000061900001]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   Program = 'metacity'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   UserID = 'erik'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   RestartStyleHint = 2
** (gnome-session:6190): DEBUG: GsmXSMPClient:   ProcessID = '6296'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   CurrentDirectory = '/home/erik'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   _GSM_Priority = 20
** (gnome-session:6190): DEBUG: GsmXSMPClient: Initializing client 0x118a330 []
** (gnome-session:6190): DEBUG: GsmXSMPClient: Client '0x118a330 []' received RegisterClient(10d500387171b5782012184652468497600000061900008)
** (gnome-session:6190): DEBUG: GsmManager: Adding new client 10d500387171b5782012184652468497600000061900008 to session
** (gnome-session:6190): DEBUG: GsmManager: ending phase APPLICATION

** (gnome-session:6190): DEBUG: GsmManager: starting phase APPLICATION

** (gnome-session:6190): DEBUG: app /org/gnome/SessionManager/App12 is disabled by AutostartCondition
** (gnome-session:6190): DEBUG: GsmManager: Skipping disabled app: /org/gnome/SessionManager/App12
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App3
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-panel.desktop: command=gnome-panel startup-id=10d500387171b5782012184652463639200000061900002
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6308
** (gnome-session:6190): DEBUG: GsmXSMPClient: Sending RegisterClientReply to '0x118a330 [10d500387171b5782012184652468497600000061900008]'
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a330 [10d500387171b5782012184652468497600000061900008]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   Program = 'metacity'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   UserID = 'erik'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   RestartStyleHint = 2
** (gnome-session:6190): DEBUG: GsmXSMPClient:   ProcessID = '6294'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   CurrentDirectory = '/home/erik'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   _GSM_Priority = 20
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
** (gnome-session:6190): DEBUG: GsmAutostartApp: (pid:6294) done (status:1)
** (gnome-session:6190): DEBUG: GsmXsmpServer: ice_io_error_handler (0x11b89c0)
** (gnome-session:6190): DEBUG: GsmXSMPClient: IceProcessMessagesIOError on '0x118a330 [metacity 10d500387171b5782012184652468497600000061900008]'
** (gnome-session:6190): DEBUG: GsmManager: disconnect client
** (gnome-session:6190): DEBUG: GsmManager: disconnect client: /org/gnome/SessionManager/Client3
** (gnome-session:6190): DEBUG: GsmManager: disconnect for app 'gnome-wm.desktop'
** (gnome-session:6190): DEBUG: GsmXSMPClient: getting restart style
** (gnome-session:6190): DEBUG: GsmManager: restarting app
** (gnome-session:6190): DEBUG: Re-starting app: /org/gnome/SessionManager/App9
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App9
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-wm.desktop: command=gnome-wm startup-id=10d500387171b5782012184652468497600000061900008
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6319
** (gnome-session:6190): DEBUG: GsmStore: Unreffing object: 0x118a330
** (gnome-session:6190): DEBUG: GsmManager: Client removed: /org/gnome/SessionManager/Client3
** (gnome-session:6190): DEBUG: GsmClient: disposing /org/gnome/SessionManager/Client3
** (gnome-session:6190): DEBUG: GsmXSMPClient: xsmp_finalize (0x118a330 [metacity 10d500387171b5782012184652468497600000061900008])
No value set for `/apps/gnome-session/gnome-wm/preferred_window_manager'
** (gnome-session:6190): DEBUG: GsmXsmpServer: accept_ice_connection()
** (gnome-session:6190): DEBUG: GsmXSMPClient: Setting up new connection
** (gnome-session:6190): DEBUG: GsmXSMPClient: New client '0x118a3c0 []'
** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/Client4 to store
** (gnome-session:6190): DEBUG: GsmManager: Client added: /org/gnome/SessionManager/Client4
** (gnome-session:6190): DEBUG: GsmXSMPClient: Initializing client 0x118a3c0 []
** (gnome-session:6190): DEBUG: GsmXSMPClient: Client '0x118a3c0 []' received RegisterClient(10d500387171b5782012184652463639200000061900002)
** (gnome-session:6190): DEBUG: GsmManager: Adding new client 10d500387171b5782012184652463639200000061900002 to session
** (gnome-session:6190): DEBUG: GsmManager: ending phase APPLICATION

** (gnome-session:6190): DEBUG: GsmManager: starting phase APPLICATION

** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App10
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-login-sound.desktop: command=/usr/lib/gnome-session/helpers/gnome-login-sound startup-id=10d500387171b5782012184652468556500000061900009
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6338
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App4
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting nautilus.desktop: command=nautilus --no-desktop --browser  startup-id=10d500387171b5782012184652464118900000061900003
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6339
** (gnome-session:6190): DEBUG: GsmXSMPClient: Sending RegisterClientReply to '0x118a3c0 [10d500387171b5782012184652463639200000061900002]'
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a3c0 [10d500387171b5782012184652463639200000061900002]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   CurrentDirectory = '/home/erik'
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a3c0 [10d500387171b5782012184652463639200000061900002]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   ProcessID = '6308'
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a3c0 [10d500387171b5782012184652463639200000061900002]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   Program = 'gnome-panel'
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a3c0 [gnome-panel 10d500387171b5782012184652463639200000061900002]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   CloneCommand = 'gnome-panel' 
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a3c0 [gnome-panel 10d500387171b5782012184652463639200000061900002]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   RestartCommand = 'gnome-panel' '--sm-client-id' '10d500387171b5782012184652463639200000061900002' '--screen' '0' 
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a3c0 [gnome-panel 10d500387171b5782012184652463639200000061900002]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   UserID = 'erik'
** (gnome-session:6190): DEBUG: GsmXsmpServer: accept_ice_connection()
** (gnome-session:6190): DEBUG: GsmXSMPClient: Setting up new connection
** (gnome-session:6190): DEBUG: GsmXSMPClient: New client '0x118a450 []'
** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/Client5 to store
** (gnome-session:6190): DEBUG: GsmManager: Client added: /org/gnome/SessionManager/Client5
** (gnome-session:6190): DEBUG: GsmXSMPClient: Initializing client 0x118a450 []
** (gnome-session:6190): DEBUG: GsmXSMPClient: Client '0x118a450 []' received RegisterClient(10d500387171b5782012184652468556500000061900009)
** (gnome-session:6190): DEBUG: GsmManager: Adding new client 10d500387171b5782012184652468556500000061900009 to session
** (gnome-session:6190): DEBUG: GsmXSMPClient: Sending RegisterClientReply to '0x118a450 [10d500387171b5782012184652468556500000061900009]'
** (gnome-session:6190): DEBUG: GsmXSMPClient: Set properties from client '0x118a450 [10d500387171b5782012184652468556500000061900009]'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   Program = 'gnome-login-sound'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   CloneCommand = 'gnome-login-sound' 
** (gnome-session:6190): DEBUG: GsmXSMPClient:   RestartCommand = 'gnome-login-sound' '--sm-client-id' '10d500387171b5782012184652468556500000061900009' 
** (gnome-session:6190): DEBUG: GsmXSMPClient:   UserID = 'erik'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   ProcessID = '6338'
** (gnome-session:6190): DEBUG: GsmXSMPClient:   RestartStyleHint = 0
** (gnome-session:6190): DEBUG: GsmAutostartApp: (pid:6338) done (status:0)
** (gnome-session:6190): DEBUG: GsmXsmpServer: ice_io_error_handler (0x11bdac0)
** (gnome-session:6190): DEBUG: GsmXSMPClient: IceProcessMessagesIOError on '0x118a450 [gnome-login-sound 10d500387171b5782012184652468556500000061900009]'
** (gnome-session:6190): DEBUG: GsmManager: disconnect client
** (gnome-session:6190): DEBUG: GsmManager: disconnect client: /org/gnome/SessionManager/Client5
** (gnome-session:6190): DEBUG: GsmManager: disconnect for app 'gnome-login-sound.desktop'
** (gnome-session:6190): DEBUG: GsmXSMPClient: getting restart style
** (gnome-session:6190): DEBUG: GsmManager: autorestart not set, not restarting application
** (gnome-session:6190): DEBUG: GsmStore: Unreffing object: 0x118a450
** (gnome-session:6190): DEBUG: GsmManager: Client removed: /org/gnome/SessionManager/Client5
** (gnome-session:6190): DEBUG: GsmClient: disposing /org/gnome/SessionManager/Client5
** (gnome-session:6190): DEBUG: GsmXSMPClient: xsmp_finalize (0x118a450 [gnome-login-sound 10d500387171b5782012184652468556500000061900009])
** (gnome-session:6190): DEBUG: GsmXsmpServer: accept_ice_connection()
** (gnome-session:6190): DEBUG: GsmXSMPClient: Setting up new connection
** (gnome-session:6190): DEBUG: GsmXSMPClient: New client '0x118a4e0 []'
** (gnome-session:6190): DEBUG: GsmStore: Adding object id /org/gnome/SessionManager/Client6 to store
** (gnome-session:6190): DEBUG: GsmManager: Client added: /org/gnome/SessionManager/Client6
** (gnome-session:6190): DEBUG: GsmXSMPClient: Initializing client 0x118a4e0 []
** (gnome-session:6190): DEBUG: GsmXSMPClient: Client '0x118a4e0 []' received RegisterClient(10d500387171b5782012184652464118900000061900003)
** (gnome-session:6190): DEBUG: GsmManager: Adding new client 10d500387171b5782012184652464118900000061900003 to session
** (gnome-session:6190): DEBUG: GsmManager: ending phase APPLICATION

** (gnome-session:6190): DEBUG: GsmManager: starting phase APPLICATION

** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App6
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting tomboy.desktop: command=tomboy startup-id=10d500387171b5782012184652467341400000061900005
Window manager warning: Failed to read saved session file /home/erik/.config/metacity/sessions/10d500387171b5782012184652468497600000061900008.ms: Failed to open file '/home/erik/.config/metacity/sessions/10d500387171b5782012184652468497600000061900008.ms': No such file or directory
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6344
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App19
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-volume-manager.desktop: command=/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable startup-id=10d500387171b57820121846524613449600000061900018
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6345
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App20
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-power-manager.desktop: command=gnome-power-manager startup-id=10d500387171b57820121846524614137500000061900019
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6346
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App21
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting redhat-print-applet.desktop: command=system-config-printer-applet startup-id=10d500387171b57820121846524614525400000061900020
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6347
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App22
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting trackerd.desktop: command=trackerd startup-id=10d500387171b57820121846524614580200000061900021
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6348
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App23
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting nm-applet.desktop: command=nm-applet --sm-disable startup-id=10d500387171b57820121846524615265000000061900022
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6349
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App24
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting jockey-gtk.desktop: command=jockey-gtk --check 60 startup-id=10d500387171b57820121846524615306900000061900023
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6350
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App25
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting evolution-alarm-notify.desktop: command=/usr/lib/evolution/2.24/evolution-alarm-notify startup-id=10d500387171b57820121846524615997000000061900024
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6351
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App14
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting gnome-at-session.desktop: command=gnome-at-visual -s startup-id=10d500387171b57820121846524612762400000061900013
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6353
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App26
** (gnome-session:6190): DEBUG: GsmAutostartApp: starting tracker-applet.desktop: command=tracker-applet startup-id=10d500387171b57820121846524616048900000061900025
** (gnome-session:6190): DEBUG: GsmAutostartApp: started pid:6355
** (gnome-session:6190): DEBUG: Starting app: /org/gnome/SessionManager/App15

(gnome-session:6190): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Key file contains key 'Terminal' which has value that cannot be interpreted.


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
starting HAL detection for ac adaptors...found /org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_AC
Throttle level is 5

(evolution-alarm-notify:6351): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6346): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(nautilus:6339): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```
It's worth noting that this also happens if I create a fresh user and log in with that, so it's probably not some old preference screwing things up with new updates.

---

### Post by DayOldPorridge on 2008-08-14
Sorry for the *very* late reply, but here is what my .xsession-errors file contains:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /home/dominique/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/scim-bridge.
Smart Common Input Method 1.4.7

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Checking for nVidia: Creating backend ...
not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
Waiting 10 more seconds for Xgl to start...
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

Gdk-ERROR **: The program 'x-session-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 11 error_code 1 request_code 151 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
```

It seems to be a bit different from wien's, though.  I've also tried creating a new user and logging in with that, but it gives me the same error when gnome starts up.

And if it helps, here's the output after I try to start gnome-session from the terminal:

```

** (gnome-session:11706): DEBUG: GsmXsmpServer: SESSION_MANAGER=local/ze-zipaktli:/tmp/.ICE-unix/11706


** (gnome-session:11706): WARNING **: Failed to acquire org.gnome.SessionManager
Segmentation fault (core dumped)

```

---

### Post by DayOldPorridge on 2008-08-14
Bump.

---

