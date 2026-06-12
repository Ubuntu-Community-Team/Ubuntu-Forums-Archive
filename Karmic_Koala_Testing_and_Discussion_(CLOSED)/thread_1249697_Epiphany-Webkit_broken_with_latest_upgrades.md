---
title: "Epiphany-Webkit broken with latest upgrades"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ceramicm on 2009-08-25
Hi, been running Karmic and just installed the latest upgrades and now Epiphany-Webkit (webkit ppa version) isn't working. Here is the terminal output. Can anyone tell me what's wrong? Thanks!

```
cer@amadeus:/home$ epiphany

(epiphany-browser:4524): GLib-GObject-WARNING **: invalid cast from `EphyWebView' to `GtkBin'

(epiphany-browser:4524): Gtk-CRITICAL **: gtk_bin_get_child: assertion `GTK_IS_BIN (bin)' failed

(epiphany-browser:4524): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(epiphany-browser:4524): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(epiphany-browser:4524): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(epiphany-browser:4524): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(epiphany-browser:4524): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(epiphany-browser:4524): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Illegal instruction (core dumped)
```

---

### Post by frenchy82 on 2009-09-12
Hi,

same problem here with karmic and the webkit ppa.
Did you find a solution?

---

### Post by frenchy82 on 2009-09-12
Oops

---

### Post by BwackNinja on 2009-09-12
try deleting/moving your .gnome2/epiphany/ folder, works for me.

---

### Post by ceramicm on 2009-09-12
Right now I am using epiphany-webkit from the official karmic repositories (ie. no PPAs) and it works just fine. There is a problem with webkit's javascript rendering though that causes epiphany to crash, so you need to disable javascript before using epiphany. 

Here's how I got epiphany working:
1. Open epiphany and go to Edit, Preferences, Privacy, and uncheck "Enable JavaScript".

OR

2. If you cannot open epiphany-webkit without it crashing, then open gconf-editor and find /apps/epiphany-webkit/web and uncheck the key "javascript_enabled".

PS. I haven't tested the PPA in a while, so I don't know if it has this problem as well. This problem is pretty annoying. Lack of JavaScript breaks more of the web than I realized it would.

---

### Post by frenchy82 on 2009-09-12
Hi,

ceramicm, this is right. Disabling javascript solve the problem but this is not usable

I hope we will find the good solution because webkit really rocks

---

### Post by robvanvliet on 2009-09-12
Epiphany-webkit works perfectly on Karmic now, including Javascript.

---

### Post by Longinus00 on 2009-09-12
Epiphany works for me as well. I'm browsing through the google chrome experiments right now.

I'm using epiphany-webkit 2.27.91-2

---

### Post by ceramicm on 2009-09-12
Very strange. I too am using epiphany-webkit 2.27.91-2, but I get

```
Illegal instruction (core dumped)
```
and
```
** (epiphany-browser:8242): CRITICAL **: WebKitNetworkRequest* webkit_network_request_new(const gchar*): assertion `uri' failed

(epiphany-browser:8242): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```
when I enable javascript. Will try removing $HOME/.gnome2/epiphany (again)

Edit: Nope, epiphany-webkit still doesn't work unless I disable javascript.

---

### Post by Longinus00 on 2009-09-12
If it helps anyone, I'm using i686.

---

### Post by ceramicm on 2009-09-12
[QUOTE=Longinus00]If it helps anyone, I'm using i686.[/QUOTE]
Do you mean i386 or x86_64? [http://packages.ubuntu.com/karmic/epiphany-webkit](http://packages.ubuntu.com/karmic/epiphany-webkit) only lists i386 and amd64 packages, no optimised packages for i686 processors.

I am using i386 as well (if that is what you meant). Any idea why I would be getting different results? Are you using the webkit team ppa or universe?

---

### Post by frenchy82 on 2009-09-13
I also have "illegal instruction" with epiphany and midori

I had no problem on jaunty

i tried to compile webkit gtk (1.14) but i had the same result
I have the same problem if i use karmic repo or the webkit ppa

Chromium had the same problem some month ago for old cpu users.
Could be this?

(really sorry for my english)

---

### Post by Longinus00 on 2009-09-13
> **ceramicm said:**
> Do you mean i386 or x86_64? [http://packages.ubuntu.com/karmic/epiphany-webkit](http://packages.ubuntu.com/karmic/epiphany-webkit) only lists i386 and amd64 packages, no optimised packages for i686 processors.

I am using i386 as well (if that is what you meant). Any idea why I would be getting different results? Are you using the webkit team ppa or universe?

Yea, I meant the kernel was i686. I'm using the universe repositories.
```

$ apt-cache policy epiphany-webkit
epiphany-webkit:
  Installed: 2.27.91-2
  Candidate: 2.27.91-2
  Version table:
 *** 2.27.91-2 0
        500 http://us.archive.ubuntu.com karmic/universe Packages
        100 /var/lib/dpkg/status
```

---

### Post by frenchy82 on 2009-09-14
hi,

i do think that this is not an epiphany issue.

We have the the same "illegal instruction" with both midori and epiphany

But with webkit 1.12 midori is working (epiphany needs webkit 1.13 at least)

So it could be a webkit issue (or this version of webkit with karmic)

---

### Post by frenchy82 on 2009-10-09
The new ppa update of webkit (1.15.2) solve the problem for me

---

### Post by nutmac on 2009-10-09
Epiphany 2.28 is now on the Karmic repository. Very fast.

---

