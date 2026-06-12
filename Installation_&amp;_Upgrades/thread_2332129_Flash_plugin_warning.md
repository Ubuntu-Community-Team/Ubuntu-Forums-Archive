---
title: "Flash plugin warning"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by geovino on 2016-07-28
I keep getting this warning about not being able to install flashplugin installer. I checked in synaptic and I have the newest flash plugin installer. How can I turn off the warning?

running Kubuntu 16.04

---

### Post by ajgreeny on 2016-07-28
Not sure about that warning, nor why you see it but try enabling the canonical-partner repos, which is done from the software sources; you can get to that from synaptic Settings->Repositories->Other Software tab.

Now install adobe-flashplugin, which will remove the flashplugin-installer and see if that gets rid of the warning for you.

---

### Post by howefield on 2016-07-28
Did the error look anything like the attached image, this is just an image for demo, might not be exactly the same but similar ?

---

### Post by geovino on 2016-07-28
Looks like this...

---

### Post by geovino on 2016-07-29
I tried adding partner repo in synaptic and it didn't change anything. when the warning comes up and I click on it it brings up the terminal with pkexec in the terminal header. What is that?

---

### Post by howefield on 2016-07-29
> **geovino said:**
> I tried adding partner repo in synaptic and it didn't change anything. when the warning comes up and I click on it it brings up the terminal with pkexec in the terminal header. What is that?

Copy/paste the terminal output back here.

---

### Post by geovino on 2016-07-29
Hey , this time is did the install...

> flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20160712.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20160712.1.orig.tar.gz)
Get:1 [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20160712.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20160712.1.orig.tar.gz) [27.2 MB]
Fetched 27.2 MB in 14s (1,935 kB/s)                                       
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20160712.1.orig.tar.gz' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20160712.1.orig.tar.gz
Flash Plugin installed.



---

### Post by geovino on 2016-07-29
Looks like its solved now. :)

---

### Post by ajgreeny on 2016-07-29
Great! Please mark as SOLVED from the Thread Tools menu up-top once you are fully sure it really is solved for you. It is a great help to users searching the forum.

---

### Post by geovino on 2016-07-29
Well I rebooted again and the warning came up again. Will we ever know what this problem is?

---

### Post by howefield on 2016-07-29
I sometimes see this "error" when installing the ttf-mscorefonts-installer package and usually hitting the "*Run this action now*" button is sufficient to finish the process off. What happened when you clicked that button ?

---

### Post by geovino on 2016-07-29
one time it said it installed flash plugin and the other times its just a blank terminal with no output.

In the ten years I've used Ubuntu I've never seen this. Maybe its a KDE issue?

---

### Post by howefield on 2016-07-30
No, it isn't specifically a KDE problem, the issue can manifest itself regardless of the desktop environment.

There are a few threads on this subject in these forums with a few suggested fixes, search them out and give them a go.

---

