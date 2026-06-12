---
title: "unable to install lubuntu 14.04 (forcepae)"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by robertk2001 on 2014-04-28
I have quite an old laptop Acer Travelmate 4500 with Intel Pentium M 1.6GHz, 512MB RAM, therefore I can only start liveCD Lubuntu with forcepae parameter.
After system is up and running I try to install it on a HDD drive but nothing happens.
After running 'ubiquity -d gtk_ui' in terminal window following log (see few lines below) is being generated.

Please can anyone help?

Btw. When I chose "Install Lubuntu" from the CD menu after system is booted from CD, eventually I get "Installation failed" windows with mesage "The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again."

Ubiquity 2.18.7
Gtk-Message: Failed to load module "overlay-scrollbar"
debconf (developer): <-- VERSION 2
debconf (developer): --> 0 2.0
debconf (developer): <-- CAPB 
debconf (developer): --> 0 multiselect escape 
debconf (developer): <-- GET ubiquity/custom_title_text
debconf (developer): --> 0 
debconf (developer): <-- GET oem-config/enable
debconf (developer): --> 10 oem-config/enable doesn't exist
debconf (developer): <-- GET ubiquity/automation_failure_command
debconf (developer): --> 0 
debconf (developer): <-- GET ubiquity/failure_command
debconf (developer): --> 0 
debconf (developer): <-- GET ubiquity/success_command
debconf (developer): --> 0 
debconf (developer): <-- GET ubiquity/show_shutdown_button
debconf (developer): --> 0 false
debconf (developer): <-- GET ubiquity/hide_slideshow
debconf (developer): --> 0 false
debconf (developer): <-- GET debian-installer/locale
debconf (developer): --> 0 
ERROR:dbus.proxies:Introspect error on :1.26:/org/freedesktop/UPower: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 636, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 620, in main
    install(args[0], query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 260, in install
    wizard = ui.Wizard(distro)
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 290, in __init__
    mod.ui = mod.ui_class(mod.controller)
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 93, in __init__
    upower.setup_power_watch(self.prepare_power_source)
  File "/usr/lib/ubiquity/ubiquity/upower.py", line 21, in setup_power_watch
    power_state_changed()
  File "/usr/lib/ubiquity/ubiquity/upower.py", line 18, in power_state_changed
    not misc.get_prop(upower, UPOWER_PATH, 'OnBattery'))
  File "/usr/lib/ubiquity/ubiquity/misc.py", line 809, in get_prop
    return obj.Get(iface, prop, dbus_interface=dbus.PROPERTIES_IFACE)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 636, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 620, in main
    install(args[0], query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 260, in install
    wizard = ui.Wizard(distro)
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 290, in __init__
    mod.ui = mod.ui_class(mod.controller)
  File "/usr/lib/ubiquity/plugins/ubi-prepare.py", line 93, in __init__
    upower.setup_power_watch(self.prepare_power_source)
  File "/usr/lib/ubiquity/ubiquity/upower.py", line 21, in setup_power_watch
    power_state_changed()
  File "/usr/lib/ubiquity/ubiquity/upower.py", line 18, in power_state_changed
    not misc.get_prop(upower, UPOWER_PATH, 'OnBattery'))
  File "/usr/lib/ubiquity/ubiquity/misc.py", line 809, in get_prop
    return obj.Get(iface, prop, dbus_interface=dbus.PROPERTIES_IFACE)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by dim162 on 2014-10-23
Sorry i can't help... i have the same problem with an acer aspire 1680, which still turn with ubuntu 10.04. 

When i launch the command *sh -c 'ubiquity gtk-ui', *it runs a few second & stop without message.

Somebody[I] has an idea?!
[/I]

---

