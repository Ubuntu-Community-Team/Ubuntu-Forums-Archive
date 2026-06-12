---
title: "What Port is CouchDB running on?"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MarkusThielmann on 2009-10-23
When installing Karmic, CouchDB will be running even if Ubuntu One is not installed.

I'd like to use CouchDB for my own project, but I'm unable to figure out what Port it is running on? How does Ubuntu trigger it's usage for a specific user? Any documentation on that?

---

### Post by wnelson on 2009-10-23
To find out what port an app is running on run netstat -tanup

---

### Post by twisted_steel on 2009-10-23
Check out the dbus.sh script in this bzr branch: [http://bazaar.launchpad.net/~sil/bindwood/find-desktop-couch-with-dbus/files/head%3A/chrome/content/](http://bazaar.launchpad.net/~sil/bindwood/find-desktop-couch-with-dbus/files/head%3A/chrome/content/)

---

### Post by 23meg on 2009-10-23
It's started on a random port every time. This will tell you which one it's running on:

```
dbus-send --session --print-reply --dest=org.desktopcouch.CouchDB / org.desktopcouch.CouchDB.getPort
```

---

