---
title: "Can't start up xfce"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bcasanov on 2009-04-01
Hi,

I just recently upgraded my Xubuntu install to Jaunty.  Everything works great, except when the system boots up and it does not load xfce, and displays a message that says that there is no exec line in the session file xfce4.  I takes me to an xterm session where I can input xfce4-session to start up an xfce session manually.  How do I remedy this problem?

---

### Post by j1mc on 2009-04-01
Hello,

Thanks for posting this here, and for giving an upgrade-install a shot.  Also, sorry for you having these difficulties.  Have you tried filing a bug on this?  An upgrade installation problem like this should come to the attention of the developers, rather than just being posted in the forums.

I'm glad you found a workaround, though.  :)

If you want to file a bug against this, you could do so here: [https://bugs.launchpad.net/ubuntu/+source/xfce4-session](https://bugs.launchpad.net/ubuntu/+source/xfce4-session)

I do strongly encourage you to file a bug against this problem, but in the meantime, maybe this could be of assistance to you? [http://bbs.archlinux.org/viewtopic.php?id=66492](http://bbs.archlinux.org/viewtopic.php?id=66492)

---

### Post by bcasanov on 2009-04-01
Hi j1mc, thank you for your response.  I haven't filed a bug yet, as I do not have a Launchpad account currently, but I think I might create an account soon so that this can be brought to the developers' attention.  Thank you for providing the link.

---

### Post by bcasanov on 2009-04-02
Okay, now I have reported the bug in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/354204](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/354204)

---

### Post by bcasanov on 2009-04-07
Well, I haven't received a response yet for my bug report, but I just wanted to put here that I can also start xfce by inputting another command besides the one I gave above: startxfce4 

I also wanted to let you know what output comes up on the terminal display once I enter the command, in case it might be pertinent to finding what the problem is:

/usr/bin/startxfce4: X server already running on display :0.0
No default user directories
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
Agent pid 16567
Failed to run gnome-keyring-daemon: Failed to execute child process "gnome-keyring-daemon" (No such file or directory)

(xfce4-panel:16600): xfce4-panel-WARNING **: xfce4-panel is not running
xfdesktop[16599]: starting up

** (update-notifier:16628): WARNING **: already running?

** (nm-applet:16619): DEBUG: applet_common_device_state_changed

(xfce4-xkb-plugin:16675): GLib-CRITICAL **: g_hash_table_destroy: assertion `hash_table != NULL' failed

(xfce4-xkb-plugin:16675): GLib-CRITICAL **: g_hash_table_destroy: assertion `hash_table != NULL' failed

(xfce4-xkb-plugin:16675): GLib-CRITICAL **: g_hash_table_destroy: assertion `hash_table != NULL' failed
** (update-notifier:16605): DEBUG: /usr/lib/update-notifier/apt-check returned 0 (security: 0)
** (update-notifier:16605): DEBUG: crashreport_check


** (xfwm4:16594): WARNING **: Last user time set back to 26442603 (was 26454758)

---

### Post by bcasanov on 2009-04-11
Someone responded to my bug, and gave a solution to the problem.  Here it is:

The following modification in the file /usr/share/xsessions/xfce.desktop solveThe following modification in the file /usr/share/xsessions/xfce.desktop solve the problem

replace :
Exec=startxfce4
with :
Exec=/usr/bin/startxfce4 the problem

replace :
Exec=startxfce4
with :
Exec=/usr/bin/startxfce4

---

