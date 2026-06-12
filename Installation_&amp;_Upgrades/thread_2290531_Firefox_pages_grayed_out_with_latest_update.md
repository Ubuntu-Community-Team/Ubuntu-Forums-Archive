---
title: "Firefox pages grayed out with latest update"
date: 2015-08-13
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2015-08-13
Hi:

I'm running 32-bit Lubuntu 14.04 on a series of Thinkpad X-40s trouble-free since 12.04. Firefox is my primary browser. 

With the latest update, which includes a new version of Firefox, the pages are now grayed out below the page title. By blindly hotkey-entering the url, I can see the page titles, but nothing below that.

This has now happened on two separate systems; I'm currently running Firefox normally on a system that is fully updated, except that I deselected the Firefox update. Importing the .firefox folder from a working system does not solve the problem.

Has anyone else run into this?  Is there a fix for it?

Thanks!

Bill

---

### Post by v3.xx on 2015-08-13
Try opening FF in terminal and see if will spit out any errors.
```
firefox
```

---

### Post by wjbmd48 on 2015-08-13
Thanks! Oh boy, does it ever:
```

bill@bill-ThinkPad-X40:~$ firefox


(process:3231): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(firefox:3231): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(firefox:3231): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(firefox:3231): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(firefox:3231): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
[email]pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm[/email]:25:14
[email]privateTab.isPrivateWindow@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/privateTab@infocatcher.xpi!/bootstrap.js:3538:20
[email]privateTab.updateWindowTitle@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/privateTab@infocatcher.xpi!/bootstrap.js:3324:1
privateTab.initWindow/<@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/privateTab@infocatcher.xpi!/bootstrap.js:411:4
[email]exports.Utils.yield@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/bootstrap.js -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/lib/utils.js:382:12
[email]INIParser.prototype.process@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/bootstrap.js -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/lib/filterStorage.js:870:7
exports.IO.readFromFile/onProgress@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/bootstrap.js -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/lib/io.js:97:15
exports.IO.readFromFile/<@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/bootstrap.js -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/lib/io.js:182:11
[email]TaskImpl_run@resource://gre/modules/Task.jsm[/email]:330:41
[email]Handler.prototype.process@resource://gre/modules/Promise.jsm[/email] -> resource://gre/modules/Promise-backend.js:867:23
[email]this.PromiseWalker.walkerLoop@resource://gre/modules/Promise.jsm[/email] -> resource://gre/modules/Promise-backend.js:746:7
this.PromiseWalker.scheduleWalkerLoop/<@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:688:37
WARNING: content window passed to PrivateBrowsingUtils.isWindowPrivate. Use isContentWindowPrivate instead (but only for frame scripts).
[email]pbu_isWindowPrivate@resource://gre/modules/PrivateBrowsingUtils.jsm[/email]:25:14
[email]privateTab.isPrivateWindow@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/privateTab@infocatcher.xpi!/bootstrap.js:3538:20
[email]privateTab.updatePageContext@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/privateTab@infocatcher.xpi!/bootstrap.js:1712:24
[email]privateTab.popupShowingHandler@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/privateTab@infocatcher.xpi!/bootstrap.js:1677:4
[email]privateTab.handleEvent@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/privateTab@infocatcher.xpi!/bootstrap.js:146:38
[email]openPopup@chrome://global/content/bindings/popup.xml[/email]:56:15
[email]MenuEdit.init@chrome://menuedit/content/menueditoverlay.js[/email]:217:7
@chrome://menuedit/content/menueditoverlay.js:725:29
[email]exports.Utils.yield@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/bootstrap.js -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/lib/utils.js:382:12
[email]INIParser.prototype.process@resource://gre/modules/addons/XPIProvider.jsm[/email] -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/bootstrap.js -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/lib/filterStorage.js:870:7
exports.IO.readFromFile/onProgress@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/bootstrap.js -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/lib/io.js:97:15
exports.IO.readFromFile/<@resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/bootstrap.js -> jar:file:///home/bill/.mozilla/firefox/nn8qfqkv.default-1389563101966/extensions/%7Bd10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d%7D.xpi!/lib/io.js:182:11
[email]TaskImpl_run@resource://gre/modules/Task.jsm[/email]:330:41
[email]Handler.prototype.process@resource://gre/modules/Promise.jsm[/email] -> resource://gre/modules/Promise-backend.js:867:23
[email]this.PromiseWalker.walkerLoop@resource://gre/modules/Promise.jsm[/email] -> resource://gre/modules/Promise-backend.js:746:7
this.PromiseWalker.scheduleWalkerLoop/<@resource://gre/modules/Promise.jsm -> resource://gre/modules/Promise-backend.js:688:37
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::activate-slider' of type `gboolean' from rc file value "((GString*) 0xa8bb9480)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::activate-slider' of type `gboolean' from rc file value "((GString*) 0xa8bb81a0)" of type `GString'

```

---

### Post by vasa1 on 2015-08-13
See if you have any luck with ```
/path/to/firefox/firefox -safe-mode
```from [http://kb.mozillazine.org/Safe_mode](http://kb.mozillazine.org/Safe_mode)

---

### Post by wjbmd48 on 2015-08-13
Thanks!

Nope, when I do that I get a gray half/quarter page.

Here's the output 



/path/to/firefox/firefox -safe-mode

---

### Post by wjbmd48 on 2015-08-13
Oops, here's the output:
```

bill@bill-ThinkPad-X40:~$ firefox -safe-mode


(process:4059): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(firefox:4059): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(firefox:4059): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(firefox:4059): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(firefox:4059): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised

```

---

### Post by vasa1 on 2015-08-13
Maybe try a new profile?```
firefox -ProfileManager
```

---

### Post by wjbmd48 on 2015-08-13
Bingo!!!

Thanks so much, greatly appreciated.

Now all I have to do is import everything into it!

Bill

---

