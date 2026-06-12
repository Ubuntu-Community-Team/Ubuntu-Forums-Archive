---
title: "Todoist fails to start"
date: 2021-01-05
forum: Installation &amp; Upgrades
---

### Post by Tectuktitlay on 2021-01-05
Hi all,

I've just upgrade to Ubuntu 20.04 from 16.04 and am facing a lot of issues... For one I can't get Todoist to work after installing it with Snap. It fails silently, both when starting it from the launcher as well as from the command line. How can I figure out what's wrong? Has anyone faced this before? Any advice would be appreciated.

BRgds,

Tec

---

### Post by tea for one on 2021-01-06
> **Tectuktitlay said:**
> I've just upgrade to Ubuntu 20.04 from 16.04 and am facing [COLOR="#FF0000"]a lot [/COLOR]of issues...

There is no direct upgrade path from 16.04 to 20.04. 
Did you go from 16.04 &#10142; 18.04 &#10142; 20.04?

Anyway, in your position, I would back up my date, download Ubuntu 20.04 (or similar flavour) and try a live session.
Double check that it works to your satisfaction then install and restore your data.

---

### Post by Tectuktitlay on 2021-01-06
Hi tea for one,

I did a clean install of 20.04 after buying a new machine. My main problem is the todoist snap not working. I can run it, but nothing happens. Same from the command line. No error message, nothing.

How can I find out how to fix it or what the problem even is? Seems weird to have to go back to 16.04 to use todoist.

Currently I've downloaded the AppImage version and use that, but I would much prefer to use the snap, since that can be updated automatically and is safer all around. But I also just want to understand what's going wrong...

BRgds,

Tec

---

### Post by #&amp;thj^% on 2021-01-06
This sounds like an apparmor bug, report back if this works:
```
/snap/todoist/current/todoist
```
Example:
```
/snap/todoist/current/todoist
16:27:27.141 &#8250; APPIMAGE env is not defined, current application is not an AppImage

```

---

### Post by Tectuktitlay on 2021-01-06
Works perfectly! Todoist launches. My output:

```

$ /snap/todoist/current/todoist 
00:47:45.709 › APPIMAGE env is not defined, current application is not an AppImage

```

So how can we fix it so that the snap works as intended?

When I launch todoist normally I seem to use "/snap/bin/todoist" which is a soft link to "/usr/bin/snap". &#129300;

BRgds, Tec

---

### Post by #&amp;thj^% on 2021-01-06
Yep, I was just talking to them and 90% of all posters solved it with removing all symlink's the user has/had. IE symlink to Downloads or any.
Let us know if that helped you, otherwise you would have to run a debug against it:
```
sudo strace -u catinbetween -f -D -vv -o ./log.trace /snap/bin/todoist
```
PLEASE PLEASE Do Not paste that here if you run it, it contains around 15k lines. :)
For that I'll post a link if needed.
Second EDIT: If you do run debug look for:
```
kernel.printk_ratelimit = 0
= AppArmor =
Time: sep 22 17:17:47
**Log: apparmor="DENIED" operation="open" profile="snap.electronplayer.electronplayer" name="/mnt/data/Downloads/" pid=20583 comm="head" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```**

---

### Post by Tectuktitlay on 2021-01-06
Don't have symlinks, but did alter my users.dirs. Moved "Downloads" to my NAS. Was not a problem for todoist previously, though, on my ubuntu 16.04 installation.

Where can I post the log? Tried some pastebin alternatives already, but they it's too large (12778 lines).

---

### Post by #&amp;thj^% on 2021-01-06
For now here: [https://forum.snapcraft.io/t/todoist-snap-silently-fails-to-start/20015](https://forum.snapcraft.io/t/todoist-snap-silently-fails-to-start/20015)
I can't reach him ATM
But from what I read, that's enough here>> "Moved "Downloads" to my NAS" ...to trip apparmor, trust me on this.
EDIT: You can add it back after you get up and running.

---

### Post by Tectuktitlay on 2021-01-06
Aargh!

Seems you're right. Reset my user.dirs. Removed todoist snap and reinstalled it. It works now. I'm a bit annoyed that this is required, but seem to share that emotion with many posters on snapcraft.io. Thanks for the help 1fallen!

---

