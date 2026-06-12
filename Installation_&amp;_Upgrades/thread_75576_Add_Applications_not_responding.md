---
title: "Add Applications not responding"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by viniosity on 2005-10-13
I installed Colony 5 and have been upgrading pretty regularly without problems.  At some point the Add Applications menu option stopped responding.  It initializes teh application and resolves dependencies but then i just get the spinning gnome wait cursor.

I assume people who did a fresh install of the release aren't seeing this.  Since I am 'up to date' what can I do to get this working again?

---

### Post by Tomy on 2005-10-13
Right now I am logged into Hoary and downloading the Breezy torrent so I can't find the name of the "Add Applications" package. Sometimes I drag an icon out to the desktop and then look at 'properties' to see what app is being run.

If you have a rough idea of the package name try this:

$ sudo apt-cache search keyword

If you find the name of the package you want to fix try this:

$ sudo apt-get install --reinstall packageName

If you think I know what I am talking about :confused: please remember that I am an end-user and know nothing or very little. :???:

good luck

---

### Post by heimo on 2005-10-14
Tomy is on the right track. That's what I'd try, reinstalling gnome-app-install
```
sudo apt-get --purge remove gnome-app-install
sudo mv /usr/lib/gnome-app-install/AppInstall.pyc /tmp
sudo apt-get install gnome-app-install

``` (apt-get gave me error for that AppInstall.pyc and I had to "remove" it manually.) Maybe this will help?

EDIT: couple errors

---

### Post by viniosity on 2005-10-14
I tried that but after install it's still stuck.  I also did an apt-get clean to make sure it would re-download the .deb just in case.  In that case, prior to install, I saw these errors on the command line:

```

Get:1 http://us.archive.ubuntu.com breezy/main gnome-app-install 0+20051005 [2362kB]
Fetched 2362kB in 1m27s (26.9kB/s)
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory

```

Maybe I should just reinstall..

---

### Post by viniosity on 2005-10-14
Ok, I ran this from the terminal (as root) and I'm seeing this error:

```

  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 778, in __mergeFile
    raise ParsingError('File not found', filename)
xdg.Exceptions.ParsingError: ParsingError in file '/etc/xdg/menus/applications-m erged/nxclient.menu', File not found

```

Looking in that directory I saw that I had a missing symlink (from when I uninstalled nxclient).  Getting rid of that symlink fixed my problem!

---

