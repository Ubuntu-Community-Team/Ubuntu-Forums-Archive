---
title: "GDM3 does not start at system boot after upgrade from 18.04 to 20.04"
date: 2021-11-18
forum: Installation &amp; Upgrades
---

### Post by danik56 on 2021-11-18
After the upgrade, I get the default logon screen (not gdm3). From a terminal, when I issue
```
sudo systemctl status gdm
```
it says "dead". Then, if I issue:
```
sudo systemctl restart gdm3
```
the GDM login screen comes up fine.

Looking at system log I see where the failure happened:

--------------------------------------------------------------------------------------------------------------------------------
 
```
Nov 15 17:12:59 ZITO-UBUNTU gnome-keyring-d[3699]: couldn't access control socket: /run/user/5002/keyring/control: No such file or directory
Nov 15 17:12:59 ZITO-UBUNTU dbus-daemon[3086]: [session uid=5002 pid=3086] Activating service name='org.gnome.keyring.SystemPrompter' requested by ':1.20' (uid=5002 pid=3699 comm="/usr/bin/gnome-keyring-daemon --start --foreground" label="unconfined")
Nov 15 17:12:59 ZITO-UBUNTU org.gnome.keyring.SystemPrompter[3707]: Unable to init server: Could not connect: Connection refused
Nov 15 17:12:59 ZITO-UBUNTU dbus-daemon[3086]: [session uid=5002 pid=3086] Activated service 'org.gnome.keyring.SystemPrompter' failed: Process org.gnome.keyring.SystemPrompter exited with status 1
Nov 15 17:12:59 ZITO-UBUNTU gnome-keyring-d[3699]: couldn't create system prompt: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.keyring.SystemPrompter exited with status 1
Nov 15 17:12:59 ZITO-UBUNTU goa-daemon[3233]: /org/gnome/OnlineAccounts/Accounts/account_1522218622_2: Setting AttentionNeeded to TRUE because EnsureCredentials() failed with: No credentials found in the keyring (goa-error-quark, 4)
Nov 15 17:13:02 ZITO-UBUNTU dbus-daemon[3086]: [session uid=5002 pid=3086] Activating service name='org.gnome.keyring.SystemPrompter' requested by ':1.20' (uid=5002 pid=3699 comm="/usr/bin/gnome-keyring-daemon --start --foreground" label="unconfined")
Nov 15 17:13:02 ZITO-UBUNTU org.gnome.keyring.SystemPrompter[4328]: Unable to init server: Could not connect: Connection refused
Nov 15 17:13:02 ZITO-UBUNTU dbus-daemon[3086]: [session uid=5002 pid=3086] Activated service 'org.gnome.keyring.SystemPrompter' failed: Process org.gnome.keyring.SystemPrompter exited with status 1
Nov 15 17:13:02 ZITO-UBUNTU gnome-keyring-d[3699]: couldn't create system prompt: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.keyring.SystemPrompter exited with status 1
Nov 15 17:13:03 ZITO-UBUNTU dbus-daemon[3086]: [session uid=5002 pid=3086] Activating service name='org.gnome.keyring.SystemPrompter' requested by ':1.20' (uid=5002 pid=3699 comm="/usr/bin/gnome-keyring-daemon --start --foreground" label="unconfined")
Nov 15 17:13:03 ZITO-UBUNTU org.gnome.keyring.SystemPrompter[4332]: Unable to init server: Could not connect: Connection refused
Nov 15 17:13:03 ZITO-UBUNTU dbus-daemon[3086]: [session uid=5002 pid=3086] Activated service 'org.gnome.keyring.SystemPrompter' failed: Process org.gnome.keyring.SystemPrompter exited with status 1
Nov 15 17:13:03 ZITO-UBUNTU gnome-keyring-d[3699]: couldn't create system prompt: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.keyring.SystemPrompter exited with status 1
Nov 15 17:13:37 ZITO-UBUNTU systemd[2953]: Stopping Virtual filesystem service - GNOME Online Accounts monitor...
Nov 15 17:13:37 ZITO-UBUNTU systemd[2953]: Stopped Virtual filesystem service - GNOME Online Accounts monitor.
Nov 15 17:23:08 ZITO-UBUNTU systemd[9879]: Starting Virtual filesystem service - GNOME Online Accounts monitor...
```

----------------------------------------------------------------------------------------------------------------------------------------------

Can someone explain what is the issue and how to resolve?

---

### Post by MAFoElffen on 2021-11-18
If you look in
```

/var/log/dist-upgrade/main.log
/var/log/dist-upgrade/apt.log
/var/log/dist-upgrade/term.log

```
And see if there was an error or related problem...

Booting from a USB LiveCD... Look at your install for the existence the gnome-keyring service file:
```

ls /usr/lib/systemd/user/gnome-keyring.service
ls /usr/lib/systemd/user/gnome-keyring-ssh.service

```
If so, if you look at that first file, it should be similar in contents to:
```

[Unit]
Description=Start gnome-keyring for the Secrets Service, and PKCS #11
Before=graphical-session-pre.target

[Service]
Type=oneshot
ExecStart=/usr/bin/gnome-keyring-daemon --start --components pkcs11,secrets

[Install]
WantedBy=graphical-session-pre.target

```
If it is like that and there is an error like you are having, sometimes, when this intermittently after an update fails, a suggested work around is to boot into rescue mode, drop to a root prompt and execute:
```

sudo /usr/bin/gnome-keyring-daemon --replace --components pkcs11,secrets

```
...which unlocks and resets the default keyring. Exit the root prompt and continue booting.

Then see if it comes up...

---

### Post by danik56 on 2021-11-19
Thanks for the info.  I'll look into it...
Just wondering though, if there is a keyring issue, why does GDM start up fine manually from terminal after boot ?

---

### Post by MAFoElffen on 2021-11-20
That 'is' a good question... LOL. I think this is what is going on on going around that...

gnome-keyring.service is called by graphical-session-pre.target before it tries to start up the graphical login manager. GDM, LightDM, etc. After th Lgin, then it satarts the Linux Graphics Layer (XServer, Wayland, etc,) On login to the graphical login manager, it shares secrets through gnome-keyring...

If you log in through a terminal, then it uses gnome-keyring instead of gnome-keyring.service. It uses the app, instead of using it as a daemon/service. I'm thinking there are different requirements for the two modes.

---

### Post by danik56 on 2021-11-21
As a workaround, I added the following line to Crontab:   "@reboot /bin/sleep 30 ; /bin/systemctl restart gdm3"
Now after reboot I have GDM running as before the upgrade.

I was wondering if it makes sense to upgrade to GNOME 40 ??

---

