---
title: "[SOLVED] Installing OO"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by Firestrider on 2008-10-24
So I have the package OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz on my desktop and I want to install OpenOffice 3 but I'm not sure how to go about it.

I already uninstalled all of the previous open office packages.

When I try to use the package manager on i386 packages I get the error "wrong architecture"

---

### Post by SiN_AmoR on 2008-10-24
> **Firestrider said:**
> So I have the package OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz on my desktop and I want to install OpenOffice 3 but I'm not sure how to go about it.

I already uninstalled all of the previous open office packages.

When I try to use the package manager on i386 packages I get the error "wrong architecture"

weird :confused:
double click the file, (or open it with Archive Manager)..
does it have a (.deb) file inside? or a lot of different files ?

---

### Post by caleb12 on 2008-10-24
If you downloaded from the OO site, it should be a tar ball of all the .debs that you need to install. So, open up Ark or another archive manager and extract the contents to a folder, then issue the command:

sudo dpkg -i *.deb 

in the folder that you extracted the debs... OO3 doesnt create links or anything so you will also have to do that as well...

---

### Post by Firestrider on 2008-10-24
Thanks for the help.

How do I issue a command within a folder?

---

### Post by caleb12 on 2008-10-24
Well you can open a terminal and execute the command... So, for instance if you open a terminal, like Gnome Terminal... 

ALthough, first, open Nautilus and create a folder under your home directory called Temp. Move the OpenOffice tar ball into the Temp folder. Then right click on the tar ball and select extract here or open it with Ark and extract the contents that way.   

Then there are two ways of dealing with the .debs that you've extracted:

Open a terminal and execute:

cd ~/Temp ## That will get you into the directory with the .debs. 

sudo dpkg -i *.deb  ## You will have to enter your password in order to execute the command, but that will install all of the .debs that you extracted. 

Another way to do this, and perhaps easier... is to open Synaptic and select File --> Add Downloaded Packages and then navigate to the .debs that you extracted.

---

### Post by Firestrider on 2008-10-24
Ok I got it through other means.

I added the two repos located here:
[http://www.theopensourcerer.com/2008/10/14/how-to-install-openofficeorg-30-on-ubuntu-intrepid-ibex/](http://www.theopensourcerer.com/2008/10/14/how-to-install-openofficeorg-30-on-ubuntu-intrepid-ibex/)

But I couldn't get it through the update manager because it couldn't be authenticated. So I went into synaptic and searched "openoffice" and marked them for installation.

---

