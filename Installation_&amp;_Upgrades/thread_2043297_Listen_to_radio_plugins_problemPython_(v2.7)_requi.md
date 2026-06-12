---
title: "Listen to radio plugins problem:Python (v2.7) requires"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2012-08-16
I am using ubuntu 12.04
I am experiencing this problem when I try to play some radios.
I have google but not stisfactory solution:
The error is bellow:
Python (v2.7) requires to install plugins to play media files of the following type: application/xml decoder

---

### Post by dino99 on 2012-08-16
which app is used to listen these radios ?
you might have some usefull errors logged into ~/.xsession-errors

---

### Post by hoboy on 2012-08-16
> **dino99 said:**
> which app is used to listen these radios ?
you might have some usefull errors logged into ~/.xsession-errors

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
** Message: applet now removed from the notification area
Initializing wall options...done
Initializing grid options...done
I/O warning : failed to load external entity "/home/luc/.compiz/session/10f2b7816b7c8c036c134511969060202700000014020033"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
** Message: using fallback from indicator to GtkStatusIcon
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:1692): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Setting Update "main_menu_key"
Setting Update "run_key"
** Message: moving back from GtkStatusIcon to indicator

(gtk-window-decorator:1900): Gdk-CRITICAL **: IA__gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(gtk-window-decorator:1900): Gdk-CRITICAL **: IA__gdk_window_set_events: assertion `GDK_IS_WINDOW (window)' failed

** (zeitgeist-datahub:2116): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

TotemEmbedded-Message: Viewer state: STOPPED
TotemEmbedded-Message: totem_embedded_open_uri: uri [http://cast3.jbstream.net/tunein.php/natedogg265/playlist.qtl](http://cast3.jbstream.net/tunein.php/natedogg265/playlist.qtl) base_uri: [http://soukous.com/index.php?t=sc_player](http://soukous.com/index.php?t=sc_player)
TotemEmbedded-Message: totem_embedded_clear_playlist
TotemEmbedded-Message: totem_embedded_open_internal 'http://cast3.jbstream.net/tunein.php/natedogg265/playlist.qtl' subtitle '(null)' is-browser-stream 0 start-play 1
TotemEmbedded-Message: Viewer state: PLAYING
TotemEmbedded-Message: totem_embedded_do_command: Play
** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(3576): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20:
no suitable plugins found

** Message: Missing plugin: gstreamer|0.10|totem-plugin-viewer|application/xml decoder|decoder-application/xml (application/xml decoder)
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
CRITICAL:Could not find any packages to operate on
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
2012-08-16 15:14:09,544 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-08-16 15:14:09,671 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-08-16 15:14:10,644 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-08-16 15:14:10,958 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-08-16 15:14:10,969 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-08-16 15:14:23,155 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-08-16 15:14:23,156 - softwarecenter.db.database - INFO - reopen() database
2012-08-16 15:14:23,156 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
gpg: /tmp/tmpSiiYDP/trustdb.gpg: trustdb created
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
TotemEmbedded-Message: Viewer state: STOPPED
TotemEmbedded-Message: totem_embedded_setup_stream called: uri [http://38.96.175.236:8814](http://38.96.175.236:8814), base_uri: [http://maliactu.net/jekafo-fm/](http://maliactu.net/jekafo-fm/)
TotemEmbedded-Message: totem_embedded_clear_playlist
** Message: totem_pl_parser_can_parse_from_data couldn't get mimetype
TotemEmbedded-Message: totem_embedded_open_stream called: with size 0
TotemEmbedded-Message: totem_embedded_open_internal 'fd://0' subtitle '(null)' is-browser-stream 1 start-play 1
TotemEmbedded-Message: Viewer state: PLAYING
TotemEmbedded-Message: totem_embedded_set_local_cache: /home/luc/.mozilla/firefox/bpddi6te.default/Cache/2/CF/885CEd01
** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(3576): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20:
no suitable plugins found

** Message: Missing plugin: gstreamer|0.10|totem-plugin-viewer|text/html decoder|decoder-text/html (text/html decoder)
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
CRITICAL:Could not find any packages to operate on
** Message: No installation candidate for missing plugins found.
** Message: Error: Stream contains no data.
gsttypefindelement.c(570): gst_type_find_element_handle_event (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin1/GstTypeFindElement:typefindelement1:
Can't typefind empty stream

TotemEmbedded-Message: Viewer state: STOPPED
TotemEmbedded-Message: totem_embedded_set_error: 'Stream contains no data.'
TotemEmbedded-Message: totem_embedded_set_error_logo called by browser plugin
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r600.so: cannot open shared object file: No such file or directory
java.lang.InterruptedException
	at java.lang.Object.wait(Native Method)
	at sun.plugin2.message.Queue.waitForMessage(Unknown Source)
	at sun.plugin2.message.Pipe$1.run(Unknown Source)
	at com.sun.deploy.util.Waiter$1.wait(Unknown Source)
	at com.sun.deploy.util.Waiter.runAndWait(Unknown Source)
	at sun.plugin2.message.Pipe.receive(Unknown Source)
	at sun.plugin2.main.server.JVMInstance$WorkerThread.run(Unknown Source)
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by linuxisgoed on 2012-12-01
It seems like i'm having the same problem,
I'm trying to listen to 

[http://www.sabc.co.za/wps/portal/SABC/listenlivepopup#fragment-13](http://www.sabc.co.za/wps/portal/SABC/listenlivepopup#fragment-13)

in rhythmbox. It plays fine in firefox but I see a message saying 

"serching for multimedia plugins
python (v2.7) requires to install plugins to play media files of the following type: text/html decoder"

it does not find the plugin it needs and then the following error message appears

Required plugin could not be found
Python (v2.7) requires to install plugins to play media files of the following type: text/html decoder

Any ideas ?

---

