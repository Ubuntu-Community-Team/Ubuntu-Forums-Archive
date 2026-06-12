---
title: "Upgrade errors"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by PaulBx on 2014-04-21
I pushed the upgrade button. It might be a good thing to suggest people backup before letting the upgrade proceed.

I had some errors:

```

paul@len780:/var/log/dist-upgrade$ grep -i error apt-term.log
...
Gtk-WARNING **: Error loading theme icon 'window-close' for stock: Unrecognized image file format at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 148.
Gtk-WARNING **: Error loading theme icon 'go-previous' for stock: Unrecognized image file format at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 148.
Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unrecognized image file format at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 148.
...
AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.deliver in /etc/apparmor.d/usr.lib.dovecot.deliver at line 15: Could not open 'tunables/dovecot'
AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.imap in /etc/apparmor.d/usr.lib.dovecot.imap at line 14: Could not open 'tunables/dovecot'
...
Installation finished. No error reported.

```

I thought that last line was rather amusing.

Those first errors were like this:
```

GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 148.

```

Needless to say, seeing "your installation is broken" is not confidence-inspiring. That file, loaders.cache, does in fact exist. I tried the suggested command even though I'm not sure what good it would do, the upgrade being done, but it would not permit me even though I used "sudo".

The latter errors looked like this:
```
Warning from profile /usr/lib/chromium-browser/chromium-browser (/etc/apparmor.d/usr.bin.chromium-browser) ptrace rules not enforced
Warning from profile chromium_browser_sandbox (/etc/apparmor.d/usr.bin.chromium-browser) ptrace rules not enforced
AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.deliver in /etc/apparmor.d/usr.lib.dovecot.deliver at line 15: Could not open 'tunables/dovecot'
Found reference to variable pid, but is never declared

```

Not sure what that is about. I don't use chromium, and have uninstalled it. I did get an unasked-for copy of firefox and sylpheed with this upgrade (I use seamonkey). I can see getting them in a fresh install, but maybe the upgrade should not put them in.

---

### Post by grahammechanical on 2014-04-21
> [COLOR=#000000]It might be a good thing to suggest people backup before letting the upgrade proceed.[/COLOR]

We advise that all the time on this forum. We even advise waiting until the rush has died down before upgrading. We especially advise to do a fresh install. I advise reverting the desktop back to its default look and deactivating proprietary video drivers

As regards that pixbuf error message I got that the other day. I have been running Trusty Tahr since the beginning and I have seen that message more than once and once the installation was broken until I ran that instruction but other times, as with the other day, it was a false alarm.

The upgrade process expects a default install and upgrades the default applications.

> gdk-pixbuf-query-loaders collects information about loadable modules for Gdk Pixbuf and writes it to the default cache file location.

[http://www.linuxfromscratch.org/blfs/view/svn/x/gdk-pixbuf.html](http://www.linuxfromscratch.org/blfs/view/svn/x/gdk-pixbuf.html)

Regards.

---

### Post by monkeybrain20122 on 2014-04-21
Well it may be a even better idea to disable that button by default.
People should never be prompted to upgrade on impulse.

---

### Post by monkeybrain20122 on 2014-04-21
> **grahammechanical said:**
> We advise that all the time on this forum. We even advise waiting until the rush has died down before upgrading. We especially advise to do a fresh install. I advise reverting the desktop back to its default look and deactivating proprietary video drivers

As regards that pixbuf error message I got that the other day. I have been running Trusty Tahr since the beginning and I have seen that message more than once and once the installation was broken until I ran that instruction but other times, as with the other day, it was a false alarm.

The upgrade process expects a default install and upgrades the default applications.

Regards.

We do, but not  all Ubuntu users visit the forums and the popup will still urge them to upgrade. :) In fact there is not even a single mention of UF on the download page or the UF installation slide show.

---

### Post by PaulBx on 2014-04-21
Yes, that was my point. I'm sure there is lots of good advice here. Where it needs to be, is in the Software Updater application. Or at the least, a link to a sticky thread going over the suggested steps and the considerations. I don't know how many times I've seen people bork their system on a major upgrade without having first backed up.

---

