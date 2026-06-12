---
title: "Cups not publishing printer on avahi?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mikeyrb on 2009-10-03
I am having an issue where cups is not publishing my printer on avahi anymore after my upgrade to 9.10.  This was working fine on 9.04.  I have made sure that cups is configured to publish shared printers and allow printing from the internet, and that the printer itself is shared.

Avahi-browse does not show any printer service:

$> avahi-browse -a
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
+ eth0 IPv4 rome [mac address]             Workstation          local

I have also tried watching dbus to see if cups would send anything to avahi, but I don't see any messages (e.g., enabling sharing on a printer I would expect a message).

Any ideas?  Anyone else notice this?

---

### Post by mikeyrb on 2009-10-05
Hmm, maybe it never did work this way.  I suspect something else changed and it could no longer resolve the hostname (adding .local allows it to resolve now, so not sure what changed).  Anyways, I got the OS X machine back up and printing by following [http://www.wikihow.com/Share-a-CUPS-Printer-With-Apple-Mac-OS-X]("http://www.wikihow.com/Share-a-CUPS-Printer-With-Apple-Mac-OS-X").

---

