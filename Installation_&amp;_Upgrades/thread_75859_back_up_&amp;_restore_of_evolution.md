---
title: "back up &amp; restore of evolution"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by gw90se on 2005-10-14
I am installing Breezy on my laptop at work. I wanted to transfer my e-mail (Evolution) over to it also, along with some other files. I did a back up of the .evolution directory and when I restored it, I have everything except my calendar entries and my e-mail addresses (mine, not contacts). If they aren't in .evolution, where are they?

---

### Post by craigaa on 2005-10-16
In order to backup Evolution do the following from a terminal.

Shutdown relevant processes:

```
gconftool2 --shutdown
evolution --force-shutdown
```

backup the following folders and file:

.evolution
.gconf/apps/evolution
.gnome2_private/Evolution

I use the following command line to backup:

```
tar -cvzf backupname.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution
```

In order to restore, you need to shutdown the processed first.

---

### Post by jogogets on 2006-10-15
Hi all, 

I followed the suggestion in this thread to back up my evolution files. The result is I have saved the evolution-backup.tar.gz package and copied it on a fresh ubuntu install. The problem is its just sitting there on my desktop. I've tried unpacking it in a number of ways but been unsuccesful. Can anyone guide me as to how I can add these files to my evolution directory so that I get my emails and contacts back? I know I'm that close.

Thanks

---

### Post by taygan on 2006-12-28
THis script works great, I've used it for a few reinstalls..  It doesn't keep my pop/smtp stuff, but almost everything else:
 ```

#!/bin/bash

gconftool-2 --shutdown
evolution --force-shutdown
cd ~
tar -cvzf evolution.tar.gz .evolution .gconf/apps/evolution .spamassassin .gnome2_private/Evolution

```

---

### Post by barry626 on 2007-12-14
Good day, I hope this is appropriate for this session.  I am moving out of RH 8.0 with evolution version 1.0.8-11, going into Ubuntu 7.10.   I have ~/.evolution in RH, but don't have .gconf.... or .gnome2_.... directories and files as listed below.  I do have ~/.gnome/accels/Evolution, and ..../accels/evolution-addressbook, and .../accels/evolution-mail-component.  Would anyone know what's what here, and what to back up, and how to reorganize it for Ubuntu?   TIA, Barry

---

### Post by spacedoggy on 2008-05-17
nice one, thanks!

---

