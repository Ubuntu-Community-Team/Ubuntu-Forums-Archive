---
title: "Cannot install tar.gz directory for the life of me"
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by Evan_Heward on 2015-11-08
So I recently downloaded OpenOffice for x64 Deb linux. I had no idea how to install a tar.gz file until I looked around a bit and found the whole terminal "./configure" and "tar -xzf" method. I thought it would work but apparently the configure file doesn't exist in *any *of the directories of the OpenOffice file. There goes that. At this point I'm sorely confused as to what to do and I'm wondering if installing software on Ubuntu should be this hard or if I'm doing something wrong that's making it difficult.

---

### Post by steeldriver on 2015-11-08
What file did you download, exactly? The ones on the main page are pre-built binaries I think - you should probably be following the instructions [here]("http://www.openoffice.org/download/common/instructions.html#linux") instead

The ./configure step only applies when building software from source code (and then not always - other build systems like cmake and scons are becoming more common)

In general, installing software on Ubuntu isn't hard - you could install LibreOffice in place of OpenOffice in a couple of clicks

---

### Post by Evan_Heward on 2015-11-08
Ohhhh I see. Thank you so much for the help, I needed to set the folder as a local repository in the software center. As for the LibreOffice substitute, I can't use it as I have a Computer Literacy class that requires the use of OO or Microsoft Office.

---

### Post by ajgreeny on 2015-11-08
Libreoffice is to all intents and purposes a newer (and arguably better) version of OO, having been forked from OO when it looked as if OO was perhaps losing its open-source status.

If you must use OO go to [http://www.openoffice.org/download/](http://www.openoffice.org/download/) and download the appropriate 32 or 64 bit version of the DEB archive, if that is not what you have already.  The installation instructions are at the same site and say
> Linux DEB-based Installation

    One you download the Apache OpenOffice tar.gz package, you should be able to decompress typing.
    tar Apache-OpenOfficeX.X.X.tar.gz package or using programs such as Ark, or File-Roller.
    cd into the DEBS subdirectory of the installation directory.
    You should see a lot of debs here and one sub-directory called "desktop-integration".
    Install this new version by typing sudo dpkg -i *.deb or become root using su command.
    By default, this will install/update Apache OpenOffice in your /opt directory.

    Alternatively, you can use a GUI package installer, reference the installation directory, and install all debs at the top level. This may also aid you in determining any dependency problems if they exist.
    Install the desktop integration features for your setup.
    cd to desktop-integration (in the installation directory),
    and install the desktop intgration using dpkg.
    Finally, start up Apache OpenOffice 4.x.x to insure it's working.


---

### Post by Evan_Heward on 2015-11-08
That worked perfectly, I now have OO up and running no problem. I was running into issues with those instructions because I hadn't completely uninstalled Libre, using the purge command solved that. Thanks!

---

