---
title: "Pidgin / Gutsy root only??"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by Merovius on 2007-10-11
I have upgraded from 7.04 to 7.10 without to much hassle. Only one odd problem. No matter what I do Pidgin will not run unless I do a very undesirable "sudo Pidgin" in the terminal. (saw another post where that was all that worked and tested it.) I uninstalled with Synaptic and reinstalled. Same thing. :confused: Whats up with that? Anyone else see this? Ideas?
TIA

---

### Post by misfitpierce on 2007-10-11
Have not seen that and it is very odd... I have no clue why it would do that. Whats the output in terminal when you just run pidgin?

---

### Post by fragos on 2007-10-11
I did a clean install of 7.10 beta and Pidgin works fine for me.  Open Nautilus to your home directory and do a <ctrl>h.  You should now see a directory .gaim with your local configuration data.

---

### Post by Merovius on 2007-10-11
Here is the output in terminal:

steve@StevesPC:~$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance

---

### Post by Merovius on 2007-10-11
I also uninstalled with add remove programs. Then reinstalled. Still doesn't work.
TIA

---

### Post by misfitpierce on 2007-10-11
Only other thing I might be able to suggest is remove it completely... Download from getdeb which is previous version... Try that one and if works then try upgrade back to gutsy 2.2.1 version. I got no other ideas :confused:

---

### Post by Merovius on 2007-10-11
Yeah tried that. Same thing with the old version. Guess maybe it's time for a clean install when Gutsy is out final..

Thanks all.

---

### Post by misfitpierce on 2007-10-11
That would prob be best... Just be thankful Ubuntu is a fast and painless install :) . Sorry you couldn't fix it and hope new 7.10 serves you well on release with pidgin.

---

### Post by bikeboy on 2007-10-11
When you uninstalled, did you do a purge uninstall? It could be a folder permission issue with ~/.purple or something like that. You would need to either change the permission to the correct ones (wherever the problem is) or remove existing configs and start again (hence the purge).

---

### Post by Mrs Twaddle on 2007-10-12
> **Merovius said:**
> Here is the output in terminal:

steve@StevesPC:~$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance

i too have this, i've tried removing all traces, reinstalling, installing old version, removing, reinstalling libpurple. removed all unwanted packages, rebooted a million times.

i have now given up, i am glad i'm not the only one with the problem though, it means i didn't break it :D

---

