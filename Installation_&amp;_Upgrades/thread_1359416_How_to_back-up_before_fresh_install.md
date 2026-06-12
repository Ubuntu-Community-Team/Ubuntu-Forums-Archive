---
title: "How to back-up before fresh install?"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Daremo_06 on 2009-12-19
I want to do a fresh installation of 9.10 and I spent some time looking for a guide, but the couple that I found seemed to have holes in them so I don't want to start until I am sure I have everything backed up.

Is there a good COMPLETE (or mostly complete) guide for this?  

Otherwise here are my questions.

What do I need to back up to put my system back the way it is right now?  

I have already done this.

```
sudo dpkg --get-selections > /home/user/package.selections
```

And then copied package.selections to my storage drive.

I also copied over */etc/apt/sources.list*

What about firefox plugins and settings?

Evolution settings?

I know I need to copy my home folder over to my storage drive also, do I need to run ```
gksu nautilus
``` in order to copy hidden files? Or is there a better way to do this so that I properly capture everything?

Will I need to re-associate things once I re-installed 9.10?

Thanks!

---

### Post by phillw on 2009-12-19
> **Daremo_06 said:**
> I want to do a fresh installation of 9.10 and I spent some time looking for a guide, but the couple that I found seemed to have holes in them so I don't want to start until I am sure I have everything backed up.

Is there a good COMPLETE (or mostly complete) guide for this?  

Otherwise here are my questions.

What do I need to back up to put my system back the way it is right now?  

I have already done this.

```
sudo dpkg --get-selections > /home/user/package.selections
```And then copied package.selections to my storage drive.

I also copied over */etc/apt/sources.list*

What about firefox plugins and settings?

Evolution settings?

I know I need to copy my home folder over to my storage drive also, do I need to run ```
gksu nautilus
``` in order to copy hidden files? Or is there a better way to do this so that I properly capture everything?

Will I need to re-associate things once I re-installed 9.10?

Thanks!

Most of your applications are installed by default - you only need to note any you have specifically added yourself.

If you've been a gud boi - then a backup and restore of your ~home will suffice. That will capture all your bookmarks, documents, vids, etc.

doing a backup & restore of ~home is quick & painless - You just need to decide where to put the backup copy.

You can look at like Pybackpack --> [http://www.ubuntugeek.com/pybackpack...x-desktop.html]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html")
Or Clonezilla --> [http://www.tuxradar.com/content/how-...ves-clonezilla]("http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla")

I use the command line for my backups. But, you choose whatever method you're happiest with.

Phill.

---

### Post by laceration on 2009-12-19
A list of your packages is pretty useless, because it mostly consists, not of the programs you installed, but of the software libraries that run system and software.  Since many, probably even most, libraries are updated in subsequent releases there is no reason carry that list over.  It might be useful to look through that list and make a note of software you have installed, so you can reinstall it, but most of what you see there won't make much sense.
Depending on what software you have installed, you may have some other settings in /etc and you might want to copy your /etc/fstab because you mentioned a storage drive so you might have a line in there that automatically mounts it.

---

### Post by terry@softreq.com on 2009-12-19
You could do your install on another (new) disk. 

Keep your current disk as a backup.

If you don't have a lot of files you could copy them to a usb jump drive and then copy them to your installation.

Once your happy with your result, use your current disk as a second internal or external drive :).

---

