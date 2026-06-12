---
title: "Nautilus problems in 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by rich52x on 2011-05-01
Since upgrading to 11.04 yesterday, nauilus has been acting strangely. It takes about 30 seconds for a right click on the desktop to respond, whereas before it would've taken 1 or 2. Also, when trying to open a directory, say, the Home direcotry accessible from the launcher, it takes about a minute to open, which is odd, because all of my other applications (Chrome, Banshee etc) ares all running smoothly. And when the direcotry windowe does open, within 10 sconds it will turn grey and prompt me to force quit. When i try to open nautilus from a terminal, it comes back with the message

```
(nautilus:3508): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

Any help you can give would be much appreciated.

Rich

---

### Post by rich52x on 2011-05-01
anyone?

---

### Post by ggdagg on 2011-05-02
Hi, 

I have the same problem since upgrade yesterday but in my side impossible to open a directory from Places or right click on the desktop even after 1 min to wait.
All others applications (Firefox, Chrome, Totem...) works perfectly. When I launch Nautilus in Terminal, I have this kind of error (not exactly the same as yours) :

```
Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
```Could you check if you have the same error ?

---

### Post by dino99 on 2011-05-02
there might be some other problems, check for packages:

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure nautilus
sudo dpkg-reconfigure -phigh -a (may take a while, dont stop it)

and of course looka at errors logged into .xsession-errors (/home, ctrl+h to unhide it) and /var/log (system admin logviewer)

note: if some ppa packages are used like gnome3, then dont complain

---

### Post by ggdagg on 2011-05-02
Hi, 

Thanks for your answer. And yes you're right, I used ppa packages for gnome 3...so I know what's that mean !
Thanks :'( !!!!

---

### Post by rich52x on 2011-05-03
I punched those commands in, still no dice on nautilus
still getting the same error when launching from a terminal

There was a hefty amount which i saw in relation to nautilus in the .xsession-errrors, there was this :
```
(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1861): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
```
And later in the file there was this:
```
* (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Could not get syncdaemon's root dir: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)
ERROR:Identi.ca:Facebook: Authentication failed - Auth needs updating
INFO:Identi.ca:Loading complete: 1 - []

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
** (<unknown>:1852): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
** (<unknown>:1852): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1852): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1852): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)
INFO:Identi.ca:Cleaning up database...
INFO:Identi.ca:Found 2000 records in the messages stream for account d9c6f9e2016d11e09eeb0013023f0bf1

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
** (process:1869): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

** (nautilus:1861): WARNING **: Error calling get_folders: Message did not receive a reply (timeout by message bus)

** (nautilus:1861): WARNING **: Error calling current_status: Message did not receive a reply (timeout by message bus)
```

Atm im just using thunar as a temporary file manager and just not right clicking the desktop.

---

