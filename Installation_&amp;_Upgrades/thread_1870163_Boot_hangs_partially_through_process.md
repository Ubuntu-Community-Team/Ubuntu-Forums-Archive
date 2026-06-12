---
title: "Boot hangs partially through process"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by ProntoAnthony on 2011-10-26
Stops at "Starting configure network device security"

I can do ctrl-alt-F1  and from there login.

apt-get install and apt-get upgrade work. Network is active.

When I type 'firefox' I get the response:

Error: no display specified


I tried rebooting. Now it froze at "Starting web server apache2" which normally works. Did a ctl-alt-F1 and then tried "firefox" again. Received the same error message.

Typed in "startx" and amazingly wallpaper and the menubar for Nautilus came up:

"File  Edit  View  Go  Bookmarks  Help"


I can choose menu items and view directories, but that's all. Can call up a terminal session and issue a reboot command. Next time it boots, PC hangs on "Starting CUPS printing spooler/server"

Booted again. This time after  "Starting web server apache2"  the message is:



initctl: Event failed



Any suggestions?

---

### Post by ProntoAnthony on 2011-10-27
I removed VirtualBox 4.1 I had installed (from the Oracle repository) and now Gnome2 comes up on boot. No Unity.

---

