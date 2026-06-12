---
title: "Broken Packages"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by Mosabama on 2010-02-16
Hi .. I used ubuntu tweak to clean some packages .. it seems it missed up something...

when I try to install gnome-do (new docky one) this is what happens:
```

mosab@mosab-laptop:~$ sudo apt-get install gnome-do
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-do: Depends: libgconf2.24-cil (>= 2.24.0) but it is not installable
            Depends: libgnome-vfs2.24-cil (>= 2.24.0) but it is not installable
E: Broken packages
mosab@mosab-laptop:~$ 


```

---

### Post by wojox on 2010-02-16
Did you install the ppa's? To do so, go to the System menu, then to the Administration category, and then select Software Sources.

When Software Sources opens up, click on the Other Software tab.

In the Other Software tab, click on the Add button. The system will then ask you to type in an apt line. Type in the following source EXACTLY as it appears:

```
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
```

Then add this source:

```
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
```

Click the Add Source button, and close out of Software Sources. After you close out, Software Sources will update your repository information, which might take a few minutes. After that’s done, go to a Terminal window (Applications menu, Accessories, and then the Terminal icon), and use this command to install the GNOME Do package:

```
sudo apt-get install gnome-do
```

---

### Post by Mosabama on 2010-02-16
it solved the dependency issue , but its not the docky one !!! 
what is ppa anyway ?

---

### Post by wojox on 2010-02-16
It's the docky one. I can't remember but you have to configure it for docky. Right click on it and select properties or something. It's been a while since I played with that. :D

---

### Post by Mosabama on 2010-02-16
you were right .. it worked ... thanks for your help:)

so what is ppa ?

---

### Post by wojox on 2010-02-16
[Personal Package Archive (PPA)]("https://help.launchpad.net/Packaging/PPA")

---

