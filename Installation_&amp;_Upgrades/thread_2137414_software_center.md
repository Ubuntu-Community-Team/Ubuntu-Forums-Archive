---
title: "software center"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by vlgngl on 2013-04-20
Hi friends, I'm new in ubuntu and &#305; had face to face a problem about ubuntu software center. 
When I were trying to open software center it seemed busy and not running. when &#305; tried from terminal "software-center" the results in below : 

~$ software-center
2013-04-20 21:40:11,781 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-04-20 21:40:11,788 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-04-20 21:40:12,677 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-04-20 21:40:12,686 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-04-20 21:40:12,685 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-04-20 21:40:12,848 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-04-20 21:40:13,213 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 257, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Malformed line 56 in source list /etc/apt/sources.list (dist parse)
2013-04-20 21:40:14,176 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
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
 anyone can help me ?

---

### Post by LArchimonde on 2013-04-20
Hello. About your problem try these ones: [FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace][FONT=verdana]sudo apt-get update -f then sudo apt-get update. Or just try Synaptic. Reinstall it with Synaptic and see if it works. To get Synaptic just type this in terminal: sudo apt-get install synaptic. That's it.[/FONT][/FONT]

---

### Post by vlgngl on 2013-04-20
Thanks for your contributions but it was not worked. I installed synaptic and tried again it but the result was same. 

 sudo apt-get update
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read

I dont understand the problem and I dont know what i should do

---

### Post by ibjsb4 on 2013-04-20
Please post the output of ..

```
cat -n /etc/apt/sources.list
```

and
```
~$ software-center
2013-04-20 21:40:11,781 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-04-20 21:40:11,788 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-04-20 21:40:12,677 - softwarecenter.backend.reviews - WARNING -  Could not get usefulness from server, no username in config file
2013-04-20 21:40:12,686 - softwarecenter.fixme - WARNING - logs to the  root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51,  'find_module')'
2013-04-20 21:40:12,685 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-04-20 21:40:12,848 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-04-20 21:40:13,213 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 257, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Malformed line 56 in source list /etc/apt/sources.list (dist parse)
2013-04-20 21:40:14,176 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
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
    self.view_manager.set_active_view(ViewPages.AVAILA  BLE)
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

[ATTACH=CONFIG]241584[/ATTACH]

---

### Post by vlgngl on 2013-04-20
hello again,

~$ sed -n 56p /etc/apt/sources.list
deb [http://archive.canonical.com/](http://archive.canonical.com/) quantalpartner     , this is the source.list result. the ubuntu software center is opening as busy but after a few seconds later it is being turned off

---

### Post by ibjsb4 on 2013-04-21
Double post are not appreciated, good bye

[http://ubuntuforums.org/showthread.php?t=2137424](http://ubuntuforums.org/showthread.php?t=2137424)

---

