---
title: "Hardy problems"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by paul_r_jacobs on 2008-05-02
Just tried to upgrade and now my system won't boot.  I get to the login screen and the hard drive stops seconds after entering the password.

Can anyone point me to links to diagnose this?  I'm not a Linux expert by any means but I've come to depend on Ubuntu: it's cool.  I need it back :-(

---

### Post by hal8000 on 2008-05-02
Try pressing ctrl-alt-F1 or ctrl-alf-F2

These will take you into an alternate console.
Can you now login with your regular user name and password?

If yes have a look in /var/log/messages for clues as to what has gone wrong

---

### Post by paul_r_jacobs on 2008-05-02
The last line:

ADDRCONF (NETDEV_UP): eth0: link is not ready

I had Wifi running although it's been a while since I set it up.  I think eth0 is the hard ehternet port which I have used only for some setup stuff and was, as I remember disabled.

I'm not at home, but if I plug in the Ethernet port temporarily will it at least boot for me based on this message?

If so, I'm guessing that trying to recreate my wifi setup and re-disabling the ethernet port might help, but I guess I don't understand why it would hang altogether because of this.

---

