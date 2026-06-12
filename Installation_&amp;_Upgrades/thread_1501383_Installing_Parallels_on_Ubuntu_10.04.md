---
title: "Installing Parallels on Ubuntu 10.04"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by leatherjacket on 2010-06-04
Many Parallels users are having issues with Parallels after upgrading to Ubuntu 10.04

Tried posting this solution on the Parallels Forum, but the website does not want to play along :-(

After struggling with it for a couple of hours I finally managed to get it working
Below is a rough outline of what I did - 

Reply to this post if you have particular issues - Can't guarantee the solution, but
it worked for me ...

---------------------------------------------------------------------------------------
Fixing  Parallels to run on Ubuntu 10_04 x64bit after Ubuntu 10.04 upgrade - not sure if this will work on fresh install

>> sudo -i

run the Parallels installer (it will crash at 96% complete)

Find the temp  directory in /tmp into which the parallels kernel module sources where  installed
typically /tmp/.XXXXXXX (i.e. it is a HIDDEN directory) - lets call this directory TMPDIR

it contains
ChangeLog  dkms.conf  Makefile  src(dir)

edit the file in TMPDIR/parallels-kernel-modules/src/vtd/prl_os.c
add the line:  #include "/linux/sched.h"

make sure that you have the kernel headers installed in your system

change back to  "tmpdir"/parallels-kernel-modules
run 'make '
(this should compile the new kernel module without errors)

"tmpdir"/parallels-kernel-modules  is also the place where dkms.conf can be found - to install the module  follow the following steps:

1) add the kernel-module to the dkms system using the following  commands (replacing xxx.xxx with the version number of your parallels  4.0 installer)

dkms add -m parallels-desktop -v 4.0.xxx.xxx
dkms  build -m parallels-desktop -v 4.0.xxx.xxx
dkms install -m parallels-desktop -v 4.0.xxx.xxx

2) reboot the  machine (might not be required - but I did it just in case)

3) change to /etc/init.d in a terminal
sudo  ./parallels-desktop start

You should now be able to run Parallels Desktop without trouble

Hope this helps

The Parallels Forum did not want me to upload this fix :-(
-------------------------------------------------------------------------------------------------------------------------

---

### Post by BIACS on 2010-06-12
Thank you for your post. I was disappointed to see Parallels not supporting 10.04. 
I was able to get the make to compile but am running into a problem with the dkms commands. 
From the /tmp/.******/parallels-kernel-modules directory I run dkms add -m parallels-desktop -v 4.0.6630.449744 which is the version I'm trying to install. 
The error message says Error! Could not find module source directory.
Directory: /usr/src/parallels-desktop-4.0.6630.449744 does not exist.

If I create that dir in /usr/src/ and run the dkms command again I get; Error! Could not locate dkms.conf file but the dkms.conf is located in the directory I'm in (still the /tmp/.*****/parallels-kernel-modules dir)

Any suggestions?
Thank you
Craig

---

### Post by leatherjacket on 2010-06-18
Hi 

Think I missed a step in my explanation

to use dkms you should copy the tmp directory of source created by parallels 
to /usr/src 

You should also name it with the exacly correct parallels version number

my case it looks like

/usr/src/parallels-desktop-4.0.6630.449744

inside dir I have
Changelog    dkms.conf    Makefile     src(dir)

Hope this helps
Regards

---

### Post by time2spare on 2010-06-25
Thank you both for your posts. It also worked for me but I found the #include line needed to be changed to use brackets to compile i.e.

#include "/linux/sched.h" -> #include <linux/sched.h>  

Thanks again,

Dennis

---

### Post by djanie78 on 2010-08-09
> **leatherjacket said:**
> Many Parallels users are having issues with Parallels after upgrading to Ubuntu 10.04

Tried posting this solution on the Parallels Forum, but the website does not want to play along :-(

After struggling with it for a couple of hours I finally managed to get it working
Below is a rough outline of what I did - 

Reply to this post if you have particular issues - Can't guarantee the solution, but
it worked for me ...

---------------------------------------------------------------------------------------
Fixing  Parallels to run on Ubuntu 10_04 x64bit after Ubuntu 10.04 upgrade - not sure if this will work on fresh install

>> sudo -i

run the Parallels installer (it will crash at 96% complete)

Find the temp  directory in /tmp into which the parallels kernel module sources where  installed
typically /tmp/.XXXXXXX (i.e. it is a HIDDEN directory) - lets call this directory TMPDIR

it contains
ChangeLog  dkms.conf  Makefile  src(dir)

edit the file in TMPDIR/parallels-kernel-modules/src/vtd/prl_os.c
add the line:  #include "/linux/sched.h"

make sure that you have the kernel headers installed in your system

change back to  "tmpdir"/parallels-kernel-modules
run 'make '
(this should compile the new kernel module without errors)

"tmpdir"/parallels-kernel-modules  is also the place where dkms.conf can be found - to install the module  follow the following steps:

1) add the kernel-module to the dkms system using the following  commands (replacing xxx.xxx with the version number of your parallels  4.0 installer)

dkms add -m parallels-desktop -v 4.0.xxx.xxx
dkms  build -m parallels-desktop -v 4.0.xxx.xxx
dkms install -m parallels-desktop -v 4.0.xxx.xxx

2) reboot the  machine (might not be required - but I did it just in case)

3) change to /etc/init.d in a terminal
sudo  ./parallels-desktop start

You should now be able to run Parallels Desktop without trouble

Hope this helps

The Parallels Forum did not want me to upload this fix :-(
-------------------------------------------------------------------------------------------------------------------------

Guys... what do you mean by "make sure you go the kernel headers install in your system" Am getting errors following this to get parallels to work on 10.04.

thanks

---

### Post by sinombre5 on 2011-04-19
Hi to everyone.
I have tried all the steps mentioned.
But i got this error message
root@nicola-desktop:/etc/init.d# sudo ./parallels-desktop start
Starting Parallels services
    Loading Parallels kernel modules:FATAL: Module prl_vtdhook not found.
Cannot load module 'prl_vtdhook'

Can anyone help me please?

I'm Running Ubuntu 10.10

Or anyone can help me giving me the steps to install parallels?

My REgards!

ATte.
Nicola Campos

---

### Post by dethorpe on 2011-11-27
Old thread i lnow. But just wanted to say thanks, this worked a treat for me. Have parallels 4 runing on 10.04 64bit

---

