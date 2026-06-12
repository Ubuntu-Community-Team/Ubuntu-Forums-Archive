---
title: "[xubuntu] lightdm kicks out of the session after 14.04 upgrade"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Sunbriel on 2014-04-18
Today a notification about the 14.04 upgrade popped up on my working 13.10 Xubuntu installation. Decided to go for it, let it install and do its bidding. After downloading/removing/replacing stuff, a reboot was requested. I agreed on this part of the standard upgrade procedure. Xubuntu booted up, and so I went on with logging in to my account. I logged in successfully, desktop started loading, but after a couple of seconds I was kicked out of the session. I tried all the tricks on the internet I stumbled upon, but none worked. I am able to log in to Guest account with no problem. I have no idea what is going on and would like to fix this without having to do a fresh installation. Any and all instructions and help are welcome.

Edit1:

I ran " cat .xsession-errors " and this is the output:

```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: update-notifier-crash (/var/crash/_usr_share_viber_Viber.0.crash) main pro
cess (4079) terminated with status 1
init: update-notifier-crash (/var/crash/_usr_bin_Xorg.0.crash) main process (407
4) terminated with status 1
init: logrotate main process (4043) killed by TERM signal
init: Disconnected from notified D-Bus bus
```

Edit2:

Managed to solve it by myself. Since I saw Xorg is causing problems, I downloaded NVIDIA drivers and reinstalled them. The problem is fixed.

---

