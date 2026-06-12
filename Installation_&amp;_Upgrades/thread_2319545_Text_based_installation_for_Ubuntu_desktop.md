---
title: "Text based installation for Ubuntu desktop"
date: 2016-04-05
forum: Installation &amp; Upgrades
---

### Post by luislupe on 2016-04-05
Before, there was an alternate DVD with text based installation.

Now, for 16.04, what alternatives do I have for a text base installation of a Ubuntu desktop system?  Is it still included in the official ISO image?

hypothesis 1:
Need to install Ubuntu server.  Then check what packages are installed.
Install elsewhere Ubuntu desktop, get the list of installed packages.
In the server edition: remove the packages not available for the desktop version and install all other that are present in the desktop version that are missing in the server edition.

hypothesis 2:
install the alternate DVD of version 12.04 and upgrade it to 14.04 and the to 16.04.  Or could I upgrade it directly to 16.04?

What other ways do I have to do this?  Hope to read some comments.
Thanks.

---

### Post by grahammechanical on 2016-04-05
As far as I know Ubuntu no longer has an Alternative CD ISO image but Lubuntu does.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

Ubuntu does have a Minimum CD ISO image with a download size of about 40 MB and all installation is done by downloading from the internet. And we can select which desktop environments to load. The minimum CD ISO image uses a text based installer. The latest minimum CD ISO images are for 14.04 & 15.10. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Regards.

---

### Post by oldfred on 2016-04-05
You should be able to install the server version. 
It uses tasksel to choose what version of server you want. You may be able to not select anything?
 Used by Server install to choose what you want, you can install in any version to get typical server groups of packages.
sudo apt-get install tasksel
sudo tasksel 


I saved this before with precise. You do not need to install a desktop version, but review its manifest and convert manifest to a list of applications to install.
 List of default applications:
Look for manifests for version:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)
[http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/) 
   Then to install that manifest:
dpkg-query -W --showformat='${Package} ${Version}\n' > casper/filesystem.manifest
apt-get install -y $(awk '{print $1}' filesystem.manifest) 


       From old install, if you have one.
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by luislupe on 2016-04-06
Thank you very much to both of you: grahammechanical  and oldfred.

---

