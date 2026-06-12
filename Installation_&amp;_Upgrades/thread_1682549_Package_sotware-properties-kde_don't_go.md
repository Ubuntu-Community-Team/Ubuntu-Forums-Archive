---
title: "Package sotware-properties-kde don't go"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by grizzo on 2011-02-06
Hi,
today I tried to add a repository with software-properties-kde on my Ubuntu 10.10 with KDE 4.6 but the software doesn't go.
This is the error in the terminal:
```
nicola@nicola-desktop:~$ sudo software-properties-kde
Traceback (most recent call last):
  File "/usr/bin/software-properties-kde", line 122, in <module>
    app = SoftwarePropertiesKDE(datadir=data_dir, options=options, file=file, attachWinID=attachWinID)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/kde/SoftwarePropertiesKDE.py", line 67, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```
So I looked on Google for searching a fix for this problem and I read this [bug]("https://bugs.launchpad.net/ubuntu/+source/python-qt4/+bug/407418") on launchpad, and there's written that the problem was fixed form Ubuntu 9.04.
So have you got any ideas for solving this problem?
Thanks :)

---

### Post by oldos2er on 2011-02-06
Make a backup copy of your current sources.list: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Open sources.list in a text editor and add the repository manually: ```
kdesu kate /etc/apt/sources.list
```

When you're done with the editor, run ```
sudo apt-get update
```

---

### Post by ankspo71 on 2011-02-06
Hi,
Do you already have Synaptic Package Manager or 'software-properties-gtk' installed? If you do, then you might be still be able to change your repositories using a gtk GUI. Or try opening software-properties-kde with gksudo in the terminal.

I myself am having a problem with Kpackagekit not working under kdesudo, but it works fine while running it with sudo. So if you tried sudo, try kdesudo (it's the recommended way to launch a graphical application in KDE anyways, but evidently there is a problem running kdesudo for some applications on my newly upgraded KDE4.6 desktop). 

My software-properties-kde works fine for me though. 
PS: I'm using KDE4.6 in Kubuntu 10.10 too.

---

