---
title: "Installation --- where do files go?"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-02-05
My first question is very basic. When one does an installation of a package how can one determine the new files that are saved (or existing files modified) on your system and more important --- where are they placed?

Two examples:

1)_ Installation of LyX_. This package (vers. 1.6.4) was installed and it requires that certain LaTeX files be on the system. Apparently it installs some LaTeX files itself and sets up a path to them. However when I test LyX, it is unable to find many of the LaTeX files that it needs. It seems that the installation does not recognize where the files are located. Note, the files that it needs are on my system!

2) _Installation of Texmaker_. This package (1.9.9) again requires that certain LaTex files be on the system. However, when I examine (in its toolbars) the location of these files  is incorrect! Again the installation does not find the correct path to the files that it should be using even though they are on my system.

Some information that might be helpful:
* I uninstalled (completely) both of these packages and then installed again --- no change from above.
* I have Ubuntu 9.10 installed.
* I have installed the complete TeXLive package (took 1 hr and 12 minutes!) which is now in:  [FONT=Fixedsys]**[FONT=System]/usr/local/texlive/2009[/FONT]** and **[FONT=System]/usr/local/texlive/texmf-local[/FONT]**[/FONT]
* I have defined (as suggested from the TeXLive installation) the following environment variables:

 [B]MANPATH = /usr/local/texlive/2009/texmf/doc/man
 INFOPATH = /usr/local/texlive/2009/texmf/doc/info[/B]
 
 
* The following was added to PATH (as strongly recommended in the TeXLive installation):

  **/usr/local/texlive/2009/bin/i386-linux**

[COLOR=Red]What must I do to get these two packages to use the correct paths?[/COLOR]

Thanks,
--V

---

### Post by BbUiDgZ on 2010-02-05
i don't know how to fix your issue or anything about your applications but i thought i'd post to make you aware of the "locate" command, it might help you (if you already know this please ignore).

to use the locate command you first need to update the database of file locations

```
sudo updatedb
```

to find a file/files

```
 sudo locate filename-or-part-filename
```

hope this is of some use

---

### Post by awam66 on 2010-02-05
Hi there,
If you want to know what files are installed and where, go to Synaptic Package Manager, find the app you are interested in right click on it and select Properties. Go to the "Installed Files" tab and bingo there they all are.

---

### Post by Herman on 2010-02-05
Oops - too late.

---

### Post by awam66 on 2010-02-06
[QUOTE=virsto;8777304]My first question is very basic. When one does an installation of a package how can one determine the new files that are saved (or existing files modified) on your system and more important --- where are they placed?

Have you been successful yet?

---

### Post by oldos2er on 2010-02-06
> **awam66 said:**
> If you want to know what files are installed and where, go to Synaptic Package Manager, find the app you are interested in right click on it and select Properties. Go to the "Installed Files" tab and bingo there they all are.

Or ```
dpkg -L <package name>
```

---

