---
title: "help-Reinstall OOo in 10.04"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by th1bill on 2011-01-07
I messed up!  I see that libreoffice is to replace OOo in 10.04 and in the article from the linux forums newsletter got me interested.  I issued the suggested commands and it installed the libreoffice suite but it had serious depedency problems.

I uninstalled it and unchecked the ppa in other software dources but I cannot reinstall, either from synaptic nor with apt-get install.

---

### Post by th1bill on 2011-01-08
The error msg looks like;

> willis@home:~$ sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
openoffice.org: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.1) but it is not going to be installed
Depends: openoffice.org-writer but it is not going to be installed
Depends: openoffice.org-calc but it is not going to be installed
Depends: openoffice.org-impress but it is not going to be installed
Depends: openoffice.org-draw but it is not going to be installed
Depends: openoffice.org-math but it is not going to be installed
Depends: openoffice.org-base but it is not going to be installed
Depends: openoffice.org-report-builder-bin but it is not going to be installed
Depends: openoffice.org-officebean but it is not going to be installed
Recommends: openoffice.org-filter-binfilter but it is not going to be installed
E: Broken packages
willis@home:~$ 

---

### Post by th1bill on 2011-01-08
I located the article instructions that got me into this mess, it is;

> As a multiplatform application, LibreOffice will run on Windows, Mac or Linux. The download page does provide RPMs, but no packages for Debian/Ubuntu users. Fortunately there’s a PPA, so Ubuntu users can just open a terminal and enter:

View Raw Code?

   1.
      sudo add-apt-repository ppa:libreoffice/ppa
   2.
      sudo apt-get update && sudo apt-get install libreoffice

Alternately, you can also add its unofficial repository to your sources.list,

View Raw Code?

   1.
      sudo gedit /etc/apt/sources.list

Add the following to the end of the file. Save and close.
View Raw Code?

   1.
      deb [http://download.tuxfamily.org/gericom/libreoffice](http://download.tuxfamily.org/gericom/libreoffice) /

Launching

If LibreOffice does not provide menu icons, you can launch it manually with



---

### Post by markus_b on 2011-01-08
I've got exactly the same problem.

I've attempted to install libreoffice along the same instructions. Instead of installing in parallel it uninstalled openoffice, failed to install and prevents going back to install openoffice again.

---

### Post by markus_b on 2011-01-08
I found a solution: Uninstall the 'ure' packages, then disable the libreoffice ppa. Then you can re-install openoffice.

*Markus*

---

### Post by th1bill on 2011-01-08
thankyou Marcus, mine is installing now!

---

### Post by Sallée on 2011-01-10
Thanks for the help!  I also had to uninstall/update/reinstall uno-libs3.

---

### Post by Sallée on 2011-01-16
I spoke too soon!  My icons and themes in OOo are all stock, instead of the Ubuntu branding.  I cannot seem to locate the correct package or proper way to set in from within OOo.  Any help is appreciated.

---

### Post by yerong on 2011-01-17
I have the same problem.. after re-install openoffice, all the icon is old...

---

### Post by Sallée on 2011-01-17
Found it:
```
sudo apt-get install openoffice.org-gtk
```

---

### Post by yerong on 2011-01-17
> **Sallée said:**
> Found it:
```
sudo apt-get install openoffice.org-gtk
```

Thx, it works....

---

