---
title: "Strigi Search won't autostart"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2010-04-13
A few days/weeks ago, Strigi Nepomuk stopped loading at login.

If I go onto the Nepomuk configuration window, I see:

---
[ ] Enable Stigi Desktop File Indexer
***Strigi service not running.***
---

If I check that box and click apply, the icon appears in the tray and it starts indexing. For some reason, it just doesn't autostart! I have to manually start Strigi myself after every login. Also, the checkbox is unchecked again after the next login.

There aren't any blatant error messages about it, and the config file seems to be okay:
```
~/.kde/share/config$ cat nepomukserverrc
[Basic Settings]
Start Nepomuk=true

[Service-nepomukstrigiservice]
autostart=true

[main Settings]
Maximum memory=50
Storage Dir[$e]=$HOME/.kde/share/apps/nepomuk/repository/main/
Used Soprano Backend=virtuosobackend
```

Does anybody have a clue why this is happening? It's really quite annoying.

---

### Post by cyberkilla on 2010-04-14
How is Strigi launched at login? Does nepomuk read the config file above and launch it when /it/ starts?

If I launch nepomukserver on the console, it doesn't load Strigi either. I have to specifically run "nepomukservicestub nepomukstrigiservice" or check the box in the Nepomuk Search Settings dialog.

It's not fair!:P

---

### Post by Seren on 2010-04-14
Just for information, I got exactly the same problem.

It might a good idea to look for a bug report or create one if necessary.

Edit : I haven't found a bug related to this problem.

Could you create a bug report on Launchpad against package "strigi" with your opening post description ?

(ubuntu-bug strigi)

---

### Post by cyberkilla on 2010-04-14
> **Seren said:**
> Just for information, I got exactly the same problem.

It might a good idea to look for a bug report or create one if necessary.

Edit : I haven't found a bug related to this problem.

Could you create a bug report on Launchpad against package "strigi" with your opening post description ?

(ubuntu-bug strigi)

Here's my half-baked attempt: [https://bugs.launchpad.net/ubuntu/+source/kdebase-runtime/+bug/563021](https://bugs.launchpad.net/ubuntu/+source/kdebase-runtime/+bug/563021)

---

### Post by cyberkilla on 2010-04-14
Anybody else having this issue? If you could take a look at my bug report in the previous post, it would be greatly appreciated.

---

### Post by Rog131 on 2010-04-15
[https://lists.ubuntu.com/archives/lucid-changes/2010-March/009334.html](https://lists.ubuntu.com/archives/lucid-changes/2010-March/009334.html)

> 
kdebase-runtime (4:4.4.2-0ubuntu1) lucid; urgency=low
...
  [ Jonathan Thomas ]
  * Add kubuntu_89_strigi_ram_detection.diff. This will make Nepomuk  disable
    strigi on systems with less than or equal to 1GB of RAM, on its first
    run. Users will still be able to enable it for themselves if they wish.
...


Do you have less than or equal to 1GB ?

If the System Settings > Advanced > Desktop Search (Strigi settings) is not helping and the patch is turning the Strigi off on the start. Maybe a bug report against the kdebase-runtime will help.


A workaround is to add the strigi call to the autostart. System Settings > Advanced > Autostart.

Fast lane is to add an executable script to the ~/.kde/Autostart/:
```

#!/bin/sh

nepomukservicestub nepomukstrigiservice

```


(add)
Kubuntu Forums link: [http://kubuntuforums.net/forums/index.php?topic=3108103.msg225370#msg225370](http://kubuntuforums.net/forums/index.php?topic=3108103.msg225370#msg225370)

---

### Post by Seren on 2010-04-15
I do confirm I have 1 GiB of RAM.

But I don't exactly get the meaning of the patch: What is a first run ?

It seems to be buggy because I reenabled strigi indexing and then rebooted and it was disabled again.

Is this the expected behavior ?

Edit :
If you don't mind I will copy those information on the bug report

---

### Post by cyberkilla on 2010-04-15
> **Rog131 said:**
> [https://lists.ubuntu.com/archives/lucid-changes/2010-March/009334.html](https://lists.ubuntu.com/archives/lucid-changes/2010-March/009334.html)

Do you have less than or equal to 1GB ?

If the System Settings > Advanced > Desktop Search (Strigi settings) is not helping and the patch is turning the Strigi off on the start. Maybe a bug report against the kdebase-runtime will help.


Yes, I've had my suspicions about that patch myself. It is the only recent change I could find.

I actually have 2GiB RAM, so it shouldn't be doing anything on my system. However, even on a system with 1GiB RAM, it should only interfere and disable it *once*, not every time the user enables it. That's assuming the patch is at fault.

By the way, thanks for the response:)

---

### Post by cyberkilla on 2010-04-17
This bug has been fixed for me. See my bug report above.

---

