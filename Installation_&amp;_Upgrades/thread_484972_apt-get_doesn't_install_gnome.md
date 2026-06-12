---
title: "apt-get doesn't install gnome"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by custommadename on 2007-06-26
Hello.  I've installed Ubuntu Server Edition 6.06, and I'm at the terminal.  I'm trying to install Gnome, but I'm told the OS can't find it.
sudo apt-get install gnome
That line doesn't work.  I'm told "E: Can't find..." It seems it's looking in E:?

I'm doing this because I'm not used to using the Terminal.  If, however, you can help me set up FTP access via the terminal only, please check out this thread:
[http://ubuntuforums.org/showthread.php?p=2916836#post2916836](http://ubuntuforums.org/showthread.php?p=2916836#post2916836)

Thank you very much!

---

### Post by bapoumba on 2007-06-26
Hello :)
The complete error message could be useful.
May be a problem with your sources.list?
```
cat /etc/apt/sources.list
```
To show the file on screen. Can you paste it in there ?

---

### Post by custommadename on 2007-06-27
Hello.  I typed sudo apt-get install ubuntu-desktop, and now it's installing.  Do you know which desktop it'll install?

---

### Post by bapoumba on 2007-06-27
> **custommadename said:**
> Hello.  I typed sudo apt-get install ubuntu-desktop, and now it's installing.  Do you know which desktop it'll install?
GNOME :)

---

### Post by stchman on 2007-06-27
> **custommadename said:**
> Hello.  I've installed Ubuntu Server Edition 6.06, and I'm at the terminal.  I'm trying to install Gnome, but I'm told the OS can't find it.
sudo apt-get install gnome
That line doesn't work.  I'm told "E: Can't find..." It seems it's looking in E:?

I'm doing this because I'm not used to using the Terminal.  If, however, you can help me set up FTP access via the terminal only, please check out this thread:
[http://ubuntuforums.org/showthread.php?p=2916836#post2916836](http://ubuntuforums.org/showthread.php?p=2916836#post2916836)

Thank you very much!

Try the following command:

sudo aptitude install ubuntu-desktop

This will install Gnome.

To install KDE type type the following:

sudo aptitude install kubuntu-desktop

---

