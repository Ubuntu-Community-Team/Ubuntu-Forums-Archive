---
title: "Installing deb packages from a CD or Directory"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by shoaibnawaz on 2007-11-06
The cost of Broadband Internet is very expensive in my area (Pakistan). The availability of packages for Ubuntu is normally through Internet. Apt-get helps in this regard. All those packages that I get using synaptic package manager are normally stored in a location (/var/cache/apt/archive). If I preserver them for other systems or for re-installation, then how can I manage them with equal ease to "Add/Remove".

---

### Post by logos34 on 2007-11-06
[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)

---

### Post by zvacet on 2007-11-06
[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by shoaibnawaz on 2007-11-20
I have a collection of .deb packages in my flash. This collection, I collected from my desktop system of my office. Because I do not have internet support at home. I copied all the packages in my flash from /usr/share/apt/archive. How can I install them without burning them on CD/DVD (as we do using aptoncd).

Is there any solution which can analyze deb packages stored on some location and then install them with effective user interaction.

---

### Post by ruibernardo on 2007-11-20
Hi shoaibnawaz.

you can just create an ISO file with APTonCD instead of burning it. You can open an ISO file with APTonCD and restore from it. You don't need to burn the ISO file.

[http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html)

---

### Post by maybeway36 on 2007-11-20
You can just install the DEB files with GDebi, but its probably easier if you can find a CD-RW disc.

---

### Post by ruibernardo on 2007-11-20
If shoaibnawaz tried to use GDebi with a package that is on the flash disc on a computer that doesn't have an internet connection, and that package had dependencies packages on the flash disc that were not installed on the hard disk or in the cdrom, GDebi would fail to install that package.

Two possible solutions:[INDENT] - Install dkpg-dev (and its dependencies) with "dpkg -i" and then use dpkg-scanpackage to scan the packages on the directory or flash disk and add a file repository on sources.list. This way GDebi will find the packages and their dependencies.

- Install aptoncd (and its dependencies) with "dpkg -i". APTonCD will scan the packages on the directory too, and it is a easier way to make packages available to the computer without internet connection.
[/INDENT]

---

