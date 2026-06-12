---
title: "fresh install, several issues (64 bit). bus interface daemon?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by ac251404 on 2010-05-02
Just did a complete fresh install of 10.04 on a machine with windows 7. I used the 64 bit ISO (Intel Core 2 Duo). 

Issues: (- problem, --- action taken)

- After the install from the Live CD Ubuntu did not boot into the session manager. 
--- I logged in with the account I created at install and got a gnome session.

- Had no network. No network manager applet visible.
--- Through the terminal I did: ifconfig eth0 up, dhclient3 eth0. Got internet and am now posting this.

- I attempted to log out of gnome in order to set the default session. No menu appears when I press the shutdown button.
--- I'm still in Ubuntu. 

Other annoyances:

- Do not seem to have access/control of the sound card.
- Cannot open restricted driver manager. Following error:
```
org.freedesktop.DBus.Error.FileNotFound: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```
- I just tried to start nm-applet from the terminal and got:
```
process 27224: D-Bus library appears to be incorrectly set up; failed to read machine uuid: UUID file '/var/lib/dbus/machine-id' should contain a hex string of length 32, not length 0, with no other text
See the manual page for dbus-uuidgen to correct this issue.

** (nm-applet:27224): WARNING **: <WARN>  bus_init(): Could not get the system bus.  Make sure the message bus daemon is running!  Message: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory


** (nm-applet:27224): CRITICAL **: nm_remote_settings_system_new: assertion `bus != NULL' failed

** (nm-applet:27224): CRITICAL **: nm_settings_service_export: assertion `priv->bus != NULL' failed

** (nm-applet:27224): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (nm-applet:27224): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service.
  Error: (-1) (unknown)

```

I have run 'apt-get update' and 'apt-get upgrade'. Retrieved 2 minor looking updates, nothing else. 

I am really surprised at such issues. I have installed multiple other releases of Ubuntu on all kinds of systems and never experienced anything near so bad. I will continue poking into the issue myself, I just wanted to get some info up here and see if anyone else is experiencing anything similar. My initial guess is this has to do with using the 64 bit ISO. I think it is the first time I've tried 64 bit Ubuntu.

---

### Post by ac251404 on 2010-05-02
just the process of writing the post apparently led me to figuring it out. i took a closer look at the error from nm-applet and realized there was no machine-id generated from dbus-uuidgen for some reason. not sure how/why this happened. anyway i logged in as root and did the following:

```

/bin/dbus-uuidgen > /var/lib/dbus/machine-id

```

Rebooted and everything is dandy.

I you can't get root access (in the terminal: su -)
Try setting the root password: sudo passwd root

Hope this helps someone

---

### Post by Cholsen on 2010-07-05
Thanks for your hint, I had the same issue with a fresh install of 10.04 x64.

---

### Post by fchevitarese on 2010-10-08
Thank you! 

I've got this same problem and it solved all ;)

---

