---
title: "Unable to use launchers after moving home folder"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by EverythingTech96 on 2011-07-27
Hello everybody,

I recently installed Ubuntu 11.04 on a Samsung RF511-A01. I decided it would be nice if I had the home folder on a separate, EXT4 partition. I followed [this guide]("http://www.go2linux.org/how-to-move-home-directory-to-another-partition") to do so.

After I had moved everything over as root, I proceeded to make the partition mount as /home when the system booted. Everything works great except that my Firefox "launcher" icon changed to the icon of (by the looks of it) a shell script. Whenever I try to run it, Ubuntu says:

[COLOR=Sienna]**Untrusted application launcher**

The application launcher "firefox.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.[/COLOR]
             
I have verified that it is executable and that the folder /home/<user> is owned by the user. I can run the launcher in the Applications menu and the one in the top bar (next to the menus), but not if it is in /home/<user> or any subfolders. It will work if I copy it into / though, so it is definitely something it doesn't like about the new location of the home folder. It does this with other applications as well, not just Firefox. Any help would greatly be appreciated!

Thanks in advance!

---

