---
title: "Getting errors trying to install BURG boot manager"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by pmgmr2 on 2011-03-10
Hello!  I've been using Ubuntu for a few months now and I'm learning A LOT, but still have to periodically dual-boot into Windows 7.  I recently found out about the Burg manager on this article:
[http://www.howtogeek.com/howto/45164/how-to-customize-the-ubuntu-bootloader-screen/](http://www.howtogeek.com/howto/45164/how-to-customize-the-ubuntu-bootloader-screen/)

When I entered the synaptic package manager and tried to install BURG, I got a dialog box that says "an error occured.  The following details are provided:"

```

E: linux-image-2.6.35-27-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

```

I've googled and come up with erratic results.  This is my first time on the forum, and any help would be greatly appreciated!  Thanks in advance.

---

### Post by Hakunka-Matata on 2011-03-11
Did the repository add alright, no errors?  Any broken packages showing in synaptic?
[http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg]("http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg")
maybe that link will help

---

### Post by Oppa888 on 2011-03-27
I believe the solution here is to run the following command in a terminal session:

sudo apt-get -f install

(this will fix any broken dependencies and automatically download and install them)

Then you can reinstall burg.....

---

### Post by Hakunka-Matata on 2011-03-28
That command-line is so oft quoted, yet rarely seems to produce sought after goal.

If only ```
sudo apt-get -f install
``` fixed the incomplete, or partial update or upgrade task it would be warranted to show up so often in these forums.

That being said, I do hope it works for the OP.  If ```
 sudo apt-get -f install
``` does not work I suggest the OP persue a series of commands investigating the contents of various /cache folders with the objective of discovering the listing of previously issued individual commands qualified at the start of each line with a status symbol (llike a bentley for example) of ```
rc
i
ii
iii
```**NOW, **if only I can remember/find those command lines, they are a series of commands along the lines of```
ls /etc/var/cache 

```  But I don't remember which directories (folders) are involved, I do believe they are all "cache" folders

**HELP ANYBODY??????**

---

