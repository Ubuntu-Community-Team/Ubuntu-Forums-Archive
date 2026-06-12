---
title: "Unity not working with Mobility Radeon HD 3650"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Marco309 on 2011-05-01
Hi there.
I've got big problems with ubuntu 11.04 (32 Bit, on Lenovo T500 with ATI Mobility Radeon HD 3650)
First of all i have to boot from the installation cd with the option "nomodeset".
Also for the first boot from harddisk i have to set this option. 
After i have installed the proprietary ATI drivers i can boot with the default options but unity won't start....
On dmesg i found following messages:
> 
 [  415.901678] unity_support_t[2357]: segfault at 4 ip b76b2824 sp bfaeee50 error 4 in libGL.so.1.2[b7639000+c9000]
 [  415.905490] unity_support_t[2359]: segfault at 4 ip b75a1824 sp bfd3fa90 error 4 in libGL.so.1.2[b7528000+c9000]
I tried to set the gl config with 
 > update-alternative --set gl_conf /usr/lib/fglrx/ld.so.confwhich failed with following message:
> 
 update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in manual mode.
 update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group gl_conf) doesn't exist.
 update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group gl_conf) doesn't exist.
I'll tried to create an symlink: 
> /usr/lib32 -> /usr/libAfter that update-alternatives returned no warning, but unity still won't start.......

---

### Post by Marco309 on 2011-05-02
Any ideas? 
Need help :-(

---

### Post by vmonkey on 2011-06-08
Same problem here with HD 3400 :(. Did anyone find a solution?

---

### Post by GinoMan2440 on 2011-10-22
I'm having the same problem too, I can't install fglrx, fglrx-dev, fglrx-amdcccle, etc. It says the following:

```

root@gino-HP-Pavilion-dv6-Notebook-PC:/etc/alternatives# aptitude install
The following partially installed packages will be configured:
  fglrx fglrx-amdcccle fglrx-dev xvba-va-driver 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up fglrx (2:8.881-0ubuntu4) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: error: unable to install /usr/lib32/libaticalcl.so.dpkg-tmp as /usr/lib32/libaticalcl.so: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xvba-va-driver:
 xvba-va-driver depends on fglrx-driver (>= 1:10-9) | fglrx (>= 2:8.840); however:
  Package fglrx-driver is not installed.
  Package fglrx is not configured yet.
dpkg: error processing xvba-va-driver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 fglrx
 xvba-va-driver
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up fglrx (2:8.881-0ubuntu4) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: error: unable to install /usr/lib32/libaticalcl.so.dpkg-tmp as /usr/lib32/libaticalcl.so: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xvba-va-driver:
 xvba-va-driver depends on fglrx-driver (>= 1:10-9) | fglrx (>= 2:8.840); however:
  Package fglrx-driver is not installed.
  Package fglrx is not configured yet.
dpkg: error processing xvba-va-driver (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 xvba-va-driver
 fglrx-dev
                                         

```

.... please help me, this is getting on my nerves and i want my 3D accelerated OpenGL!!!

---

### Post by john stiles on 2012-03-03
Has anyone been able to make progress on this? 

I can get OpenGL by uninstalling fglrx and using my on board Intel graphics chip set, but I suspect this is the root of my problem to not connect to my hdmi TV. I've tried the proprietry driver, I've even tried compiling the driver to no avail.

Any news, hints or, dare I ask, solutions from anyone?

---

