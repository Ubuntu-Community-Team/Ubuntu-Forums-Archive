---
title: "newbie doesn't know...'ubuntu-minimal' has no candidateOrigin"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by pilot4fun on 2010-10-26
Trying to upgrade from Ubuntu 10.04 to 10.10.  Using the Update Manager ('cause what else would a newbie be doing??)  All 10.04 updates installed but when I ask for 10.10 upgrade, it falls over
 :( 

Looked at /var/log/dist-upgrade/xxxx and found:

2010-10-26 19:30:43,942 DEBUG updateSourcesList()
2010-10-26 19:30:43,985 DEBUG rewriteSourcesList()
2010-10-26 19:30:43,986 DEBUG BaseMetaPkg 'ubuntu-minimal' has no candidateOrigin
2010-10-26 19:30:44,014 ERROR not handled expection:
Traceback (most recent call last):

  File "/tmp/tmpS171XA/maverick", line 7, in <module>
    sys.exit(main())

  File "/tmp/tmpS171XA/DistUpgradeMain.py", line 158, in main
    if app.run():

  File "/tmp/tmpS171XA/DistUpgradeController.py", line 1616, in run
    return self.fullUpgrade()

  File "/tmp/tmpS171XA/DistUpgradeController.py", line 1534, in fullUpgrade
    if not self.updateSourcesList():

  File "/tmp/tmpS171XA/DistUpgradeController.py", line 664, in updateSourcesList
    if not self.rewriteSourcesList(mirror_check=True):

  File "/tmp/tmpS171XA/DistUpgradeController.py", line 486, in rewriteSourcesList
    distro.get_sources(self.sources)

  File "/tmp/tmpS171XA/distro.py", line 103, in get_sources
    source.template.official == True and

AttributeError: 'Template' object has no attribute 'official'

2010-10-26 19:30:44,014 DEBUG running apport_crash()
2010-10-26 19:30:45,132 DEBUG enabling apt cron job

any suggestions?

Thanks!

---

### Post by meanderingthoughts2 on 2010-11-05
I'm a newbie here to who ran into the same problem. I figured my way out of it and I can give you the "how-to", but not the "why?". 

system>administration.>software sources
Under "Ubunutu Software" tab, check the box: Cannocial-supported Open Source software (main)

A popup should come up telling you may need to reinstall software, but if you have recently done an update (which you probably had when trying to first upgrade), then never mind this message.

Go to system>admin>update manager and try to upgrade again. 

If this doesn't work go back to to Software Sources and also check the box: Community-maintained Open Source software (I can't remember if I checked this or not, that is why I'm suggesting try this if the upgrade doesn't work)

Hope this helps!

-meanderingthoughts2

---

