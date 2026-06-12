---
title: "Update Error"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by hoffboy on 2007-02-22
Power failed during Software Updates, and I was away at dinner so the battery ran out before the updates were complete. I rebooted, and now when I attempt to run the Software Updates I get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When I attempted to to enter the suggested bits in the terminal, I was told I needed super user rights. I'm a complete noob so this scares me somewhat. Any thoughts on a fix?

TIA

---

### Post by Rhubarb on 2007-02-22
You need to type this into the terminal:
```
sudo dpkg --configure -a
```
It'll then ask you for your password.

---

### Post by hoffboy on 2007-02-22
> **Rhubarb said:**
> You need to type this into the terminal:
```
sudo dpkg --configure -a
```
It'll then ask you for your password.

Thanks. It looked like that was going to work (lots of activity in the terminal, which seems  like a loaded gun to me) but then this error showed up:

dpkg: error processing gnome-applets-data (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.

And after some more processing it ended with:

dpkg: error processing gnome-applets-data (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.


Thoughts? TIA

---

### Post by Kateikyoushi on 2007-02-22
You can reinstall the package with the following command.

```
sudo aptitude reinstall gnome-applets-data
```

---

### Post by pearlie on 2007-02-22
Thanks - I had a hard hang whilst upgrading, and this method worked for me once I rebooted into gnome-failsafe mode.  Whew - I wasn't looking forward to formatting it all and starting over again - I use some goofy hacks to run my Wacom tablet and Synaptic touchpad, and I wasn't looking forward to trying to remember how I got them to work. :p

---