### Post by frenzie on 2007-10-13
im having the same issue since upgrading from feisty to Gutsy.
Ive completely removed and pidgin and reinatlled from the package availabe here: [http://packages.ubuntu.com/gutsy/net/pidgin](http://packages.ubuntu.com/gutsy/net/pidgin) and still no joy.

Here is my debug out since upgrading to gutsy

:~$ pidgin -d
(15:13:45) plugins: probing /usr/lib/pidgin/gevolution.so
(15:13:45) plugins: /usr/lib/pidgin/gevolution.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/iconaway.so
(15:13:45) plugins: /usr/lib/pidgin/iconaway.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/gestures.so
(15:13:45) plugins: /usr/lib/pidgin/gestures.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/markerline.so
(15:13:45) plugins: /usr/lib/pidgin/markerline.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/extplacement.so
(15:13:45) plugins: /usr/lib/pidgin/extplacement.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/nautilus.so
(15:13:45) plugins: /usr/lib/pidgin/nautilus.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/timestamp_format.so
(15:13:45) plugins: /usr/lib/pidgin/timestamp_format.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/convcolors.so
(15:13:45) plugins: /usr/lib/pidgin/convcolors.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/spellchk.so
(15:13:45) plugins: /usr/lib/pidgin/spellchk.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/notify.so
(15:13:45) plugins: /usr/lib/pidgin/notify.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/timestamp.so
(15:13:45) plugins: /usr/lib/pidgin/timestamp.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/musicmessaging.so
(15:13:45) plugins: /usr/lib/pidgin/musicmessaging.so is not loadable: undefined symbol: purple_dbus_register_bindings
(15:13:45) plugins: /usr/lib/pidgin/musicmessaging.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/pidginrc.so
(15:13:45) plugins: /usr/lib/pidgin/pidginrc.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(15:13:45) plugins: /usr/lib/pidgin/gtkbuddynote.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/history.so
(15:13:45) plugins: /usr/lib/pidgin/history.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/cap.so
(15:13:45) plugins: /usr/lib/pidgin/cap.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/ticker.so
(15:13:45) plugins: /usr/lib/pidgin/ticker.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/xmppconsole.so
(15:13:45) plugins: /usr/lib/pidgin/xmppconsole.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/local/lib/purple-2/liboscar.so
(15:13:45) plugins: /usr/local/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(15:13:45) plugins: probing /usr/local/lib/purple-2/joinpart.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/newline.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/idle.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/statenotify.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libnovell.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libxmpp.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/ssl-nss.so
(15:13:45) plugins: /usr/local/lib/purple-2/ssl-nss.so is not loadable: libnss3.so: cannot open shared object file: No such file or directory
(15:13:45) plugins: probing /usr/local/lib/purple-2/libgg.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libzephyr.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libicq.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/ssl-gnutls.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libirc.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/psychic.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libyahoo.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/log_reader.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libmsn.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libaim.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/ssl.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libqq.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/buddynote.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libsimple.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/autoaccept.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/offlinemsg.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libjabber.so
(15:13:45) plugins: /usr/local/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(15:13:45) util: Reading file accounts.xml from directory /home/shanna/.purple
(15:13:45) util: Reading file status.xml from directory /home/shanna/.purple
(15:13:45) stun: using server 
(15:13:45) stun: using server 
(15:13:45) sound: Initializing sound output drivers.
(15:13:45) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(15:13:45) gtkblist: added visibility manager: 1
(15:13:45) docklet: created
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance

---

### Post by Merovius on 2007-10-13
Well after a clean install of 7.10 all is well. Really running very well. Almost no problems to speak of. Really nice release. Pidgin worked right from the start.

Thanks for the sugestions and help. ::popcorn:

---

### Post by hanzomon4 on 2007-10-13
Check the ownership of the .gaim or.pidgin file. You may need to chown -R it.

---

### Post by Merovius on 2007-10-14
I can confirm that before the clean install I did not have ownership of .pidgin. It was a root only file.

---

### Post by Mrs Twaddle on 2007-10-16
> **frenzie said:**
> im having the same issue since upgrading from feisty to Gutsy.
Ive completely removed and pidgin and reinatlled from the package availabe here: [http://packages.ubuntu.com/gutsy/net/pidgin](http://packages.ubuntu.com/gutsy/net/pidgin) and still no joy.

Here is my debug out since upgrading to gutsy

:~$ pidgin -d
(15:13:45) plugins: probing /usr/lib/pidgin/gevolution.so
(15:13:45) plugins: /usr/lib/pidgin/gevolution.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/iconaway.so
(15:13:45) plugins: /usr/lib/pidgin/iconaway.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/gestures.so
(15:13:45) plugins: /usr/lib/pidgin/gestures.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/markerline.so
(15:13:45) plugins: /usr/lib/pidgin/markerline.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/extplacement.so
(15:13:45) plugins: /usr/lib/pidgin/extplacement.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/nautilus.so
(15:13:45) plugins: /usr/lib/pidgin/nautilus.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/timestamp_format.so
(15:13:45) plugins: /usr/lib/pidgin/timestamp_format.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/convcolors.so
(15:13:45) plugins: /usr/lib/pidgin/convcolors.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/spellchk.so
(15:13:45) plugins: /usr/lib/pidgin/spellchk.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/notify.so
(15:13:45) plugins: /usr/lib/pidgin/notify.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/timestamp.so
(15:13:45) plugins: /usr/lib/pidgin/timestamp.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/musicmessaging.so
(15:13:45) plugins: /usr/lib/pidgin/musicmessaging.so is not loadable: undefined symbol: purple_dbus_register_bindings
(15:13:45) plugins: /usr/lib/pidgin/musicmessaging.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/pidginrc.so
(15:13:45) plugins: /usr/lib/pidgin/pidginrc.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(15:13:45) plugins: /usr/lib/pidgin/gtkbuddynote.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/history.so
(15:13:45) plugins: /usr/lib/pidgin/history.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/cap.so
(15:13:45) plugins: /usr/lib/pidgin/cap.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/ticker.so
(15:13:45) plugins: /usr/lib/pidgin/ticker.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/lib/pidgin/xmppconsole.so
(15:13:45) plugins: /usr/lib/pidgin/xmppconsole.so is not loadable: ABI version mismatch 2.2.x (need 2.0.x)
(15:13:45) plugins: probing /usr/local/lib/purple-2/liboscar.so
(15:13:45) plugins: /usr/local/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(15:13:45) plugins: probing /usr/local/lib/purple-2/joinpart.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/newline.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/idle.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/statenotify.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libnovell.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libxmpp.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/ssl-nss.so
(15:13:45) plugins: /usr/local/lib/purple-2/ssl-nss.so is not loadable: libnss3.so: cannot open shared object file: No such file or directory
(15:13:45) plugins: probing /usr/local/lib/purple-2/libgg.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libzephyr.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libicq.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/ssl-gnutls.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libirc.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/psychic.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libyahoo.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/log_reader.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libmsn.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libaim.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/ssl.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libqq.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/buddynote.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libsimple.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/autoaccept.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/offlinemsg.so
(15:13:45) plugins: probing /usr/local/lib/purple-2/libjabber.so
(15:13:45) plugins: /usr/local/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(15:13:45) util: Reading file accounts.xml from directory /home/shanna/.purple
(15:13:45) util: Reading file status.xml from directory /home/shanna/.purple
(15:13:45) stun: using server 
(15:13:45) stun: using server 
(15:13:45) sound: Initializing sound output drivers.
(15:13:45) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(15:13:45) gtkblist: added visibility manager: 1
(15:13:45) docklet: created
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance

I get exactly the same, i'm about ready to give up. I've been searching for a duplicate library file or dependancy that may be left over from old pidgin or gaim, and i am getting precisely nowhere.
I don't know where the problem is or why..
as much as i am loving gutsy, i need pidgin to work, and have no means to back up my stuff to do a clean install.

---

### Post by fragos on 2007-10-16
I started from a clean install of 7.10 beta and the update manager has kept it current.  Mine works fine.  It appears that you have some kind of version dependancy mismatch.  Output from my system follows:

fragos@Geo:~$ pidgin -d
(12:33:21) prefs: Reading /home/fragos/.purple/prefs.xml
(12:33:21) prefs: Finished reading /home/fragos/.purple/prefs.xml
(12:33:21) dbus: okkk
(12:33:21) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(12:33:21) plugins: probing /usr/lib/pidgin/nautilus.so
(12:33:21) plugins: probing /usr/lib/pidgin/cap.so
(12:33:21) plugins: probing /usr/lib/pidgin/pidginrc.so
(12:33:21) plugins: probing /usr/lib/pidgin/history.so
(12:33:21) plugins: probing /usr/lib/pidgin/markerline.so
(12:33:21) plugins: probing /usr/lib/pidgin/convcolors.so
(12:33:21) plugins: probing /usr/lib/pidgin/iconaway.so
(12:33:21) plugins: probing /usr/lib/pidgin/ticker.so
(12:33:21) plugins: probing /usr/lib/pidgin/timestamp_format.so
(12:33:21) plugins: probing /usr/lib/pidgin/musicmessaging.so
(12:33:21) plugins: probing /usr/lib/pidgin/extplacement.so
(12:33:21) plugins: probing /usr/lib/pidgin/gestures.so
(12:33:21) plugins: probing /usr/lib/pidgin/timestamp.so
(12:33:21) plugins: probing /usr/lib/pidgin/gevolution.so
(12:33:21) plugins: probing /usr/lib/pidgin/xmppconsole.so
(12:33:21) plugins: probing /usr/lib/pidgin/spellchk.so
(12:33:21) plugins: probing /usr/lib/pidgin/notify.so
(12:33:21) plugins: probing /usr/lib/purple-2/libgg.so
(12:33:21) plugins: probing /usr/lib/purple-2/newline.so
(12:33:21) plugins: probing /usr/lib/purple-2/psychic.so
(12:33:21) plugins: probing /usr/lib/purple-2/libsimple.so
(12:33:21) plugins: probing /usr/lib/purple-2/libjabber.so
(12:33:21) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(12:33:21) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(12:33:21) plugins: probing /usr/lib/purple-2/libirc.so
(12:33:21) plugins: probing /usr/lib/purple-2/libmsn.so
(12:33:21) plugins: probing /usr/lib/purple-2/libbonjour.so
(12:33:21) plugins: probing /usr/lib/purple-2/idle.so
(12:33:21) plugins: probing /usr/lib/purple-2/statenotify.so
(12:33:21) plugins: probing /usr/lib/purple-2/ssl-nss.so
(12:33:21) plugins: probing /usr/lib/purple-2/tcl.so
(12:33:21) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(12:33:21) plugins: probing /usr/lib/purple-2/libqq.so
(12:33:21) plugins: probing /usr/lib/purple-2/libnovell.so
(12:33:21) plugins: probing /usr/lib/purple-2/perl.so
(12:33:21) plugins: probing /usr/lib/purple-2/libsametime.so
(12:33:21) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(12:33:21) plugins: probing /usr/lib/purple-2/ssl.so
(12:33:21) plugins: probing /usr/lib/purple-2/libicq.so
(12:33:21) plugins: probing /usr/lib/purple-2/offlinemsg.so
(12:33:21) plugins: probing /usr/lib/purple-2/libzephyr.so
(12:33:21) plugins: probing /usr/lib/purple-2/log_reader.so
(12:33:21) plugins: probing /usr/lib/purple-2/libxmpp.so
(12:33:22) util: Reading file xmpp-caps.xml from directory /home/fragos/.purple
(12:33:22) plugins: probing /usr/lib/purple-2/buddynote.so
(12:33:22) plugins: probing /usr/lib/purple-2/libyahoo.so
(12:33:22) plugins: probing /usr/lib/purple-2/joinpart.so
(12:33:22) plugins: probing /usr/lib/purple-2/autoaccept.so
(12:33:22) plugins: probing /usr/lib/purple-2/liboscar.so
(12:33:22) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(12:33:22) plugins: probing /usr/lib/purple-2/libaim.so
(12:33:22) plugins: probing /usr/lib/purple-2/dbus-example.so
(12:33:22) plugins: probing /usr/lib/purple-2/libmyspace.so
(12:33:22) prefs: /purple/status/scores/offline changed, scheduling save.
(12:33:22) prefs: /purple/status/scores/available changed, scheduling save.
(12:33:22) prefs: /purple/status/scores/invisible changed, scheduling save.
(12:33:22) prefs: /purple/status/scores/away changed, scheduling save.
(12:33:22) prefs: /purple/status/scores/extended_away changed, scheduling save.
(12:33:22) prefs: /purple/status/scores/idle changed, scheduling save.
(12:33:22) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(12:33:22) util: Reading file accounts.xml from directory /home/fragos/.purple
(12:33:22) util: Reading file status.xml from directory /home/fragos/.purple
(12:33:22) certificate: CertificateVerifier x509, singleuse requested but not found.
(12:33:22) certificate: CertificateVerifier singleuse registered
(12:33:22) certificate: CertificatePool x509, ca requested but not found.
(12:33:22) certificate: CertificateScheme x509 requested but not found.
(12:33:22) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(12:33:22) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(12:33:22) certificate: CertificatePool ca registered
(12:33:22) certificate: CertificatePool x509, tls_peers requested but not found.
(12:33:22) certificate: CertificatePool tls_peers registered
(12:33:22) certificate: CertificateVerifier x509, tls_cached requested but not found.
(12:33:22) certificate: CertificateVerifier tls_cached registered
(12:33:22) prefs: /purple/logging/format changed, scheduling save.
(12:33:22) prefs: /purple/logging/format changed, scheduling save.
(12:33:22) prefs: /purple/proxy/type changed, scheduling save.
(12:33:22) prefs: /purple/proxy/host changed, scheduling save.
(12:33:22) prefs: /purple/proxy/port changed, scheduling save.
(12:33:22) prefs: /purple/proxy/username changed, scheduling save.
(12:33:22) prefs: /purple/proxy/password changed, scheduling save.
(12:33:22) certificate: CertificateScheme x509 requested but not found.
(12:33:22) certificate: CertificateScheme x509 registered
(12:33:22) stun: using server 
(12:33:22) sound: Initializing sound output drivers.
(12:33:22) prefs: /pidgin/conversations/placement changed, scheduling save.
(12:33:22) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(12:33:22) gtkblist: added visibility manager: 1
(12:33:22) docklet: created
(12:33:22) blist: Attempted to save buddy list before it was read!
(12:33:22) certificate: CertificateScheme x509 unregistered
(12:33:22) certificate: CertificateVerifier tls_cached unregistered
(12:33:22) certificate: CertificateVerifier singleuse unregistered
(12:33:22) certificate: CertificatePool tls_peers unregistered
(12:33:22) certificate: CertificatePool ca unregistered
(12:33:22) util: Writing file accounts.xml to directory /home/fragos/.purple
(12:33:22) util: Writing file /home/fragos/.purple/accounts.xml
(12:33:22) util: Writing file status.xml to directory /home/fragos/.purple
(12:33:22) util: Writing file /home/fragos/.purple/status.xml
(12:33:22) util: Writing file prefs.xml to directory /home/fragos/.purple
(12:33:22) util: Writing file /home/fragos/.purple/prefs.xml
(12:33:22) main: Unloading all plugins
(12:33:22) plugins: Unloading plugin Gadu-Gadu
(12:33:22) plugins: Unloading plugin SIMPLE
(12:33:22) plugins: Unloading plugin IRC
(12:33:22) plugins: Unloading plugin MSN
(12:33:22) plugins: Unloading plugin Bonjour
(12:33:22) plugins: Unloading plugin NSS
(12:33:22) certificate: CertificateScheme x509 unregistered
(12:33:22) plugins: Unloading plugin QQ
(12:33:22) plugins: Unloading plugin GroupWise
(12:33:22) plugins: Unloading plugin Perl Plugin Loader
(12:33:22) plugins: Unloading plugin Sametime
(12:33:22) plugins: Unloading plugin SSL
(12:33:22) plugins: Unloading plugin ICQ
(12:33:22) plugins: Unloading plugin Zephyr
(12:33:22) plugins: Unloading plugin XMPP
(12:33:22) plugins: Unloading plugin Yahoo
(12:33:22) plugins: Unloading plugin AIM
(12:33:22) plugins: Unloading plugin MySpaceIM
(12:33:22) accels: accel changed, scheduling save.
(12:33:22) accels: accel changed, scheduling save.
(12:33:22) accels: accel changed, scheduling save.
(12:33:22) accels: accel changed, scheduling save.
(12:33:22) accels: accel changed, scheduling save.
(12:33:22) accels: accel changed, scheduling save.
(12:33:22) gtkblist: removed visibility manager: 0
(12:33:22) docklet: destroyed
(12:33:22) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed

---

### Post by Mrs Twaddle on 2007-10-16
Yeah thats what I'm thinking but i can't find it...

i'll try checking things off from your log above to see if i can narrow it down a bit

---

### Post by iceslice on 2007-10-18
I'm having this issue also. It was working fine after the Gutsy upgrade, and just stopped working after one of the updates. I've checked ownership of my config files, and everything looks good. I guess its time to sift through the -d log.

---

### Post by Mrs Twaddle on 2007-10-18
I fixed mine, by grabbing the source from the pidgin site, and installing that.

It then worked.

something isn't installed or upgraded if you previously used pidgin before upgrading to gutsy. But that something is sorted with the source package.
Good luck in finding it.

---

### Post by inc595 on 2007-10-19
I had this same problem of pdgin not running. I thnk this is becuase I had used another repo to install pidgin on fiesty. I needed to remove the libpurple libraries in  /usr/local/lib then run ldconfig and pidgin started right up. Hope this helps someone out.
```

sudo mv /usr/local/lib/libpurple.la /tmp
sudo mv /usr/local/lib/libpurple.so.0.0.1 /tmp
sudo rm /usr/local/lib/libpurple.so.0
sudo ldconfig
```

---

### Post by JeffD on 2007-10-19
> **inc595 said:**
> I had this same problem of pdgin not running. I thnk this is becuase I had used another repo to install pidgin on fiesty. I needed to remove the libpurple libraries in  /usr/local/lib then run ldconfig and pidgin started right up. Hope this helps someone out.
```

sudo mv /usr/local/lib/libpurple.la /tmp
sudo mv /usr/local/lib/libpurple.so.0.0.1 /tmp
sudo rm /usr/local/lib/libpurple.so.0
sudo ldconfig
```



You are definately *The Man*!  That saved me who knows how much hair loss!:)

---

### Post by inc595 on 2007-10-23
Glad to see it worked out for you, thanks.

---

