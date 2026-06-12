---
title: "A problem occurred when I open the software center"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by rooney09 on 2012-12-25
Hello!
I am entirely new to this forum and Ubuntu as OS.
A few days after using my new OS one problem has come up with the Ubuntu Software Center.
Somehow after its open it gets automatically closed. After I spent hours of searching a positive decision to find out what the problem is, I am still stuck on this problem.
So let me spend you some posts by giving you perhaps the right information about my problem.

1. When I type ```
sudo apt-get update && sudo apt-get upgrade
``` into the Terminal I get this:
```
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```

2. When I type > gksudo software-center, I get the following:

```
2012-12-25 20:37:25,992 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-12-25 20:37:26,974 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-12-25 20:37:26,983 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2012-12-25 20:37:26,983 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2012-12-25 20:37:27,145 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-12-25 20:37:27,532 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 257, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Malformed line 60 in source list /etc/apt/sources.list (dist parse)
2012-12-25 20:37:28,595 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 182, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1387, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1325, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 151, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 173, in init_view
    self.cache, self.db, self.icons, self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 80, in __init__
    self.build()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 324, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 119, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 253, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 238, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 131, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 330, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 225, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
```

3. When I type this: ```
cat /etc/apt/sources.list
```, the following text displays in the terminal:

```
# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://bg.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://bg.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://bg.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://bg.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://bg.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://bg.archive.ubuntu.com/ubuntu/ quantal universe
deb http://bg.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://bg.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://bg.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://bg.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://bg.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://bg.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://bg.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://bg.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb http://archive.canoncical/ quantal partner
deb-src http://archive.canoncical/ quantal partner
deb http://archive.canonical.com/ quantal partner
deb-src http://archive.canonical.com/ quantal partner
deb http://archive.canonical.com/ partner
deb-src http://archive.canonical.com/ partner
deb-src http://extras.ubuntu.com/ubuntu quantal main
```

Any help will be greatly appreciated!

---

### Post by Old_Grey_Wolf on 2012-12-25
Edit the sources.list and put a # in front of these lines

```
deb http://archive.canoncical/ quantal partner
deb-src http://archive.canoncical/ quantal partner
deb http://archive.canonical.com/ quantal partner
deb-src http://archive.canonical.com/ quantal partner
deb http://archive.canonical.com/ partner
deb-src http://archive.canonical.com/ partner
```

They type ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rooney09 on 2012-12-25
> **Old_Grey_Wolf said:**
> Edit the sources.list and put a # in front of these lines

```
deb http://archive.canoncical/ quantal partner
deb-src http://archive.canoncical/ quantal partner
deb http://archive.canonical.com/ quantal partner
deb-src http://archive.canonical.com/ quantal partner
deb http://archive.canonical.com/ partner
deb-src http://archive.canonical.com/ partner
```

They type ```
sudo apt-get update && sudo apt-get upgrade
```

Thank you so much @Old_Grey_Wolf!
It has just worked brilliantly :D

---

