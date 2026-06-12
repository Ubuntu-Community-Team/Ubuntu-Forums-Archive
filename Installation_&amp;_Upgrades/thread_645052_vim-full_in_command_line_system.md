---
title: "vim-full in command line system"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by donbondave on 2007-12-19
hi, i'm just running a command line system (7.10 alternate) and and trying to get syntax highlighting working in vim for various programming languages.   I ssh in to the machine and don't run a monitor or keyboard locally.  the machine, in most respects is a central programming server...

i'm trying to install taglist off of vim.org but i need the full version of vim to do so... vim-tiny is installed be default. when attempting to go to vim-full, i get a lot of dependences that want libs from a graphical install... 

see output below...


```
xxxxx@xxxxxxx:~$ sudo apt-get install vim-full
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vim-full: Depends: vim-gui-common (= 1:7.1-056+2ubuntu2) but it is not installable
            Depends: vim-runtime (= 1:7.1-056+2ubuntu2) but it is not installable
            Depends: libart-2.0-2 (>= 2.3.18) but it is not installable
            Depends: libatk1.0-0 (>= 1.13.2) but it is not installable
            Depends: libbonobo2-0 (>= 2.15.0) but it is not installable
            Depends: libbonoboui2-0 (>= 2.15.1) but it is not installable
            Depends: libcairo2 (>= 1.4.0) but it is not going to be installed
            Depends: libfontconfig1 (>= 2.4.0) but it is not installable
            Depends: libgconf2-4 (>= 2.13.5) but it is not installable
            Depends: libglib2.0-0 (>= 2.14.0) but it is not installable
            Depends: libgnome2-0 (>= 2.17.3) but it is not installable
            Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not installable
            Depends: libgnomeui-0 (>= 2.19.1) but it is not going to be installed
            Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not installable
            Depends: libgtk2.0-0 (>= 2.12.0) but it is not installable
            Depends: libice6 (>= 1:1.0.0) but it is not installable
            Depends: liborbit2 (>= 1:2.14.8) but it is not installable
            Depends: libpango1.0-0 (>= 1.18.2) but it is not going to be installed
            Depends: libruby1.8 (>= 1.8.6.36) but it is not installable
            Depends: libsm6 but it is not installable
            Depends: libx11-6 but it is not installable
            Depends: libxcomposite1 (>= 1:0.3-1) but it is not installable
            Depends: libxcursor1 (> 1.1.2) but it is not installable
            Depends: libxdamage1 (>= 1:1.1) but it is not installable
            Depends: libxext6 but it is not installable
            Depends: libxfixes3 (>= 1:4.0.1) but it is not installable
            Depends: libxi6 but it is not installable
            Depends: libxinerama1 but it is not installable
            Depends: libxrandr2 (>= 2:1.2.0) but it is not installable
            Depends: libxrender1 but it is not installable
            Depends: libxt6 but it is not installable
            Depends: tcl8.4 (>= 8.4.5) but it is not installable
E: Broken packages

```

---

### Post by Pumalite on 2007-12-19
What's the output of:
sudo apt-get install -f

---

### Post by donbondave on 2007-12-19
> **Pumalite said:**
> What's the output of:
sudo apt-get install -f

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Pumalite on 2007-12-19
Did you try:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by donbondave on 2007-12-19
> **Pumalite said:**
> Did you try:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

indeed i did.

---

### Post by Pumalite on 2007-12-19
I imagine, if you have Synaptic, you already tried Edit>Fix Broken Packages.
So. take a look at /var/lib/dpkg/status and see which ones are not 'installed...ok...installed'

---

### Post by Thanoulis on 2007-12-19
Just try to install vim-common and vim-runtime packages only. They do not have the GUI version, so i imagine they will not need GNOME libraries.

---

### Post by donbondave on 2007-12-19
> **Pumalite said:**
> I imagine, if you have Synaptic, you already tried Edit>Fix Broken Packages.
So. take a look at /var/lib/dpkg/status and see which ones are not 'installed...ok...installed'

not using a gui.


> **Thanoulis said:**
> Just try to install vim-common and vim-runtime packages only. They do not have the GUI version, so i imagine they will not need GNOME libraries.

same deal as before, its wanting dependencies met but not pulling them in.

---

### Post by Pumalite on 2007-12-19
Did you see in /var/lib/dpkg/status?

---

### Post by donbondave on 2007-12-20
> **Pumalite said:**
> Did you see in /var/lib/dpkg/status?

i found the following:

```


Package: ubuntu-minimal
Status: purge ok not-installed
Priority: optional
Section: metapackages

Package: vim-tiny
Status: purge ok not-installed
Priority: important
Section: editors

```

i used the following command: cat -n status |grep Status: |more

then did a "less status" and then hit colon, and typed in the line number that showed up in the previous command

---

### Post by Pumalite on 2007-12-20
How are you doing now?

---

### Post by donbondave on 2007-12-20
fed up with Ubuntu shenanigans... heading back to Slackware... at least package management there doesn't work for good reason.

---

### Post by Pumalite on 2007-12-20
Before you give up, you could try editing your status file and changing ununtu-minimal amd vim-tiny to installed...ok...installed.
Reboot and try your apt-get.

---

### Post by donbondave on 2007-12-20
too late.  got everything done in slack already.  got users doing there thing too... we'll try again sometime i think.  seems Ubuntu is making a dent in the w32 markets but still has some kinks to work out.  i'll be back.

---

