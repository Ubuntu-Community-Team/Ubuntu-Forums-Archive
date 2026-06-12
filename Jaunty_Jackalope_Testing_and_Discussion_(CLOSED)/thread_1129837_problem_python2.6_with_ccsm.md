---
title: "problem python2.6 with ccsm"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-04-19
i think there is a problem with python 2.6 on jaunty (again). infact, i installed ccsm (from git) , it works fine but when i click for example on "gnome compatibility" button, i have this error:

Traceback (most recent call last):
File "/usr/local/lib/python2.6/dist-packages/ccm/Pages.py", line 1303, in ShowPlugin
pluginPage = PluginPage(plugin)
File "/usr/local/lib/python2.6/dist-packages/ccm/Pages.py", line 129, in __init__
groupPage = GroupPage(name, group)
File "/usr/local/lib/python2.6/dist-packages/ccm/Pages.py", line 1370, in __init__
sga = SubGroupArea('', group[''][1])
File "/usr/local/lib/python2.6/dist-packages/ccm/Settings.py", line 1466, in __init__
settings = sorted(GetSettings(subGroup), key=SettingKeyFunc)
File "/usr/local/lib/python2.6/dist-packages/ccm/Utils.py", line 400, in GetSettings
screen = group.Screen.itervalues()
AttributeError: 'compizconfig.SSGroup' object has no attribute 'Screen'


NOTE: there isn't this error on other distro for example suse with python 2.6

---

