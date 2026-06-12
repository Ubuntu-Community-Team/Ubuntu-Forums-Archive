---
title: "upgrade to edgy from dapper - after grub screen get cursor"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by pulper on 2006-11-03
hi - i see a lot of problems here in my searches for edgy upgrade, but i have a different one (i think). 

errors after doing the upgrade (done using gksu "update-manager -c").  something about "wget to car" but unfortunately i didn't write them down.  after trying to fix by doing update manager, it wouldn't accept my root password.  so, i restarted.

surprised when i received grub screen (thought it wouldn't get that far).  tried to go to ubuntu.  after saying ok to mounting root filesystem, it goes to a blank screen with a cursor.  tried many other times and same thing.

1.  can i simply do an upgrade from the live edgy cd now?  i don't think it offers that option (only a full install) but i thought i'd ask.

2.  any other options?  

if you don't know anyting for #2 but can answer #1, i certainly would appreciate it.  Thanks.

---

### Post by pulper on 2006-11-03
I found a partial answer here:

[https://launchpad.net/distros/ubuntu/+source/uim/+bug/63431](https://launchpad.net/distros/ubuntu/+source/uim/+bug/63431)

it talks about editing the /var/lib/dpkg/info/uim-common.prerm file.  however, how do i edit that if i cannot even get into ubuntu either using the regular means or the recovery?  should i just use the live cd and then edit?

---

### Post by philippe_carlo on 2006-11-03
That's screwed up. This is why I backup my partition images to usb disk (with partimage) prior to updating.

---

### Post by pulper on 2006-11-03
thanks for your reply.  did you do that from the live cd?  if not, how did you get it to work when the booting doesn't work?

---

### Post by CarpKing on 2006-11-03
What happens if you select "recovery mode" from grub?  That should take you into a text-only root session.  If that doesn't work, you could probably edit said file from a live CD, provided you mount the hard disk read/write.

---

### Post by pulper on 2006-11-03
i have booted from the live cd, mounted the hd, chroot, and then did sudo apt-get -f install (after update).  here is the response i get:

```
root@ubuntu:/# sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libatk1-ruby libgdk-pixbuf2-ruby libglade2-ruby libglib2-ruby libgtk2-ruby
  libgtkhtml2-ruby libgtksourceview1-ruby libpango1-ruby uim-common
Suggested packages:
  libgnome2-ruby uim-gtk2.0 uim-xim
The following packages will be upgraded:
  libatk1-ruby libgdk-pixbuf2-ruby libglade2-ruby libglib2-ruby libgtk2-ruby
  libgtkhtml2-ruby libgtksourceview1-ruby libpango1-ruby uim-common
9 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.
1124 not fully installed or removed.
Need to get 0B/1813kB of archives.
After unpacking 520kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 263410 files and directories currently installed.)
Preparing to replace uim-common 1:1.0.0-1ubuntu1 (using .../uim-common_1%3a1.2.1-3ubuntu2_all.deb) ...
ERROR: unbound variable (errobj is-set-ugid?)

*backtrace*
>>(is-set-ugid?)
>>(if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ()))))
>>(define uim-plugin-lib-load-path (if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ())))))
>>(require "plugin.scm")
>>(require "init.scm")
>>(*catch (quote errobj) (require "init.scm"))
>>(eq? (quote *init.scm-loaded*) (*catch (quote errobj) (require "init.scm")))

ERROR: unbound variable (errobj custom-reload-customs)

ERROR: unbound variable (errobj custom-choice-rec-sym)

ERROR: unbound variable (errobj plugin-alist)

ERROR: wta to car (errobj t)

```

does anyone have any idea?  thanks!

---

### Post by pulper on 2006-11-06
instead of fooling around with what no one seems to have an answer for, i just installed Edgy from scratch.  probably faster that way.  as mentioned in the faq's, backup before doing an update over the internet.

---

