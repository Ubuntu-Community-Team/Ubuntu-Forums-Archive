---
title: "Softwar index broken"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by vulpeso on 2006-10-20
When I ran the updater I got this error message:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I ran the command and then clicked on the update icon again and got the same error message.

When I ran it, this was displayed in the terminal:

 trying to overwrite `/usr/bin/mpeg3cat', which is also in package mpeg3-utils
Errors were encountered while processing:
 /var/cache/apt/archives/libmpeg3hv_1%3a2.0.0-1svn20060611.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What do I need to do to rectify the situation?

Many thanks,

vulpeso

---

### Post by Kateikyoushi on 2006-10-20
I would delete this file for a start, if it's an svn then pretty old anyway.
/var/cache/apt/archives/libmpeg3hv_1%3a2.0.0-1svn20060611.1_i386.deb

---

### Post by vulpeso on 2006-10-20
That didn't seem to clear the error. The weird thing is, I delete libmpeg3hv_1%3a2.0.0-1svn20060611.1_i386.deb and it no longer lists with ls in that dir. But I still get the original error and when I run apt-get install -f and after running it, the file reappears.

---

### Post by vulpeso on 2006-10-20
I right clicked on the updater icon and ran Package Manager. I filtered on Broken, discovered the package(s) and removed it/them. It was the video editing package (and/or it's library) Cinelerra that broke it.

---

