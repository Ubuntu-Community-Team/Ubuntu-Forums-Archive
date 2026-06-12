---
title: "error in karomic kaola with the update manager crashing"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by steve101101 on 2009-09-01
when running the update manager i get this:

```

steven@steven-laptop:~$ gksudo update-manager 
/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:34: RuntimeWarning: missing handler 'on_expander_details_activate'
  self.builder.connect_signals(self)
WARNING: can not get name for '<atk.NoOpObject object at 0x99190f4 (AtkNoOpObject at 0x9b70790)>'
WARNING: can not get name for '<atk.NoOpObject object at 0x99191bc (AtkNoOpObject at 0x9b70ca0)>'
WARNING: can not get name for '<atk.NoOpObject object at 0x9919a54 (AtkNoOpObject at 0x9b7f000)>'
/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeCache.py:120: DeprecationWarning: Accessed deprecated property Package.candidateDownloadable, please see the Version class for alternatives.
  if (not pkg.candidateDownloadable and
/usr/lib/python2.6/dist-packages/UpdateManager/Core/UpdateList.py:82: DeprecationWarning: Accessed deprecated property Package.candidateOrigin, please see the Version class for alternatives.
  if pkg.candidateOrigin == None:
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:743: DeprecationWarning: Accessed deprecated property Package.summary, please see the Version class for alternatives.
  summary = xml.sax.saxutils.escape(pkg.summary)
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:746: DeprecationWarning: Accessed deprecated property Package.packageSize, please see the Version class for alternatives.
  size = _("(Size: %s)") % humanize_size(pkg.packageSize)
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:747: DeprecationWarning: Accessed deprecated property Package.installedVersion, please see the Version class for alternatives.
  if pkg.installedVersion != None:
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:749: DeprecationWarning: Accessed deprecated property Package.installedVersion, please see the Version class for alternatives.
  {"old_version" : pkg.installedVersion,
/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py:750: DeprecationWarning: Accessed deprecated property Package.candidateVersion, please see the Version class for alternatives.
  "new_version" : pkg.candidateVersion}
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 98, in <module>
    view = DistUpgradeViewGtk(data_dir)
  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeViewGtk.py", line 361, in __init__
    SimpleGtkbuilderApp.__init__(self, gladedir+"/DistUpgrade.ui")
  File "/usr/lib/python2.6/dist-packages/DistUpgrade/SimpleGtkbuilderApp.py", line 33, in __init__
    self.builder.add_from_file(path)
glib.GError: Duplicate object id 'vbox2' on line 409 (previously on line 311)

```

---

### Post by Paqman on 2009-09-01
First of all, if you're a beginner, you should be running Karmic. It's not finished yet, so you _will_ get bugs and stuff that doesn't work.

Secondly, Karmic has it's own section of the forum, [here]("http://ubuntuforums.org/forumdisplay.php?f=359").

Thirdly, can you update without using update-manager? Try using Synaptic or the command line (sudo apt-get update && sudo apt-get upgrade). If you strike a bug in the testing branch it's always a good idea to make sure you're using the most recent packages. Launchpad won't even accept automated bug reports if your packages are out of date.

---

### Post by overdrank on 2009-09-01
Moved to Karmic Koala Testing and Discussion

---

### Post by steve101101 on 2009-09-01
im not a beginner. usually i can figure out my issues but this one stumps me.

---

### Post by kleeman on 2009-09-01
I had an issue like this today and when I upgraded using

sudo apt-get update
sudo apt-get install update-manager

in a terminal. The problem was fixed.

---

### Post by orlox on 2009-09-01
> **kleeman said:**
> I had an issue like this today and when I upgraded using

sudo apt-get update
sudo apt-get install update-manager

in a terminal. The problem was fixed.

I had the same issue, and I used this same solution. Just when I had this problem, there was already an update that fixed it.

---

### Post by steve101101 on 2009-09-01
i have tried doing that and reinstalling it but it doesn't help it. plz help

---

### Post by orlox on 2009-09-01
Well, did you tried a complete system update??

Now that I look at the solution provided, I actually did a complete update instead of just updating update-manager to solve it...

---

### Post by seaq on 2009-09-01
seems to be bug 422665

[https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/422665](https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/422665)

---

### Post by steve101101 on 2009-09-02
this worked

Changing the id in line 409 of /usr/share/update-manager/glade/DistUpgrade.ui to something like "vbox0" fixes the problem.

---

