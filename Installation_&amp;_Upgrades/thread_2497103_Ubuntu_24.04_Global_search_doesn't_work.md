---
title: "Ubuntu 24.04: Global search doesn't work"
date: 2024-04-23
forum: Installation &amp; Upgrades
---

### Post by m-elodie on 2024-04-23
Hello!

I have upgraded to 24.04. I know I'm a bit early, but I noticed a possible bug.
I read that the new nautilus windows allow to search, either locally or globally.
I could verify that the local search work (i.e. in the current folder).
Example: click on the folder icon at the right of the search bar.
Enter a file you know exists on your disc, in this folder.
-> You will get all the occurrences of that file.

Now: leave the folder icon unselected
Enter the same file name. Logically it should find it. But it doesn't.
I thought it might be because there is much more global data, but for instance
I am searching for the same file as above right now. I started the search before
starting to write this post (maybe 1 ~ 2 min ago) and there is still no match.

NB: I don't know if Ubuntu does something or not, maybe it does, but I'm not sure
when I will get results. -> It would be nice to add a kind of marker, a little clock
spinning, or 3 dots ... constantly rewriting, just to tell the user something is under
process.

Thanks,

Elodie

---

### Post by daveandclaire75 on 2024-05-06
+1 for me.
Nautilus will search the current folder, but when I try Global search it just hangs and returns no results.

---

### Post by him610 on 2024-05-07
You might consider trying *catfish*
```
$ apt show catfish
Package: catfish
Version: 4.16.3-1
Priority: optional
Section: universe/utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Python Team <team+python@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,743 kB
Depends: gir1.2-gdkpixbuf-2.0, gir1.2-glib-2.0, gir1.2-gtk-3.0, gir1.2-pango-1.0, gir1.2-xfconf-0, python3-dbus, python3-gi-cairo, python3-pexpect, python3:any
Recommends: plocate | locate
Suggests: gir1.2-zeitgeist-2.0
Homepage: https://docs.xfce.org/apps/catfish/start
Task: xubuntu-desktop
Download-Size: 267 kB
APT-Manual-Installed: no
APT-Sources: http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: File searching tool which is configurable via the command line
 Catfish is a handy file searching tool for Linux and UNIX.
 The interface is intentionally lightweight and simple, using only Gtk+3.
 You can configure it to your needs by using several command line options.
 
```

---

### Post by TheFu on 2024-05-07
There are lots of search tools for Unix systems.

If you know part of the filename and only want to search on that, use locate.   This is a CLI tool.  I never remember the package name and it has changed names at least 4 times the last 20 yrs.  Looks like ....
```
$ apt search locate
...i   **plocate**                             - much faster locate
```
is the new name.  Install that and every day it will scan your file system for any new files.  If you don't want to wait until tomorrow, you can force a scan immediately with:
```
sudo updatedb
```

If you want a person Google-like search for nearly all files on your computer, there's **Recoll**.  It looks inside files for text to index. It does this using a bunch of helper-programs so audio, video, documents, PDFs, text, emails, and most other popular types of files can be indexed.  Because indexing is pretty heavy, by default it only runs on request, but you can setup a daily or weekly cron-job to update everything.  The indexes for recoll are much larger.  Recoll has a GUI and a command line interface.  I update the recoll DB daily before I get up in the morning. Happens automatically.  

I don't think Recoll integrates into any other desktop tools, but it will send any file found to the xdg-open command which should use the correct program to open the file.

There might be other desktop search tools. I've just never used them.  Recoll is pretty amazing and it is very, very, fast.

---

