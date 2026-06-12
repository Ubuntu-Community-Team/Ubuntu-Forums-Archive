---
title: "Installing pyqt5-dbus on Mint (for hplip)"
date: 2017-03-23
forum: MINT
---

### Post by chellrose on 2017-03-23
I'm running Mint 17.3 and trying to install hplip 3.16.11 from the hplip  site.  My printer requires at least hplip 3.16.10, so I can't use the  older version in the repository.

When running the hplip  installation script, it has several missing dependencies and asks if I  want the installer to install them for me.  I choose "yes" to all but  then I get this error:

```
warning: Missing REQUIRED dependency: pyqt5-dbus (PyQt 5 DBus - DBus Support for PyQt5)
warning: This installer cannot install 'pyqt5-dbus' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.


```

I have installed pyqt5.  I cannot find pyqt5-dbus in the repository, or on google.  How do I get this package?

---

### Post by pdc on 2017-03-23
on our Mint 18.1, I find that if I open synaptic; (the file installer programme); and if I type in pyqt5-dbus that I get a variety of files that I could install; that seem to be in the Mint repos; (as per the screenshot)

If they really are not there, then Debian seems to have most things in its store cupboards; and as ubuntu uses debian packages; from debian; they should install fine: with some downloads though, you need to check if they are 32 or 64bit specific

[https://packages.debian.org/source/sid/pyqt5](https://packages.debian.org/source/sid/pyqt5)

---

### Post by ajgreeny on 2017-03-23
I am not sure about the repos that Mint uses, but to install the hplip-3.16.11.run file, and I am assuming that is what you're using, in Ubuntu you have to ensure that both **universe** and **multiverse** repo versions are enabled or some of the dependencies are not available.
See [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) for the details of what is needed.

Could this be your problem? Open up software-sources and have a look.

---

