---
title: "Trying to install packages on 10.10 without access to internet"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by Vudue Priest on 2011-02-21
Hi, I'm very new to ubuntu and am having issues with package installations. I am trying to install virtualbox 4.0 without the internet. I am currently deployed in afghanistan, so internet access to personal comps is not available. However the computers they have set up for internet access allows me to download the packages. I have read through a number of threads before posting and could not find one that fit the same circumstances.  So please be gentle lol. as of right now I have the .deb file saved to my desk top and have toyed in terminal to get this to work. Saddly I just do not know enough to solve this problem. I appreciate all of your help.


Other info you may need:
running on a mactel book pro
ubuntu 10.10 64 installed
file name is:  virtualbox-4.0_4.0.4-70112~ubuntu~maveric_amd64.deb
if there is anything else please let me know.

---

### Post by Quackers on 2011-02-21
Copy the .deb file from the computer with internet access to your personal computer (to the Downloads folder maybe) then double-click on the .deb file. What happens?

---

### Post by Vudue Priest on 2011-02-21
After dragging the deb file into the downloads folder i double clicked on the deb file and it mounted it to my desktop. after opening the mounted deb file i have a control.tar.gz package, a data.tar.gz package and a debian-binary file.  I really do appreciate you help

---

### Post by Quackers on 2011-02-21
From the terminal try ```

cd Downloads
sudo dpkg --install file.deb
(where file.deb is changed to the actual deb filename
```

---

### Post by Vudue Priest on 2011-02-21
> **Quackers said:**
> From the terminal try ```

cd Downloads
sudo dpkg --install file.deb
(where file.deb is changed to the actual deb filename
```
I get this error 


 Selecting previously deselected package virtualbox-4.0.
    (Reading database ... 117839 files and directories currently installed.)
    Unpacking virtualbox-4.0 (from virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_amd64.deb) ...
    dpkg: dependency problems prevent configuration of virtualbox-4.0:
     virtualbox-4.0 depends on libqt4-network (>= 4:4.5.3); however:
      Package libqt4-network is not installed.
     virtualbox-4.0 depends on libqt4-opengl (>= 4:4.5.3); however:
      Package libqt4-opengl is not installed.
     virtualbox-4.0 depends on libqtcore4 (>= 4:4.7.0~beta1); however:
      Package libqtcore4 is not installed.
     virtualbox-4.0 depends on libqtgui4 (>= 4:4.7.0~beta1); however:
      Package libqtgui4 is not installed.
    dpkg: error processing virtualbox-4.0 (--install):
     dependency problems - leaving unconfigured
    Processing triggers for ureadahead ...
    ureadahead will be reprofiled on next reboot
    Processing triggers for shared-mime-info ...
    Processing triggers for desktop-file-utils ...
    Processing triggers for python-gmenu ...
    Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
    Processing triggers for hicolor-icon-theme ...
    Processing triggers for python-support ...
    Errors were encountered while processing:
     virtualbox-4.0

---

### Post by Quackers on 2011-02-21
It seems that virtualbox requires files to be installed that you don't have. It won't be possible to install without them afaik. They would automatically be picked up as dependencies by a package manager like Synaptic. It may be possible to download the extra packages separately, but they too may have dependencies. It could go on for some time.

---

### Post by Vudue Priest on 2011-02-21
I had a feeling that was going to be an issue. I appreciate your time.

---

### Post by Quackers on 2011-02-21
No problem. Unfortunately lots of installations problems are dependency based. It makes things very difficult if you can't directly connect to the internet.

---

### Post by Vudue Priest on 2011-02-21
In light of this fact, can anyone tell me if wine 1.3.13 will have the same problem because the same actions in terminal dont seem to work on .tar.bz2 files...

---

### Post by Vudue Priest on 2011-02-21
I suppose finding an internet source is my only option for configuring linux lol

---

### Post by Vudue Priest on 2011-02-22
So after an almost sleepless night I found a few threads that explain how to add a repository... However the packages (wine 1.3 and virtualbox 4.0) on a disk are not being permitted to be added under synaptic saying "e:failed to mount the cdrom"... like wise trying "sudo apt-cdrom add" says that "E: unable to locate any package files, perhaps this is not a debian disc or the wrong architecture?"  I am almost completely at a loss as what to do. As my earlier posts said I'm in Afghanistan without internet for PCs. I do have access to internet via government windows based computer. Any advice one can share would be greatly appreciated. Just for clarification I only want one of the two applications to run computer games.  Again thank you all for your support.

---

### Post by jcmb on 2011-03-08
Hey brother, try this page out for offline installations: [https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection](https://help.ubuntu.com/community/InstallingSoftware#Installing%20packages%20without%20an%20Internet%20connection)

---

### Post by jcmb on 2011-03-08
These are the packages you need to install VirtualBox 4.0 on a fresh Ubuntu 10.10 machine:

dkms_2.1.1.2-3ubuntu1.1_all.deb
fakeroot_1.14.4-1ubuntu1_amd64.deb
libaudio2_1.9.2-3_amd64.deb
libmng1_1.0.10-1_amd64.deb
libqt4-dbus_4.7.0-0ubuntu4.2_amd64.deb
libqt4-network_4.7.0-0ubuntu4.2_amd64.deb
libqt4-opengl_4.7.0-0ubuntu4.2_amd64.deb
libqt4-xml_4.7.0-0ubuntu4.2_amd64.deb
libqtcore4_4.7.0-0ubuntu4.2_amd64.deb
libqtgui4_4.7.0-0ubuntu4.2_amd64.deb
patch_2.6-2ubuntu1_amd64.deb

You can download them manually from packages.ubuntu.com, but I used Keryx to download them for me!

---

