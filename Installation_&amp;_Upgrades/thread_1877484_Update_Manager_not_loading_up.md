---
title: "Update Manager not loading up"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by maravingian on 2011-11-08
Hi guys, 

I think I`ve made a small mistake and I`m unsure on how to step back Ubuntu to its previous settings.
I was trying to load shell extensions to change the theme on my computer. I downloaded and installed repository ppa: ricotz/testing.

Since install though I`m now unable to load up update manager therefore also unable to download new essential updates for my computer.

Is there any way I can step back Ubuntu or is there any way I can remove ppa:ricotz/testing. Tried the rm command in Terminal but it advised no file or directory.

---

### Post by BillyBoa on 2011-11-08
Did you try using the software sources? You can go directly there typing on 2software sources" on AltF2. If not you could try through Ubuntu Tweak.

---

### Post by pavi_elex on 2011-11-08
Did you change in /etc/apt file?
Use New-fresh apt directory.

---

### Post by maravingian on 2011-11-08
software sources and software centre will not load either. Unsure of the fresh-apt command.

---

### Post by drs305 on 2011-11-08
Try launching one of them in a terminal. That way you will see the error message and you may be informed of the problem.

```
gksu software-properties-gtk &
gksu update-manager
```

---

### Post by maravingian on 2011-11-16
So the first command, gksu software-properties-gtk & , returned: 

[1] 2735
smith@smith-desktop:~$   File "/usr/bin/software-properties-gtk", line 25, in <module>
    from gi.repository import Gtk
  File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
    dynamic_module._load()
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 224, in _load
    overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
  File "/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py", line 523, in <module>
    class FontSelectionDialog(Gtk.FontSelectionDialog, Dialog):
  File "/usr/lib/python2.7/dist-packages/gi/module.py", line 105, in __getattr__
    self.__name__, name))
AttributeError: 'gi.repository.Gtk' object has no attribute 'FontSelectionDialog

The second command, gksu update-manager , returned

[1]+  Exit 1                  gksu software-properties-gtk

If I`m reading this correctly, because software centre does not load correctly, update-manager fails to load also?

---

### Post by BillyBoa on 2011-11-16
First do a backup of your sources list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Then edit the list

```
sudo gedit /etc/apt/sources.list 
```

Now comment with hashes # in front of the 1 or 2 deb files of the repository ppa:ricotz/testing you added and created the problem.

Save, exit and

```
sudo apt-get update
```

---

### Post by drs305 on 2011-11-16
> **maravingian said:**
> So the first command, gksu software-properties-gtk & , returned: 

The second command, gksu update-manager , returned

[1]+  Exit 1                  gksu software-properties-gtk

If I`m reading this correctly, because software centre does not load correctly, update-manager fails to load also?

That's what it looks like. Are you able to install packages from the terminal?

One of the errors comes from the folders associated with python-gobject. You might try reinstalling that package:
```
sudo apt-get install --reinstall python-gobject
```

---

### Post by maravingian on 2011-11-17
saved source list then brought up gedit:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
# deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) karmic main # disabled on upgrade to karmic
##repo for open office3
# deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) karmic main # disabled on upgrade to karmic
# deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) karmic main # disabled on upgrade to karmic
##GeeXboX package repository
# deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main #Third party developers repository

I don`t want to mess this up so would the lines required have to do with updates-multiverse, security multiverse and updates restricted?

---

### Post by BillyBoa on 2011-11-18
In your case I would commenting with hashes the line

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main #Third party developers repository

It's for developers and maybe is causing you trouble with updates you don't need.

---

### Post by the-saint on 2011-11-18
Even to me the Update manager does not pops up when clicked but keeps showing 14updates available or so... I just right click and chose install updates...

---

### Post by maravingian on 2011-11-20
so....I tried commenting on the third party line as suggested but no luck at all.  read about a ppa purge tool, but when I tried to install that through Terminal Ubuntu was unable to find ppa purge. 

Software Centre, Update Manager, Software Sources, Advanced settings so far are all the apps that will not load for me.

---

### Post by MAFoElffen on 2011-11-20
> **maravingian said:**
> so....I tried commenting on the third party line as suggested but no luck at all.  read about a ppa purge tool, but when I tried to install that through Terminal Ubuntu was unable to find ppa purge. 

Software Centre, Update Manager, Software Sources, Advanced settings so far are all the apps that will not load for me.
You could do **ppa-purge** on what you added as a ppa or add comment characters in front of the lines in your sources.list... or delete them out.  

Couldn't one of you just copy your oneiric source.list and post is for him to copy over his.  I would, but I'm up on a Solaris 11 box right now... Then he wouldn't have to edit.

---

### Post by maravingian on 2011-11-24
Is there any way I can reinstall Ubuntu 11.10 from downloading it without losing my current settings, and regaining update manager?

---

### Post by drs305 on 2011-11-24
> **maravingian said:**
> Is there any way I can reinstall Ubuntu 11.10 from downloading it without losing my current settings, and regaining update manager?

You could copy your current /home/<username> to another partition and then during the installation choose to manually partition the drive. Select your new /home partition, make it the mount point for /home, and make sure NOT to tick the 'format' box. This will keep your user-defined settings, but it will not save any universal/root configurations you have made.

You can use these commands to copy your current home folder contents to another partition (XX would be the drive/partition, such as sd**a6**):

```
sudo mkdir /newhome   && sudo chown -R $USER:  /newhome  
sudo mount /dev/sd**[COLOR="DarkRed"]XX[/COLOR]** /newhome   # partition that will be new home 

sudo cp --preserve -r  /home/<username>  /newhome  	# copy username/  to  /mnt/newhome; ignore .gvfs permission denied error	
*or:*
sudo rsync -axS --exclude='/*/.gvfs'  /home/<username>  /newhome 

```

You can also export a list of installed apps, if you have already added some and want to import them into your new installation. Normally I'd recommend using the Synaptic "File, Saving Markings" option (and ticking the option in the lower left corner of the screen) but I think you can't use Synaptic currently.

It isn't as convenient, but you can export the list of installed apps via a terminal with the following commands:
```

sudo dpkg --get-selections | grep -v "deinstall” > /home/<username>/Desktop/installed-packages 
```


Copy installed-packages to your Desktop on new computer: 
```
	sudo apt-get update
	sudo dpkg --clear-selections
	sudo dpkg --set-selections /home/<username>/Desktop/installed-packages 	
	sudo apt-get dselect-upgrade
```

---

