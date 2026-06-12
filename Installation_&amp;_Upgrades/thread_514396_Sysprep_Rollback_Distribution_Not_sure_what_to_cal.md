---
title: "Sysprep? Rollback? Distribution? Not sure what to call it..."
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by disabledveteran on 2007-07-31
If I want to setup ubuntu, clone it to multiple systems and provide those to various remote locations, is there a way to force the users to enter a unique name/IP/etc. when they first boot the system?

Thanks!

---

### Post by kidders on 2007-08-01
Hi there,

There are a few ways of doing this sort of thing. For distribution to a common network, the neatest solution might be to configure your master system to use a hostname & IP address provided by a DHCP server. You could set these centrally, based on MAC addresses.

Even if you can do that, you will still need some way of making the first boot interactive, so you can at least set up a new unprivileged local account. One possibility could be ...[LIST]
[*]Create a new service (just like cupsd or samba) and add it to the startup sequence for, say, runlevel 3.
[*]Have the service's "start" routine ask for a username, "useradd" it, and run "passwd" on it, to let the user type a password.
[*]You might like to alter the skeleton home directory, to customise the new user's desktop environment a little.
[*]Have the service delete itself from the startup sequence. If you wanted to, you could use its "stop" routine to do this, so the service would keep running until the end user manages to successfully boot & shut down his PC at least once.[/LIST]What do you think?

---

