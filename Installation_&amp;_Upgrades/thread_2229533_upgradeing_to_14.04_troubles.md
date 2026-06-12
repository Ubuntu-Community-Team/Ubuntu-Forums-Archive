---
title: "upgradeing to 14.04 troubles"
date: 2014-06-13
forum: Installation &amp; Upgrades
---

### Post by ulao2 on 2014-06-13
I have done an update and upgrade on my current version of 12.10. At this point it reports there is nothing to upgrade. If I try a do-release-update and then  do-release-upgrade I get no release found. I read mixed reviews about development mode ( -d ) I tried it anyways and I get that stupid message about x to terminate and r to resurrect. Neither option helps...

Reading the net many say its possible to upgrade and other source say its not. Also I read that a CD install does not allow upgrades? I have set up so many configs that I really dont want to do a fresh install. Is there no way to upgrade?

---

### Post by Bucky Ball on 2014-06-13
Don't think there would be now. If you open update manager, is there a message to tell you there is a new release available?

12.10 has been out of support since April so don't like your chances, but I could be wrong. Just that you would need to upgrade to 13.04 and that is not supported anymore either. I stick with the LTS (long term support) releases myself. Upgrading from where you are would be a nightmare if you are intending to get to 14.04 LTS. You would need to go 12.10>13.04>13.10>14.04 LTS. Yuk. That could get problematic. 

12.10 is reporting there is nothing to update/upgrade as the repositories would now be closed. 'do-release-update/upgrade' is not working because, as I say, 13.04 is your next port of call and that's EOL also.

---

### Post by ulao2 on 2014-06-13
I really dont mind what I upgrade to, I just need greater than 12. I guess I got some really bad advice when a friend of mine said dot upgrade unless you need to. 

 update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 26, in <module>
    from gi.repository import Gtk
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py", line 1533, in <module>
    raise RuntimeError("Gtk couldn't be initialized")
RuntimeError: Gtk couldn't be initialized
root@spawnlinux:~#

---

### Post by Bucky Ball on 2014-06-13
In that case, back up your valuable data and do a clean install of 14.04 LTS. Don't know that you've got a lot of choice.

---

### Post by ulao2 on 2014-06-13
Yeah gui says no release available.

---

