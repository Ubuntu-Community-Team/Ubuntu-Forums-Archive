---
title: "stuck with oss-linux"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by bracc0 on 2007-05-29
Hi,
trying to fix a sound problem on my notebook Fujitsu Siemens Lifebook C1410 with feisty, I installed the package oss-linux.
Having verified that oss-linux 4.0 doesn't fix my sound problem I decided to remove it. That's the start of my nightmare.

Synaptics doesn't start anymore.
After synaptics start i receive this message:
"the package oss-linux must be re-installed but its archive can't be found"
After this message, Synaptics kick me off and close itself.

The archive oss-linux_v4.0-1002_i386.deb is present in my home directory, and it's perfectly "browsable" with the tool "Debian package viewer". Furthermore, is owned by root group roo, and the permissions are set to rwxrwxrwx.

No luck with sudo apt-get install or remove:
same error than Synaptics
same error with the command  "gdebi oss-linux_v4.0-1002_i386.deb"
and same error with "sudo aptitude install oss-linux" too.

Any idea? Any guru need to see some files? Just ask!

Thanks in advance
Claudio

---

### Post by jamesjtucker on 2007-05-29
Claudio,
   where did you get this package? I cant find it in any of the repositories. Try this in a terminal wherever the .deb is:  'sudo dpkg -i oss-linux_v4.0-1002_i386.deb'
  That should install it or complain about broken dependencies, let us know what happens. After it properly installs, you can try to remove it by doing a 'sudo apt-get remove oss-linux [hit the tab key here to see if it completes], or by trying to find the package in aptitude.

---

### Post by bracc0 on 2007-05-29
> **jamesjtucker said:**
> Claudio,
   where did you get this package? I cant find it in any of the repositories. 

I got the package from [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

> **jamesjtucker said:**
> 
Try this in a terminal wherever the .deb is:  'sudo dpkg -i oss-linux_v4.0-1002_i386.deb' 

That should install it or complain about broken dependencies, let us know what happens.

Good point. I tried with apt-get, with aptitude, with synaptic and with gdebi. I didn't try (yet) with dpkg. I'll let you know tomorrow. 

Thank you
Claudio

---

### Post by bracc0 on 2007-05-30
Here's the output of the command suggested:

> 
**claudio@claudio-laptop:~$ sudo dpkg -i oss-linux_v4.0-1002_i386.deb**

Password:
(Lettura del database ... 127798 file and directory installed.)
Preparing substitution of oss-linux v4.0-1002 (with oss-linux_v4.0-1002_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - the old pre-removal exit with code 2
dpkg - trying script of new package ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1002_i386.deb (--install):
 The new pre-removal script subprocess exit with code 2
Building OSS Modules for Linux-unknown 2.6.20-16-generic
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: errore while cleaning:
 The post-installation script subprocess exit with code 1
There are errors while processing:
 oss-linux_v4.0-1002_i386.deb


Tried to remove "/usr/lib/oss/starting" and re-running the dpkg command with no success.

Permissions on the deb package (re-downloaded) are as follows:

-rwxr-xr-x  1 root    root    2844184 2007-05-29 12:50 oss-linux_v4.0-1002_i386.deb




Thanks in advance
Claudio

---

### Post by bracc0 on 2007-05-31
Hi,
finally I got rid of oss-linux.

I simply executed the command:

sudo dpkg --extract oss-linux_v4.0-1002_i386.deb ./<any dir you like>

Then I re-run the command:

sudo dpkg -i oss-linux_v4.0-1002_i386.deb

and I take note where the uninstall/install script complained about missing files.
I placed the missing files in the appropriate directory, and I re-run the installation.

After three loops the install script succeded! After that I have been able to uninstall oss-linux

Thanks
Claudio

---

### Post by jamesjtucker on 2007-05-31
Thats great to hear. Thanks for posting the followup!

---

