---
title: "Upgraded LTSP from 12.04 to 16.04 and now no cursor on clients!"
date: 2018-08-30
forum: Installation &amp; Upgrades
---

### Post by tomatogoatee on 2018-08-30
Where I work, I set up a 12.04 LTSP server AGES ago. Everything was super with it, until recently. I decided to bite the bullet and bring it to a more current version. The update from 12.04 to 14.04 went smoothly, as did the move to 16.04. (18.04 is out of the question, as there are conflicts with that running on Proxmox.)

The problem I've run into is that, while clients are still able to log in (using Gnome with Metacity as their session), the cursor is invisible. It's odd, because on the login screen, the cursor shows just fine. And if I choose Unity for the session, I get a cursor but nothing else (no menus or the title bar, just desktop icons).

I'm looking for any help. As I mentioned, 18.04 is not an option, as it will not run under Proxmox, which is where this LTSP server lives.

---

### Post by tomatogoatee on 2018-08-31
One view, eh? Well, I was finally able to track down a solution that worked.
[https://itsfoss.com/invisible-mouse-cursor-ubuntu-1310/](https://itsfoss.com/invisible-mouse-cursor-ubuntu-1310/)
Apparently, this stems from a bug in 13.04 that carried over to 14.04. The command to fix it:
```
[COLOR=#000000][FONT=monospace]gsettings set org.gnome.settings-daemon.plugins.cursor active false[/FONT][/COLOR]
```
Only problem is that I need to log in with every client individually and run the command. But it only needs to be run once, thankfully, and not on every boot.

---

### Post by Perfect Storm on 2018-08-31
Good that you fixed your problem. I'll mark the thread solved for you.

The one view is nothing. The counter is broken (for ages).

regards
A.I.

---

