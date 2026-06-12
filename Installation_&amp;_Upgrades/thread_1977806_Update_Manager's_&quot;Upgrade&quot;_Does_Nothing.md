---
title: "Update Manager's &quot;Upgrade&quot; Does Nothing"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by jun0inoue on 2012-05-10
Hi, I'm a long-time Debian user and relative newcomer to Ubuntu; I started with 11.10 and now trying to upgrade to 12.04, but I can't seem to make it happen at all.  
 * I start Update Manager (UM)
 * UM says "new release 12.04 LTS is available", so I click on "Upgrade"
 * UM shows confirmation dialog saying "= Welcome to Ubuntu 12.04 'Precise Pangolin' =", so I click "Upgrade" again
 * UM asks for password, so I enter password
 * UM quits: no message, no dialog, no nothing.
If I try starting UM again, it still offers the upgrade and the System Settings -> System Info shows "Ubuntu 11.10".

Here's what UM shows in the console, if I invoke it from a console.  All of the messages appear before UM asks for my password.  Nothing shows up in /var/log/syslog in the meantime.  I'd appreciate suggestions about what other information might be relevant.
```

$ jun@jun-MacBookAir ~
update-manager -d

(update-manager:8727): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8727): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8727): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8727): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8727): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8727): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8727): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed

(update-manager:8727): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
extracting 'precise.tar.gz'

(gksu:8727): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:8727): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:8727): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksu:8727): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```Now, there's something a bit confusing about this.  Seeing UM fail, I tried "apt-get update; apt-get upgrade" (or maybe I did dist-upgrade), which did install some packages, though the size seemed way too small (~10s of MB) for a system upgrade. I did that a while ago, and I don't have a log from that, but the following is what I see now, which seems to imply there's no upgrade to do.  Is it possible that I did upgrade the system but the system tools are just saying I didn't?

```

# root@jun-MacBookAir ~
apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```So to summarize, I have three questions:
- For the immediate problem, why is UM exiting without doing anything?
- Is my system already upgraded to 12.04?  How can I check this? (Is there a package/version only available on 12.04?)
- If my system is indeed already upgraded, why is UM offering an upgrade and the system info saying I have 11.10?  Again, how can I investigate this?

---

### Post by darkod on 2012-05-10
You can check what you are running with:
lsb_release -a
uname -r

I don't know much about the rest.

Note that if you are running the previous LTS, 10.04, it shouldn't offer the upgrade to 12.04 until 12.04.1 is released in July.

---

### Post by jun0inoue on 2012-05-10
Thanks for quick reply, Darko.  lsb_release says I'm running 11.10.  I'm pretty sure I never had 10.04 on this machine.
```

# root@jun-MacBookAir ~
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
# root@jun-MacBookAir ~
uname -r
3.0.0-16-generic

```

---

