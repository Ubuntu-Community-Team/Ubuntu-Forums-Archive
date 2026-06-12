---
title: "What can be a minimum install &amp; upgrade"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by Tazmman on 2013-03-14
Hello. was hoping some could describe to me how to extract programs, to reduce the size  of my OS. As well as pick  the updates . thanks.

---

### Post by cortman on 2013-03-14
1. ??
2. Use the [Ubuntu Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") to create a system from CLI up.
3. Run

```
sudo apt-get --only-upgrade install package_name
```

to only upgrade (update) package_name.

---

### Post by slickymaster on 2013-03-14
I'm not completely sure I understood what you're asking. When you say *"... extract programs, to reduce the size of my OS..."*, do you mean to remove them from your computer? If so,_ you can do it, but you have to **be sure of what you are removing**, because there is a real risk of data loss or making other programs or Ubuntu unusable when uninstalling and this might leave your system in a funky state, or you might select a critical system file for deletion and this leaves your system unusable_.

But you can achieve it either by clicking **Remove** in the Ubuntu Software Center or at a terminal window, using the following command:
```
sudo apt-get remove --purge <package_name>
``` which will remove the package and it's config files.

---

### Post by ibjsb4 on 2013-03-14
Its better to build from the ground up instead of taking a full install and removing packages.

An example.  To build a desktop using Unity you could install only the packages Unity depends on and not the recommended packages.

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

Like cortman said, use the mini iso and this command:

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

That basically turns the Unity 850MB install into a 150MB install.

And there are a 100 different ways to to a mini install, thats just one.  Minimum GUIs are sometimes install on servers.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

This can also be done with the mini iso.

---

