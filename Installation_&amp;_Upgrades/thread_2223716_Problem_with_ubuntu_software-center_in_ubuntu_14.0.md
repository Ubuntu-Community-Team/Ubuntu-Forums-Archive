---
title: "Problem with ubuntu software-center in ubuntu 14.04"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by Sascha_Behnsen on 2014-05-12
Hi Everybody,

i ve installed the newest version of ubuntu in the last week and i have a lttle problem with the ubuntu software center. When I start the software center, nothing happens.

When I reinstall the ubuntu software center from the terminal, I get the following issue.

 Updating software catalog...this may take a moment.
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 176, in <module>
    pathname, appinfo_dir=options.app_install_desktop_dir)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 1147, in rebuild_database
    cache = get_pkg_info()
  File "/usr/share/software-center/softwarecenter/db/pkginfo.py", line 245, in get_pkg_info
    from softwarecenter.db.pkginfo_impl.aptcache import AptCache
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 30, in <module>
    from aptdaemon.client import AptClient
  File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 48, in <module>
    from . import enums
  File "/usr/lib/python2.7/dist-packages/aptdaemon/enums.py", line 337, in <module>
    ROLE_INSTALL_FILE: _("Installed file"),
  File "/usr/lib/python2.7/dist-packages/aptdaemon/enums.py", line 72, in _
    return gettext.dgettext("aptdaemon", msg)
  File "/usr/lib/python2.7/gettext.py", line 545, in dgettext
    codeset=_localecodesets.get(domain))
  File "/usr/lib/python2.7/gettext.py", line 493, in translation
    t = _translations.setdefault(key, class_(fp))
  File "/usr/lib/python2.7/gettext.py", line 180, in __init__
    self._parse(fp)
  File "/usr/lib/python2.7/gettext.py", line 337, in _parse
    tmsg = unicode(tmsg, self._charset)
LookupError: unknown encoding: UTF-8



I have nothing found by google to fix this issue.
Is there anybody who has a idea?

Thanks for youre comments.

---

### Post by ibjsb4 on 2014-05-12
Try a different package manager, see if it will work.
```
sudo apt-get install synaptic
```
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by Sascha_Behnsen on 2014-05-13
sorry, but I get the same issue :-(

---

### Post by ibjsb4 on 2014-05-13
Open synaptic in terminal.

```
gksudo synaptic
```

Get any errors?

---

### Post by Sascha_Behnsen on 2014-05-18
yes, I get the following issue on the terminal: 

> 
(gksudo:10844): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed
    if not indexer.setupIndexing(force=opts.force, system=opts.pkgfile is None):
  File "/usr/lib/python2.7/dist-packages/axi/indexer.py", line 518, in setupIndexing
    addon.obj.init(dict(values=self.values), self.progress)
  File "/usr/share/apt-xapian-index/plugins/app-install.py", line 147, in init
    entry = DesktopEntry(os.path.join(APPINSTALLDIR, f))
  File "/usr/lib/python2.7/dist-packages/xdg/DesktopEntry.py", line 33, in __init__
    self.parse(filename)
  File "/usr/lib/python2.7/dist-packages/xdg/DesktopEntry.py", line 42, in parse
    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.7/dist-packages/xdg/IniFile.py", line 53, in parse
    fd = io.open(filename, 'r', encoding='utf-8', errors='replace')
LookupError: unknown encoding: utf-8




but, the software center is open!

---

### Post by ibjsb4 on 2014-05-18
Please post the output of

```
[COLOR=#000000][FONT=Ubuntu Mono]echo "$XDG_CURRENT_DESKTOP"[/FONT][/COLOR]
```

And look for errors

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Sascha_Behnsen on 2014-05-24
Result of "[COLOR=#000000][FONT=Ubuntu Mono]echo "$XDG_CURRENT_DESKTOP""

[/FONT][/COLOR]**Unity**[COLOR=#000000][FONT=Ubuntu Mono]

when I update oder upgrade, no errors shown[/FONT][/COLOR]

---

### Post by ibjsb4 on 2014-05-25
> **Sascha_Behnsen said:**
> yes, I get the following issue on the terminal: 
but, the software center is open!

The software center works?

---

