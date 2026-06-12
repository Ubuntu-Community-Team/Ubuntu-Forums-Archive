---
title: "How to install kubuntu after installed ubuntu"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by fs_tigre on 2008-10-12
Hi,

first of all I'm new to linux and i'm currently trying linux ubuntu and yes, I already have a question.

Is it possible to install kubuntu if I have already installed ubuntu?

If yes, do I have to make a new istallation and a new partition or how can I do this?

Can someone explain this please?

Thanks,
fs_tigre

---

### Post by SuperSonic4 on 2008-10-12
```
sudo aptitude install kubuntu-desktop
```

^ Puts the kde desktop along the gnome one

[http://www.kubuntu.org/](http://www.kubuntu.org/) - Or burn the iso from the link here to a cd and install like you would have ubuntu

---

### Post by northrup on 2008-10-12
There are multiple ways to do this. Note that I haven't done any of these; I'm pretty new to Ubuntu and Linux in general so if something doesn't work quite right, I probably can't really help you much.
 
Option 1: Install using apt-get
 
Supposedly, you can use apt-get (an application in the terminal) to install the kubuntu-desktop package, like so:
 
```

sudo apt-get install kubuntu-desktop

```
 
This will install KDE on your Ubuntu system. Likewise, the same can be done if you have a different Ubuntu (Xubuntu, Fluxbuntu, etc.) by replacing "kubuntu" in "kubuntu-desktop" with the distribution whose desktop you are trying to get (might not work with Fluxbuntu...). So, if you wanted to install Xfce (to get an Xubuntu desktop):
 
```

sudo apt-get install xubuntu-desktop

```
 
Or, install GNOME (the normal Ubuntu desktop) on a Kubuntu/Xubuntu/Fluxbuntu/whatever computer:
 
```

sudo apt-get install ubuntu-desktop

```
 
You should be able to do the same using Synaptic Package Manager (the GUI frontend to the apt-get command) by selecting kubuntu-desktop or whichever you're installing and clicking on the install button. This is great if you don't want to burn a Kubuntu CD, but this requires an internet connection.
 
Option 2: Install the package via the Kubuntu Install CD
 
Just insert the Kubuntu CD (either the Live CD or the Alternate Install, doesn't matter) and open Synaptic. You should be able to use the Kubuntu CD as a repository. Select and install the kubuntu-desktop package from the CD. This procedure is ideal for computers without an internet connection (like my Ubuntu computer). I believe the automatic update feature may automatically do this for you, but I haven't tried it myself...
 
Alternately, just insert the CD, access the CD drive with a file manager, and browse to wherever the .deb files are. I can't recall the exact folder names, but it shouldn't be too hard to find. All the packages are organized alphabetically into folders. So, go to the folder that corresponds with the letter "K" and double-click on kubuntu-desktop.deb. Synaptic should automatically start up and install KDE.
 
When installing KDE, make sure you take care of all its dependencies (the other packages it needs prior to installing the main package). Most, if not all, should already be present. If not, Synaptic and/or apt-get should tell you which ones are missing.
 
Since I have not done this before, I don't know any details on whether you can switch between GNOME and KDE freely, any options you have to configure for KDE, etc. I believe selection of which desktop to use is done at login in the "Session" menu, but I can't confirm.
 
Good luck!
 
-Northrup

---

### Post by fs_tigre on 2008-10-13
First of all thank you for the quick response to both. If I enter this code (insudo aptitude install kubuntu-desktop) will this create a new installation in a separated partition?

The reason I’m asking this is because I have all versions of the ubuntu system, and if this is basically a new installation, wouldn’t be better for me to use the DVD to perform this new installation?

Thanks
Fs_tigre

---

### Post by zorniki on 2008-10-13
As I´m having the same question, I´m assuming that executing the command "sudo apt-get install kubuntu-desktop" just downloads the KDE package and uses it as the current desktop version.

Does that mean I have to reinstall the GNOME version if I wanted to go back to it, or can I just select it in the system management?

---

### Post by snowpine on 2008-10-13
> **fs_tigre said:**
> First of all thank you for the quick response to both. If I enter this code (insudo aptitude install kubuntu-desktop) will this create a new installation in a separated partition?

The reason I&#8217;m asking this is because I have all versions of the ubuntu system, and if this is basically a new installation, wouldn&#8217;t be better for me to use the DVD to perform this new installation?

Thanks
Fs_tigre

'sudo aptitude install kubuntu-desktop' will install the KDE desktop environment and its associated applications on top of your Ubuntu installation. Then, each time you log in, you can choose between KDE and Gnome (Ubuntu) at the login screen by choosing Sessions. Because Ubuntu and Kubuntu share much of the same base system, it is a much more efficient use of hard disk space to install them in the same partition using this method. The only drawback that I'm aware of is that your Applications menu will get a bit more crowded, since you'll have two sets of applications.

It's worth mentioning (in response to Northrup) that you can't install Fluxbuntu using this method. It is an "unofficial" release candidate, so 'fluxbuntu-desktop' is not in the repositories. You can get some of the Fluxbuntu experience, if you're curious, using 'sudo apt-get install fluxbox' to add the Fluxbox windows manager to your Sessions menu.

---

### Post by fs_tigre on 2008-10-13
Thank you all for the big help.

---

