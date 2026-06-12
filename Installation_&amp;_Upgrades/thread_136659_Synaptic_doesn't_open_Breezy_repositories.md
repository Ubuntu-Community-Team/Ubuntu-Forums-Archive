---
title: "Synaptic doesn't open Breezy repositories"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by Edward The Bonobo on 2006-02-26
I originally installed Hoary.  Then I upgraded to Breezy, using the CD.  But when I looked at my sources.list, I noticed that the only Breezy repository listed was the CD.

So...I replaced the sources.list with the one shown here: [http://www.ubuntuforums.org/showthread.php?t=87946&highlight=sources+list](http://www.ubuntuforums.org/showthread.php?t=87946&highlight=sources+list) (bored2K's post)

But...when I open Synaptic, I get:  [COLOR="RoyalBlue"]W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists[/COLOR]
and so on for every line in sources.list.  Synaptic still seems to recognise the repositories when I go Rettings...Repostories...  but the versions of some of my applications look kinda old.  For example...I'm trying to upgrade gtkpod and Synaptic is still showing the latest version as 0.94 (isn't 0.99.2 in Breezy backport?)

Any ideas?

---

### Post by bluevoodoo1 on 2006-02-26
You did run...

```

sudo apt-get update
```

after changing your sources.list... right?

What does your sources.list look like? Paste it in here.

---

### Post by Edward The Bonobo on 2006-02-27
Ah...no.  I didn't do 'sudo apt-get update'.

My assumption was that opening up Synaptic would be equivalent to doing this...that it would read my new sources.list and find updates for me.  Wrong, huh?

My new sources.list looks like this:

[I]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe[/I]

By the way...how do I post so that my code is in a scrollable window?

---

### Post by bluevoodoo1 on 2006-02-27
Sources list looks ok, Is is working now after the "sudo apt-get update" ??

you can do the code window with...

(code) (/code) surrounding your code, but replace the instances of ( and ) with [ and ]

---

### Post by Edward The Bonobo on 2006-03-01
vmt.

Yes - didn't know I had to apt-get update.

---

### Post by engla on 2006-03-01
The equivalent to 'update' in synaptic is to hit the reload button.

---

### Post by Edward The Bonobo on 2006-03-01
Thanks.  I'm learning to walk in tiny steps.

---

