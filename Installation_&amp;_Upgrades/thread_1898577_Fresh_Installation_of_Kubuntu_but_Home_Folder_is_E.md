---
title: "Fresh Installation of Kubuntu but Home Folder is Encrypted"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by Great Blue Heron on 2011-12-21
Hi, ):P

I am currently running Ubuntu 11.04. When I installed the OS I chose the option to encrypt my Home folder. Now, I want to do a fresh installation of Kubuntu 11.10. 

:?: Is it possible to install Kubuntu and be able to access everything in my encrypted Home folder? Or will I have to back everything up and copy it back over after installing the new OS? Note: I always back up my very important information.

Please advise.  :mrgreen:

---

### Post by MAFoElffen on 2011-12-21
> **Great Blue Heron said:**
> Hi, ):P

I am currently running Ubuntu 11.04. When I installed the OS I chose the option to encrypt my Home folder. Now, I want to do a fresh installation of Kubuntu 11.10. 

:?: Is it possible to install Kubuntu and be able to access everything in my encrypted Home folder? Or will I have to back everything up and copy it back over after installing the new OS? Note: I always back up my very important information.

Please advise.  :mrgreen:
Easiest would be to open a terminal session <Cntrl><Alt><t> and
```

sudo apt-get install kubuntu-desktop

```That would install KDE (and it's app's) and tie everytinig into the Ubuntu base system. The Unbuntu base can have many desktops running on top of it... At the login screen, click on the White Ubuntu Icon above the User Name... A drop down box will have all the installed Desktop Environments listed. Select the one you want to use. Unity 3D, Unity 2D, Gnome3, Gnome Classic, Kubuntu, Xubuntu, Lubuntu, etc. (Whatever is installed.)

I've tested the above with "all" the Ubuntu variant desktops at the same time, plus a few custom java desktops... The one thing that stands out ids that all the applications that are associated with a desktop showup in the menus of all installed Desktop Environments.  Meaning some KDE app's work only in KDE, but they still show out in other Desktop menus. Without saying, this method the installed footprint is bigger in disk space.

The other way is how you are proposing, full fresh/install, which since it is not a separate home partition, would format that directory when it formats the partition. If you backup the home folder before you do it, you could restore it.  One thing you might have to do after that, is to reset the Xauthorities file.

---

### Post by Great Blue Heron on 2011-12-22
Thanks MAFoElffen for the reply. :)

I hadn't thought of just updating Ubuntu to 11.10 and then installing the Kubuntu desktop. I think I will give that a try.

---

