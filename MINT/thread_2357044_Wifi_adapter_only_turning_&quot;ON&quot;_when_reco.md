---
title: "Wifi adapter only turning &quot;ON&quot; when reconnecting or restarting network manager"
date: 2017-03-29
forum: MINT
---

### Post by nortriptyline on 2017-03-29
Hello!
I seem to be having some sort of an issue with my Wifi adapter. Whenever  I boot, the OS doesn't turn the adapter "ON" ("ON" as in blue light  blinking on the adapter, checking for available connections). I have to  either unplug and plug it back in, or stop and then start the network  manager to get it to work (sudo service network-manager stop/start).
** This has happened Ubuntu Gnome and MATE also, but I'm currently running Mint 18.1, so I doubt it's distro related.**
Info about the dongle I'm using:
TRENDnet TEW646-UBH device
Bus 003 Device 002: ID 20f4:646b TRENDnet

I tried solving it by creating "wifi-workaround.service" in /etc/systemd/system, pasting this: 
```
[Unit]
Description=Restart network manager at startup

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=multi-user.target
```

in and enabling the service with
```
sudo systemctl enable wifi-workaround.service
```
but that didn't fix anything either.

---

### Post by howefield on 2017-03-29
Thread moved to the "*MINT*" sub forum.

---

