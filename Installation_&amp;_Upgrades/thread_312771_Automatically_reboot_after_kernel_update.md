---
title: "Automatically reboot after kernel update?"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by dbr on 2006-12-04
After searching/asking around a bit, I've found nothing, so many someone here could answer or explain :
Basicly, I have Ubuntu Dapper Server installed on a machine, running as a shell server (Currently it's used for remote-access to my network, and for a few friends to IRC off, among other stuff)

Every ~30 days or so it will (seemingly) randomly reboot. The only line in any logs that seem related too it is "[time stamp] reboot".

It's happened about 3 or 4 times (The install is only about 3 or 4 months old), I original had ubuntu-desktop installed, with a lot of stuff uninstalled (Like OpenOffice) - it was really only there to make it simpler to change network settings, and get X working for ratpoison (window manager, tiles windows, and doesn't need a mouse - worked well for monitoring the server via a few terminals).
Recently I removed everything X (Gnome, X11 etc) related since the machine was being moved "out the way" (So no monitor, so no need for a GUI).

Anyway, it'd reboot itself, which was annoying, then I re-setup my screen session and forget it happened, none the wiser..
But, this last time, I recently edited the motd file, and removed the line with the kernel version and such in.
Then, after it had rebooted, the line was magically back (And wiped the first line of the old motd), which made me think the rebooting problem may be relating to updates - It makes sense, kernel updates seem to be vaugly a month apart, it updates the motd with the new kernel version, the ex-Gnome-update-notifier always promted you to reboot after a kernel update.


"<@dbr> But it shouldn't just reboot itself as soon as the update is done
[01:29] <@switch> ubuntu right?
[01:29] <@switch> under some settings iirc ubuntu will reboot after a while if no usage is being recorded and a new kernel update was automatically downloaded"

Makes sense, in a (slightly annoying) way. But, if this is true (As all this is just educated guessing..) - is there a way to disable the automatic reboot part of the kernel update? Idealy it'd do something like leave a mail message for me, or echo a message to a file in my home dir instead.

If it's not relating to kernel updates (And it just so happened to update the kernel between reboots, and rebooted for a seperate reason) - Any idea why a machine would reboot every approx' 30 days?


In short : Does Ubuntu automatically reboot after a kernel update, if theres no activity on the machine - if so, how can I disable this?
- Ben

---

