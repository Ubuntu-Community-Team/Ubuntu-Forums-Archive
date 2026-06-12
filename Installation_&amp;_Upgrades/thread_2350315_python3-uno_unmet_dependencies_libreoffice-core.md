---
title: "python3-uno unmet dependencies libreoffice-core"
date: 2017-01-23
forum: Installation &amp; Upgrades
---

### Post by ct952 on 2017-01-23
Hi all,
On xubuntu 16.04, I'm trying to install package 'python3-uno' using 'sudo apt-get install python3-uno', but I'm stuck with the following error:

The following packages have unmet dependencies:
 python3-uno : Depends: libreoffice-core (= 1:5.1.4-0ubuntu1) but 1:5.2.1~rc2-0ubuntu1~trusty0 is to be installed
E: Unable to correct problems, you have held broken packages.

Any idea on how to correct this, other than installing 'uno' via python installer ('pip3 install uno'), that would introduce other dependency problems with a file called 'base.py'?

Many thanks

---

### Post by ian-weisser on 2017-01-23
python3-uno is already a dependency of LibreOffice. You should not need to install it separately.

Have you been upgrading LibreOffice from some PPA or other non-Ubuntu source? That's the most common cause of held broken packages.
If so, uninstall LibreOffice completely, disable the source, and revert to the supported Ubuntu version.

---

### Post by ct952 on 2017-01-24
It worked, many thanks. As  ian-weisser pointed out, probable cause was some obsolete PPA when upgrading xubuntu from release 14 to 16. Reinstalling Libreoffice fixed the problem. Now python3-uno is correctly installed and I can use "import uno" in my python scripts.

Here below the steps I followed:

First, I uninstalled Libreoffice as explained here:
[http://askubuntu.com/quesunotions/180403/how-to-uninstall-libreoffice](http://askubuntu.com/quesunotions/180403/how-to-uninstall-libreoffice)

sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove

Then I used the "Software & Updates" tool in XUbuntu, on the "Other software" tab I removed all the obsolete PPA.

Finally, I reinstalled Libreoffice using "Ubuntu Software Center"

---

