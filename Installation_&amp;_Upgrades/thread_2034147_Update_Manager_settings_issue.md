---
title: "Update Manager settings issue"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by AK44 on 2012-07-27
I am having an issue where if I click on the settings option in Update Manager the app simply reloads itself but never takes me to the settings menu. I have attempted (possibly incorrectly as I am very new to Ubuntu) to uninstall/reinstall the application with no change. Any ideas? On 12.04 if that matters. Thanks.

---

### Post by plucky on 2012-07-28
> **AK44 said:**
> I am having an issue where if I click on the settings option in Update Manager the app simply reloads itself but never takes me to the settings menu. I have attempted (possibly incorrectly as I am very new to Ubuntu) to uninstall/reinstall the application with no change. Any ideas? On 12.04 if that matters. Thanks.

From a terminal ```
software-properties-gtk
``` and post whatever it outputs.

---

### Post by AK44 on 2012-07-28
> **plucky said:**
> From a terminal ```
software-properties-gtk
``` and post whatever it outputs.

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 85, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 584, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 87, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

---

### Post by plucky on 2012-07-31
> ("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

Could you post the output from a terminal for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```

---

### Post by Dawnbandit on 2012-07-31
> **plucky said:**
> Could you post the output from a terminal for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```
Yea, because that sounds a little disconcerting, was it like this when you installed Ubuntu?

---

### Post by AK44 on 2012-07-31
> **plucky said:**
> Could you post the output from a terminal for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```

[http://pastebin.com/7RCrc2LJ](http://pastebin.com/7RCrc2LJ)

> **Dawnbandit said:**
> Yea, because that sounds a little disconcerting, was it like this when you installed Ubuntu?

No, I know for a fact it worked fine before I updated to 12.04 from 11.10. I am pretty sure it worked after the update as well but am not 100% confident there.

---

### Post by plucky on 2012-08-01
Those sources look ok as they all seem to be valid.I am not really sure what to do next to get **Software Sources** working again.

Do you have a **Software Sources** launcher in the DASH?

Does that work?

---

### Post by AK44 on 2012-08-07
Ok I fixed my problem with this link - [http://askubuntu.com/questions/126498/12-04-reports-itself-as-quantal-after-installing-the-toolchain-test-ppa](http://askubuntu.com/questions/126498/12-04-reports-itself-as-quantal-after-installing-the-toolchain-test-ppa)

---

