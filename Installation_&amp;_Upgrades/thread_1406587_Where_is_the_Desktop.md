---
title: "Where is the Desktop?"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by giammy on 2010-02-14
Hi all,

I need to build an instalaltion script for my project [http://www.cloudusb.net](http://www.cloudusb.net)
where I need to access to the Desktop.

The folder in the English installation is $HOME/Desktop, but it varies in installation
in other languages ($HOME/Scrivania in Italian for example).

Is there a way to get the correct directory name?
Something like an environment variable $DESKTOP pointing to the name of
the Desktop in the current installation?

thaks
Giammy

---

### Post by Barriehie on 2010-02-14
How about $HOME/Desktop ???

---

### Post by efflandt on 2010-02-14
Barriehie apparently missed the part about Desktop not being "Desktop" in other languages.

The **env** command tells you what is in your environment.  But I do not see anything related to desktop (other than part of my computer hostname).

But how about **~/.config/user-dirs.dirs** (don't forget dot prefix on .config)

---

### Post by giammy on 2010-02-14
> **efflandt said:**
> 
But how about **~/.config/user-dirs.dirs** (don't forget dot prefix on .config)

thank you for the suggestion: you are right - this is the solution to get the localized Desktop directory!

test -f ${XDG_CONFIG_HOME:-~/.config}/user-dirs.dirs && source ${XDG_CONFIG_HOME:-~/.config}/user-dirs.dirs
echo ${XDG_DESKTOP_DIR:-$HOME/Desktop}

bye
giammy

---

