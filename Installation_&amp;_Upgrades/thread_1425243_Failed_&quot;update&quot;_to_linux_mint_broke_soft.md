---
title: "Failed &quot;update&quot; to linux mint broke software sources"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by krippa on 2010-03-08
Hi,

When karmic was just out I wanted to try Linux Mint 8 Helena before it was released. So I followed a guide online how to update using debs from the linux mint page. Well.. I only came half-way before something broke and I cancelled the installation - I now also realize that I don't want Linux Mint.

So.. Everything works fine except software sources! I first thought it wasn't a big deal because I could just update the sources manually until Lucid - but trying to install wine repos was a no go since it uses the new format: ppa:xxxxxxxxx which only works using software sources and not directly in sources.list. Actually if someone could just tell me the karmic repo for wine I will probably be fine until Lucid since I imagine this might not be easy to fix:

```
sudo software-properties-gtk
```

Results in an exception:

```
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 110, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 87, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 536, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```

Please help me back to Karmic... "lsb_release -icdr" returns the following 

```
Distributor ID:	LinuxMint
Description:	Linux Mint 8 Helena - Main Edition
Release:	8
Codename:	helena

```

Ideas?

---

### Post by mikewhatever on 2010-03-08
Have you tried reinstalling software-properties-gtk package?

---

### Post by krippa on 2010-03-10
I had not, but purging it and reinstalling it did not fix this..

---

### Post by Dragonlaw on 2010-03-12
I had the same problem and took the solution from [http://forums.geteasypeasy.com/viewtopic.php?f=12&t=2424&view=previous]("http://forums.geteasypeasy.com/viewtopic.php?f=12&t=2424&view=previous")

I've modified the solution to fit your ubuntu version (presumably its Ubuntu 9.10)

**To summarise**
The problem was in the /etc/lsb_release file.
installing the mint file changed the way the distribution is identified form Ubuntu to Linux.

You can check if you are in the same situation by typing

lsb_release -a

in your terminal. If it is different from
Distributor ID: Ubuntu
Description: Ubuntu 9.04
Release: 9.04
Codename: jaunty

edit the /etc/lsb_release file (using gksudo gedit /etc/lsb-release) and put the following code in it

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10

save the file and now Software Sources should work fine.

---

### Post by krippa on 2010-03-12
That fixed it! Thanks a lot!

---

### Post by Dragonlaw on 2010-03-12
no worries. could you mark the thread as solved then?

---

