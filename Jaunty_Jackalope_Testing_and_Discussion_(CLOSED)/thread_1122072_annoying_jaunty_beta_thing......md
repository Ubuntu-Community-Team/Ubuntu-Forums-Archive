---
title: "annoying jaunty beta thing....."
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mokoma on 2009-04-10
when i go to update it tells me that it needs to do a partial upgrade, but when i click partial upgrade it disappears O,o

how can i fix this?

---

### Post by ibuclaw on 2009-04-10
Try opening a terminal
**Applications->Accessories->Terminal**

and run the following:
```
sudo apt-get update && sudo apt-get upgrade
```

Also, can you please post all Jaunty related questions in this forum ( Development & Programming -> Jaunty Jackalope Testing and Discussion) until the OS is officially released.

Regards
Iain

---

### Post by jmmL on 2009-04-10
It seems other people have also been having similar problems to you: [http://ubuntuforums.org/showthread.php?t=1122008](http://ubuntuforums.org/showthread.php?t=1122008)

If you wanted a more GUI way of updating, you could also look in the updates section of synaptic.

---

### Post by Mokoma on 2009-04-10
> **tinivole said:**
> Try opening a terminal
**Applications->Accessories->Terminal**

and run the following:
```
sudo apt-get update && sudo apt-get upgrade
```

Also, can you please post all Jaunty related questions in this forum ( Development & Programming -> Jaunty Jackalope Testing and Discussion) until the OS is officially released.

Regards
Iain

sorry dude this is quite well hidden from the main forums section. i will do in future though :)

---

### Post by Mokoma on 2009-04-10
> **jmmL said:**
> It seems other people have also been having similar problems to you: [http://ubuntuforums.org/showthread.php?t=1122008](http://ubuntuforums.org/showthread.php?t=1122008)

If you wanted a more GUI way of updating, you could also look in the updates section of synaptic.

ok thanks!

---

### Post by Mokoma on 2009-04-10
when i run update manager from cli this is the output from terminal

crash2k@crash2k-desktop:~$ sudo /usr/bin/update-manager
ERROR:root:not handled expection:
Traceback (most recent call last):

File "/usr/bin/update-manager", line 100, in <module>
controler.doPartialUpgrade()

File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 1595, in doPartialUpgrade
if not self.doDistUpgrade():

File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeController.py", line 972, in doDistUpgrade
self.quirks.run("StartUpgrade")

File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeQuirks.py", line 77, in run
for plugin in self.plugin_manager.get_plugins(condition):

File "/usr/lib/python2.6/dist-packages/computerjanitor/plugin.py", line 167, in get_plugins
filenames = self.get_plugin_files()

File "/usr/lib/python2.6/dist-packages/computerjanitor/plugin.py", line 120, in get_plugin_files
basenames = [x for x in os.listdir(dirname)

OSError: [Errno 2] No such file or directory: './plugins'

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook
none
crash2k@crash2k-desktop:~$

---

### Post by ibuclaw on 2009-04-10
This is not a problem that will be resolved through this forum.

What you can do is report a bug about it, but it is more than likely that the developers already know about this and have triaged it.

For information of how to report bugs, see here: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

As for now, as a workaround, you'll just have to stick with either **synaptic** or using **apt-get** in the terminal to upgrade your system until the issue is resolved upstream (you will have "update-manager" come through as an upgrade in apt).

Regards
Iain

---

### Post by bobnutfield on 2009-04-10
> **tinivole said:**
> This is not a problem that will be resolved through this forum.

What you can do is report a bug about it, but it is more than likely that the developers already know about this and have triaged it.

For information of how to report bugs, see here: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

As for now, as a workaround, you'll just have to stick with either **synaptic** or using **apt-get** in the terminal to upgrade your system until the issue is resolved upstream (you will have "update-manager" come through as an upgrade in apt).

Regards
Iain

Getting the same issue, but this is correct information...upgrading from the terminal works just fine, so this is just a GUI issue.  This is just one of quirky little things that can occur before a final release and I can assure you that it will be corrected in the final release.

---

