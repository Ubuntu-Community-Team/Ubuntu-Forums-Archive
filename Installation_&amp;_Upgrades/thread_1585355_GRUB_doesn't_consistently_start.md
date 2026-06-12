---
title: "GRUB doesn't consistently start"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2010-09-30
When I restart, GRUB sometimes doesn't start.  It just hangs at the flashing cursor before grub.

When I restart again, grub works fine.  The flashing cursor shows at the top of the screen for a few seconds, and then there is one or more new lines, and then the grub screen.

This is on an HP Pavilion 640 which is otherwise very stable.

Any ideas?

---

### Post by Rubi1200 on 2010-09-30
Are you still using Jaunty (it is in your sig.)?

---

### Post by 5circles on 2010-09-30
Whoops - I've been meaning to update the signature.

This has been happening through several Ubuntu releases.  First Jaunty, then Karmic, and now Lucid.  So I think it must be something to do with the machine.

---

### Post by dino99 on 2010-09-30
you might watch logs to know about that issue: xsession-errors in your /home (ctrl+h to unhide it) and logviewer (system admin)

be sure that menu.list is gone and you can remove/purge then reinstall grub-pc into synaptic (in a raw, dont reboot without grub installed of course)

---

### Post by Rubi1200 on 2010-09-30
So which version of GRUB do you currently have installed?

---

### Post by 5circles on 2010-11-02
Sorry - I didn't realize how long it has taken me to get back to this.  Too many other projects (and thankfully few Ubuntu reboots).

Rubi1200: Here's what I see from > grub-install -v

grub-install (GNU GRUB 1.98-1ubuntu7)

Dino99:  Redoing the menu is probably a good idea, but I doubt that it is anything to do with x-session.  This is from right at reboot - isn't that before any x windows stuff?

Thanks

---

