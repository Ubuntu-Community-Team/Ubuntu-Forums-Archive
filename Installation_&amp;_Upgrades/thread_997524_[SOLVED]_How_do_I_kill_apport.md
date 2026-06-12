---
title: "[SOLVED] How do I kill apport?"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by sosaudio1 on 2008-11-29
It apparantly is stuck in a loop. I found a core dump and was wanting to look at it, first I went to gedit...but at 396M, it was taking a while. Then I went to open it in apport-gtk and that has produced this really nagging icon that says...."crash report detected" well that is cool and all but when I click the icon and put in my pw, I get the thinking cursor and the icon disappers, thinking cursor stops and the killer cool apport icon tells me there is a crash report click for details....what do I need to do to make this go away??????

---

### Post by sosaudio1 on 2008-11-29
This may have to do with my other issue with dpkg....but 

when I open /usr/share/apport/apport-gtk

This was what I got....PLEASE someone tell me what to do to get rid of the icon and I guess clear apport

$ /usr/share/apport/apport-gtk
dpkg-query: cannot scan updates directory `/var/lib/dpkg/updates/': No such file or directory
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 253, in <module>
    app = GTKUserInterface()
  File "/usr/share/apport/apport-gtk", line 34, in __init__
    apport.ui.UserInterface.__init__(self)
  File "/usr/lib/python2.5/site-packages/apport/ui.py", line 90, in __init__
    self.crashdb = get_crashdb(None)
  File "/usr/lib/python2.5/site-packages/apport/crashdb.py", line 450, in get_crashdb
    m = __import__('apport.crashdb_impl.' + db['impl'], globals(), locals(), ['CrashDatabase'])
  File "/usr/lib/python2.5/site-packages/apport/crashdb_impl/launchpad.py", line 22, in <module>
    Bug = Connector.ConnectBug()
  File "/usr/lib/python2.5/site-packages/launchpadbugs/connector.py", line 59, in __init__
    LaunchpadConnector.__init__(self, "Bug", method)
  File "/usr/lib/python2.5/site-packages/launchpadbugs/connector.py", line 44, in __init__
    self.connection = getattr(self.__mod_connection, __connections[__module]["connection"][1])()
  File "/usr/lib/python2.5/site-packages/launchpadbugs/http_connection.py", line 29, in __init__
    __version = "bughelper/%s (Python-urllib2/%s)" %(utils.find_version_number(),urllib2.__version__)
  File "/usr/lib/python2.5/site-packages/launchpadbugs/utils.py", line 24, in find_version_number
    return output.split()[1]
IndexError: list index out of range

---

### Post by sosaudio1 on 2008-11-29
any help would be awesome!!!!!!!!!

---

### Post by sosaudio1 on 2008-11-30
so in my midst of trying to fix my dpkg problem, I went to try to kill update manager thru system monitor and when I did, apport went away.....so I need to figure out what is up...looks like they are tied together but, I don't know how all this is tied together...

honestly, I'm at the point of trying to figure out if diving into the folders helps. I am not afraid of doing so. If someone can tell me what is the best way to basically reset restart dpkg I am cool with that...just let me know what to do...


Thanks for all the help it have been invaluable!!!!

Rich

---

### Post by sosaudio1 on 2008-11-30
sys borked reinstalled ubuntu

---

### Post by Inoki on 2013-03-25
I know this may be old, but since no one provided a solution I found one:

You need to open the task manager as root and then kill the apport service.

---

