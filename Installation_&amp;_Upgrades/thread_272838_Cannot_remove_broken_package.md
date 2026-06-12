---
title: "Cannot remove broken package"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by tribunal on 2006-10-07
There is a "broken" package in my Ubuntu
I want to remove it, but I can't!
Every time I try to do in Adept, Synapric or just with apt-get
I see:
pre-removal script returned -1
But how should I remove it?
It is very important for me

---

### Post by Titus A Duxass on 2006-10-07
Try doing a reinstall with aptitude.  Aptitude is a lot smarter than apt-get and it may give you more feedback.

---

### Post by codejunkie on 2006-10-07
try running ```
sudo apt-get -f install
``` then run 
```
sudo dpkg --configure -a
``` that should automaticly take care of it, if it doesn't you might want to try reinstalling that package again with ```
sudo apt-get install --reinstall packagename
```and try removing it again incase there was some files that were changed causing it to not uninstall correctly. if none of the above works it would be very helpful if you could post the terminal output so we can see what's going on.

---

### Post by tribunal on 2006-10-07
The same error :(
I need something like --force- ... (flag) but not to install, for remove

---

### Post by tribunal on 2006-10-07
This package seems not to be created for ubuntu :(
I was naive and newbie and installed debian's package
But now I cannot remove it

---

### Post by ALainONE on 2006-10-07
I have the same problem with Adept Updater!  Gives me the window message:

> Could not commit changes - Adept Updater
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.
But this sorted it out!

> try running ```
sudo apt-get -f install
``` then run 
```
sudo dpkg --configure -a
``` that should automaticly take care of it

Thanks very much, codejunkie! :D

---

### Post by tribunal on 2006-10-08
I have resolved my problem too! :)
But ALL Ubuntu's tools couldn't help me :(
I had to fix some scripts by hands (!)
It looks like a systematical problem:
Average user should have an oppotunity to remove package even with some pre-errors

---

### Post by fbergeron on 2006-10-27
I have a similar problem.  I've just upgraded to Ubuntu 6.10 and I have a broken package.  I try to remove it and I get the following error message :

```

root@ubuntu:~# aptitude -f install
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been kept back:
  libggi2 mplayer 
The following packages will be REMOVED:
  uim-anthy{p} 
The following packages will be upgraded:
  uim-common 
1 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B/819kB of archives. After unpacking 164kB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 114844 files and directories currently installed.)
Removing uim-anthy ...
ERROR: unbound variable (errobj is-set-ugid?)

*backtrace*
>>(is-set-ugid?)
>>(if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ()))))
>>(define uim-plugin-lib-load-path (if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ())))))
>>(require "plugin.scm")
>>(require "init.scm")
>>(*catch (quote errobj) (require "init.scm"))
>>(eq? (quote *init.scm-loaded*) (*catch (quote errobj) (require "init.scm")))

ERROR: unbound variable (errobj custom-reload-customs)

ERROR: unbound variable (errobj custom-choice-rec-sym)

ERROR: unbound variable (errobj plugin-alist)

ERROR: wta to car (errobj t)

```

How can I remove the uim-anthy package...?

---

### Post by srf21c on 2006-11-08
I've got a similar situation with a fresh Xubuntu 6.10 command line installation, this $%&@ libgnomeui-common package is proving impossible to remove.  The problem is blocking the installation or removal of any other packages on the system.

Here's the sad story pasted below:

```
user@desktop:~$ sudo aptitude -f remove libgnomeui-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  libgnomeui-common 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3248kB will be freed.
Writing extended state information... Done
(Reading database ... 14468 files and directories currently installed.)
Removing libgnomeui-common ...
dpkg: error processing libgnomeui-common (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 libgnomeui-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

user@desktop:~$ sudo dpkg --configure -a

user@desktop:~$ sudo aptitude -f reinstall libgnomeui-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  libgnomeui-common 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/119kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Selecting previously deselected package libgnomeui-common.
(Reading database ... 14468 files and directories currently installed.)
Preparing to replace libgnomeui-common 2.16.1-0ubuntu2 (using .../libgnomeui-common_2.16.1-0ubuntu2_all.deb) ...
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Unpacking replacement libgnomeui-common ...
Setting up libgnomeui-common (2.16.1-0ubuntu2) ...
dpkg: error processing libgnomeui-common (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 libgnomeui-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libgnomeui-common (2.16.1-0ubuntu2) ...
dpkg: error processing libgnomeui-common (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 libgnomeui-common

```

---

### Post by CheeseEatingBulldog on 2006-11-08
I had this problem a while back and nothing helped except the following (mind that it is a hard cut way of solving it)(from one of my old posts here, hope it helps)

> I fixed it, albeit a butchering.

I found [http://forum.linspire.com/viewtopic....12d](http://forum.linspire.com/viewtopic....12d) 05f72ff72

And followed the suggestion to

"Then I went to my /var/lib/dpkg/status file and backed it up (called it status-bak) and removed the "paragraph" or section on the mfc driver which I tried to install (I did a search and then deleted it).
I then ran CNR and tried a update and it worked!!!!!"

Which does indeed work, so if you bugger your apt, then edit its status file.
__________________

---

### Post by srf21c on 2006-11-08
well, I tried this by backing up /var/lib/dpkg/stutus to statusbak and  then opening up the original file to edit in vi.

Searched for libgnomeui-common, and removed the following section:

```
Package: libgnomeui-common
Status: install ok half-configured
Priority: optional
Section: libs
Installed-Size: 3172
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: all
Source: libgnomeui
Version: 2.16.1-0ubuntu2
Config-Version: 2.16.1-0ubuntu2
Replaces: libgnomeui-0 (<= 1.117.0-1), gnome-libs-data (<= 1.4.2-17)
Conflicts: libgnomeui-0 (<= 1.117.0-1)
Description: The GNOME 2 libraries (User Interface) - common files
 This package contains internationalization files for the base GNOME
 library functions (User Interface functions).
Original-Maintainer: Ond&#345;ej Surý <ondrej@debian.org>


```

Saved the file, then tried a manual install of libgnomeui-common

```
sudo dpkg -i libgnomeui-common_2.16.1-0ubuntu2_all.deb 

```

Still getting the same general error.    ](*,)

```
Selecting previously deselected package libgnomeui-common.
(Reading database ... 14457 files and directories currently installed.)
Unpacking libgnomeui-common (from libgnomeui-common_2.16.1-0ubuntu2_all.deb) ...
Setting up libgnomeui-common (2.16.1-0ubuntu2) ...
dpkg: error processing libgnomeui-common (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 libgnomeui-common

```

btw, the link to the linspire forum posting does not work.

---

### Post by CheeseEatingBulldog on 2006-11-08
I am sorry to hear that, this is the link to the thread I started when my apt broke:

> [http://ubuntuforums.org/showthread.php?t=262935](http://ubuntuforums.org/showthread.php?t=262935)

And the linspire link workds fine for me....

---

### Post by drkeuk on 2006-12-17
> **fbergeron said:**
> I have a similar problem.  I've just upgraded to Ubuntu 6.10 and I have a broken package.  

How can I remove the uim-anthy package...?

Fbergeron,

This thread has a solution: [http://www.ubuntuforums.org/showthread.php?t=286944](http://www.ubuntuforums.org/showthread.php?t=286944)

It worked fine for me!

---

### Post by fbergeron on 2006-12-18
> **drkeuk said:**
> Fbergeron,

This thread has a solution: [http://www.ubuntuforums.org/showthread.php?t=286944](http://www.ubuntuforums.org/showthread.php?t=286944)

It worked fine for me!

Thanks a lot.  It worked for me too.

---

