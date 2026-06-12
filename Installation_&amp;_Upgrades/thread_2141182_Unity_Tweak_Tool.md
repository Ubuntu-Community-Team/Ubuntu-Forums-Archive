---
title: "Unity Tweak Tool"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by kelvinator on 2013-05-01
I am running Ubuntu 13.04. The Unity Tweak Tool bombs with this error. How can I fix it? 


Traceback (most recent call last):
  File "/usr/bin/unity-tweak-tool", line 72, in <module>
    UnityTweakTool.Application()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 88, in __init__
    self.run(pageid)
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 97, in run
    self.connectpages()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/__init__.py", line 110, in connectpages
    from UnityTweakTool.section.unity import Unity
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/unity.py", line 804, in <module>
    Unity.add_page(LauncherIcons)
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/skeletonpage.py", line 48, in add_page
    page.refresh()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/section/skeletonpage.py", line 69, in refresh
    element.refresh()
  File "/usr/lib/python3/dist-packages/UnityTweakTool/elements/switch.py", line 78, in refresh
    type  =self.type
KeyError: 3
kelvin@Ambition:~$

---

### Post by fantab on 2013-05-02
I don't think that it is supported for 13.04, however I am not sure. Uninstall it and use [Ubuntu Tweak]("https://launchpad.net/~tualatrix/+archive/ppa") instead.

Just run the following from Terminal to install ubuntu-tweak:


```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

I don't use either. dconf-editor and CCSM do everything I need.

---

### Post by dandroid13 on 2013-05-02
Both are, but Unity Tweak Tool is in the repos, so it's easier.

---

