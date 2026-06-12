---
title: "No local textshell with Ubuntu server 11?"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by Blindleistung on 2011-12-02
Hi Community.


I am looking for information on how to ge a local shell:

I have loaded and installed ubuntu server this week, installed on a new  system with Intel MB and G620 processor (cheap sandybridge + GPU). B65  Express chipset, no graphics board.

Installation runs normally using local monitor and keyboard. I did not  select to install desktop. Only samba, print and openssh server.

After first normal boot after installation, the screen goes to standby  immediately after passing BIOS and remains there. no wakeup on local  keyboard action.

But the system runs fine and is accessible via SSH.

Is this normal? Do I need to activate the local text-mode shell for  server? I don't want desktop or graphics, but a local text-shell would  be nice in case the networks gets a cough. Anyone know how to activate it? :confused:

By some INet searching I found that Ubuntu 11 should support Sandybridge GPUs.



thanks for any help.

Achim.

---

### Post by Blindleistung on 2011-12-17
Hi again.

I found something myself now.

(I saw that some people looked in here, so an update might help...)

It looks like the system just mis-detects the monitor. When I disconnect the monitor at powerup, wait for the launch, then connect it, there is a picture. When the monitor is connected during powerup (even if monitor is powered off (not standby, but off)), the terminal is initialized in a way that the monitor cannot show.

Which is strange, as the monitor supports framerates from 50 to 120 Hz, and line-frequencies from 45kHz to beyond 100kHz. Anyway, no picture.

This behavior is reproduceable.

So, to be able to drop into the console in case I need  it, I keep the monitor off...

---

