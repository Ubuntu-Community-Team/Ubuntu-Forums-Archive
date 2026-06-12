---
title: "How to generate a list of all installed software/packages?"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2008-07-01
How to generate a list of all installed software?

How to generate a list of all installed packages?

---

### Post by Alan Coleman on 2008-07-01
* The Debian menuInstall the Debian menu. The Debian menu has a much more thorough list of your installed applications, and it will be available as a category in your existing Applications menu. You need to install the package called menu-xdg and possibly restart X (ctrl + alt + backspace) for it to show up.


Hope this helps.
found it in the absolute beginers thread.
it should be more public knowlage.

hope you find what youve lost.

---

### Post by sdennie on 2008-07-01
To see all the packages installed you can use:

```

dpkg -l | grep "^ii"

```

You may want to redirect that to a file because it's going to be a lot of packages:

```

dpkg -l | grep "^ii" > packages.txt

```

---

### Post by iaculallad on 2008-07-01
The terminal command you need list all currently installed packages is dpkg –get-selections.

```
dpkg --get-selections
```

To pipe the output to a file:

```
dpkg --get-selections > Installed_Packages.log
```

---

### Post by blackhawx on 2010-06-30
> **iaculallad said:**
> The terminal command you need list all currently installed packages is dpkg –get-selections.

```
dpkg --get-selections
```To pipe the output to a file:

```
dpkg --get-selections > Installed_Packages.log
```


but how does it now where to save that outputted file too?  will it just pop up after running that command?

---

### Post by blackhawx on 2010-06-30
> **sdennie said:**
> To see all the packages installed you can use:

```

dpkg -l | grep "^ii"

```You may want to redirect that to a file because it's going to be a lot of packages:

```

dpkg -l | grep "^ii" > packages.txt

```


thank you!!!

---

### Post by jocko on 2010-07-01
> **blackhawx said:**
> but how does it now where to save that outputted file too?  will it just pop up after running that command?
The file will be saved wherever you tell it to.
To be sure where it ends up, use the full path and not just the file name, so to get it in your home directory:
```
dpkg --get-selections > /home/[COLOR=Blue]username[/COLOR]/Installed_Packages.log
```

If you don't include the path in the command, it will be saved in whichever folder you are currently in. A terminal always opens in your home directory, so unless you cd away from there that's where the file will end up.

---

### Post by veko on 2010-07-01
If you want to list all the packages in order to install them again (after fresh upgrade, or when cloning install to another computer), here's a handy trick.  This is directly from dpkg man pages:

```
       
       To make a local copy of the package selection states:
            dpkg --get-selections >myselections

       You might transfer this file to another computer, and  install  it  there
       with:
            dpkg --clear-selections
            dpkg --set-selections <myselections

       Note that this will not actually install or remove anything, but just set
       the selection state on the requested packages. You will need  some  other
       application  to actually download and install the requested packages. For
       example, run apt-get dselect-upgrade.

```So with:
```

dpkg –get-selections > mypackages.txt
sudo dpkg –set-selections < mypackages.txt
sudo apt-get dselect-upgrade

```you should be able to copy and replicate your setup.

---

