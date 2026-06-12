---
title: "Apt-get software sources.list issue"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by elang on 2012-07-12
I use Ubuntu 12.04 Desktop 32-bit
whenever i try to run sudo apt-get <anything except purge>, i get the following error:
E: Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.


I tried replacing the sources.list with the default, from my friend's newly installed Ubuntu 12.04, but i still got the same error.

This is my sources.list file:
    ```

&#65279;## deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution
deb http://in.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://in.archive.ubuntu.com/ubuntu/ precise universe
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

##ADDED BY ELAN: for GATE
deb http://cz.archive.ubuntu.com/ubuntu hardy-updates main universe
 
```Software center closed immediately whenever I opened it , so i opened it from terminal and got this:
```

2012-07-12 11:07:43,901 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-07-12 11:07:43,905 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-07-12 11:07:44,171 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-07-12 11:07:44,306 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-07-12 11:07:44,341 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-07-12 11:07:44,351 - softwarecenter.backend.spawn_helper - WARNING - exit code 1 from helper for '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'review_stats', '{"days": 14}']'
2012-07-12 11:07:44,352 - softwarecenter.backend.spawn_helper - WARNING - got error from helper: 'WARNING:__main__:connecting to http://reviews.ubuntu.com/reviews/api/1.0: 
'
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.
2012-07-12 11:07:45,162 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1420, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1350, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 168, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 237, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 504, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 270, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 443, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 432, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'


```

---

### Post by dino99 on 2012-07-12
open a terminal & run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

and remove (or comment out, by adding # in front of the line) the latest sources.list line:

( you only want/need "precise", surely not "hardy" )

##ADDED BY ELAN: for GATE
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) hardy-updates main universe

and use the main server:

instead of:   [http://in.archive](http://in.archive) .....
replace by:  [http://archive](http://archive) ....       for all the related lines

then update again

---

### Post by elang on 2012-07-13
Thanks for pointing out the hardy-precise mixup. I have commented it out.

Unfortunately, the problem still persists. I tried using a new sources.list from [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) too, but end up with the same result.

Now, I ran the three commands you gave me:

[LIST=1]
[*]sudo apt-get clean
[LIST]
[*]this ran without any results i.e. there was no information displayed, the next line came with the cursor
[/LIST]
 
[*]sudo apt-get autoclean
[LIST]
[*]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.

```
[/LIST]
 
[*]sudo apt-get autoremove
[LIST]
[*]```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kde-l10n-de kde-l10n-engb kde-l10n-zhcn language-pack-de
  language-pack-de-base language-pack-kde-de
  language-pack-kde-de-base language-pack-kde-en
  language-pack-kde-en-base language-pack-kde-zh-hans
  language-pack-kde-zh-hans-base language-pack-zh-hans
  language-pack-zh-hans-base
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
After this operation, 96.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 235627 files and directories currently installed.)
Removing kde-l10n-de ...
Removing kde-l10n-engb ...
Removing kde-l10n-zhcn ...
Removing language-pack-kde-zh-hans-base ...
Removing language-pack-zh-hans-base ...
Removing language-pack-kde-de-base ...
Removing language-pack-kde-de ...
Removing language-pack-de-base ...
Removing language-pack-kde-en-base ...
Removing language-pack-kde-zh-hans ...
Removing language-pack-zh-hans ...
Removing language-pack-de ...
Removing language-pack-kde-en ...
Processing triggers for man-db ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
E: Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.


```
[/LIST]
 
[*]sudo apt-get update gave me the **_same old_** error:
```

E: Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.

```
[/LIST]

---

### Post by plucky on 2012-07-13
Post the output from a terminal for ```
cat /etc/apt/sources.list.d/*.list
```

---

### Post by elang on 2012-07-16
Upon running cat /etc/apt/sources.list.d/*.list     :
```

# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)
deb http://archive.canonical.com/ubuntu precise partner #Added by software-center

```

---

### Post by plucky on 2012-07-16
That looks ok.

Try renaming your sources.list file by running ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
``` and then run ```
sudo apt-get update
``` and see if you get the same error.

Without a sources.list file,the error should go away unless there is another file that it is finding in that directory.

Good luck

---

