---
title: "Changing default locations for folders"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by MSXManiac on 2018-07-29
Because the original thread was closed and did not bring any objective response to users talking about using an NTFS partition and its problems and which is really highly inadvisable, it did not answer the original question.


However, there is a more drastic way of defining default paths for user directories by using any text editor in the file with the path as described below, remembering that username should be replaced with the name of the profile in use such as peter or carl:
home / username / .config / user-dirs.dirs


In the content of the file you should have content like:


# This file was written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you are
# interested in. All local changes will be retained at next run
# Format is XDG_xxx_DIR = "$ HOME / yyy", where yyy is a shell escape
# path relative to homedir, or XDG_xxx_DIR = "/ yyy", where / yyy is a
# absolute path. No other format is supported.
#
XDG_DESKTOP_DIR = "$ HOME / Desktop"
XDG_DOWNLOAD_DIR = "$ HOME / Downloads"
XDG_TEMPLATES_DIR = "$ HOME / Templates"
XDG_PUBLICSHARE_DIR = "$ HOME / Public"
XDG_DOCUMENTS_DIR = "$ HOME / Documents"
XDG_MUSIC_DIR = "$ HOME / Music"
XDG_PICTURES_DIR = "$ HOME / Pictures"
XDG_VIDEOS_DIR = "$ HOME / Videos"


Just change the name or full path of each folder and restart the session (not the system)

---

### Post by TheFu on 2018-07-30
Probably should be in the How-Tos subforum.
XDG is widespread, but not used by all Window managers that can be run on Linux, so this won't always work, but probably over 90% of the time it will. This is probably the best solution for users in a corporate environment.

Other methods can be used like using symbolic links.  I won't forget that a default config was modified somewhere in 2 yrs.

But all solutions are a matter of opinion. People should use whatever works for them.

---

