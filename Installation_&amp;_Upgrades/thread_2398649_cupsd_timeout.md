---
title: "cupsd timeout"
date: 2018-08-15
forum: Installation &amp; Upgrades
---

### Post by escifell on 2018-08-15
Ubuntu 18.04.1
Tried to customise printers to work with local HP network printers (hplip) and failed. Tried to revert back to vanilla set-up and now cupsd will not start.
Where I am at is I have purged hplip and cups, then reinstalled cups (apt-get install cups) systems hangs at "setting up cups-daemon" then times-out. Running systemctl does not reveal much:

$systemctl status cups.service
&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/etc/systemd/system/cups.service; enabled; vendor preset: enabled)
   Active: failed (Result: timeout) since Wed 2018-08-15 13:56:16 BST; 55s ago
     Docs: man:cupsd(8)
 Main PID: 21874 (code=exited, status=0/SUCCESS)

Aug 15 13:54:46 XPS13 systemd[1]: Starting CUPS Scheduler...
Aug 15 13:56:16 XPS13 systemd[1]: cups.service: Start operation timed out. Terminating.
Aug 15 13:56:16 XPS13 systemd[1]: cups.service: Failed with result 'timeout'.
Aug 15 13:56:16 XPS13 systemd[1]: Failed to start CUPS Scheduler.

However running journalctl reveals:
Aug 15 13:54:46 XPS13 systemd[1]: Starting CUPS Scheduler...
-- Subject: Unit cups.service has begun start-up
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit cups.service has begun starting up.
Aug 15 13:55:14 XPS13 nm-applet[2362]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Aug 15 13:55:14 XPS13 nm-applet[2362]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Aug 15 13:55:14 XPS13 nm-applet[2362]: Can't set a parent on widget which has a parent
Aug 15 13:55:14 XPS13 nm-applet[2362]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Aug 15 13:55:14 XPS13 nm-applet[2362]: gtk_widget_destroy: assertion 'GTK_IS_WIDGET (widget)' failed
Aug 15 13:55:14 XPS13 nm-applet[2362]: Can't set a parent on widget which has a parent
Aug 15 13:56:16 XPS13 systemd[1]: cups.service: Start operation timed out. Terminating.
Aug 15 13:56:16 XPS13 systemd[1]: cups.service: Failed with result 'timeout'.
Aug 15 13:56:16 XPS13 systemd[1]: Failed to start CUPS Scheduler.
-- Subject: Unit cups.service has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit cups.service has failed.

So I suspect I have done something to my network manager. Is there a simple fix please as I seem to have a rouge widget?

---

