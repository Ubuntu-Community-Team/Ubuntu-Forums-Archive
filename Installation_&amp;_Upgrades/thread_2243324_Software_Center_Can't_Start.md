---
title: "Software Center Can't Start"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by nusr on 2014-09-08
Hi,
I'm a new user of Ubuntu. I like it a lot except I don't really know what I'm doing yet.
I got some help from the chat room yesterday, but the problem is still present.

2 packages are not found. More on that below.

After a clean install, everything was working. Then I started installing python3.4 and Idle3. 
Everything seemed fine till later when I tried downloading a firewall from software center.
Nothing launched when I clicked the button.
I checked in terminal 
software-center
bash: /usr/bin/software-center: /usr/bin/python: bad interpreter: No such file or directory

Next I tried to install.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
software-center is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/325 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package software-center (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Setting up software-properties-common (0.92.37.1) ...
Setting up software-properties-gtk (0.92.37.1) ...
Errors were encountered while processing:
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)

Ok I have software-center, but it is not where it is supposed to be /usr/bin

Next I tried purging and install. Same problem.

sudo apt-get purge software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3,015 kB disk space will be freed.
Do you want to continue? [Y/n] 
dpkg: error processing package software-center (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)

I since that didn't work, I tried "reinstalling"

sudo apt-get install --reinstall software-center 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/325 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package software-center.
(Reading database ... 197523 files and directories currently installed.)
Preparing to unpack .../software-center_13.10-0ubuntu4.1_all.deb ...
/var/lib/dpkg/info/software-center.prerm: 6: /var/lib/dpkg/info/software-center.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing archive /var/cache/apt/archives/software-center_13.10-0ubuntu4.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/software-center.postinst: 8: /var/lib/dpkg/info/software-center.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_13.10-0ubuntu4.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


 [B]pyclean: not found
pycompile: not found[/B]

This is something I found on another forum.
Didn't know I needed pycompile.
Same for pyclean.
Why is software-ware checking if these two packages are present?

Can someone help me?
How can I install these two packages to reinstall software-center?


Thank you.

 					 						[h=2]2 Answers[/h]


[TABLE]
[TR]
[TD="class: votecell"]                             up vote     4     down vote                accepted 
              [/TD]
                [TD="class: answercell"]      [py_compile]("http://docs.python.org/release/3.2.3/library/py_compile.html") is a stdlib module that can produce byte-code given Python source. *It is rarely needed.*
  To compile Python 3 source code you must use py_compile version  included with it and not the version from Python 2.7 if you use it from a  command-line:
  $ python3 -mpy_compile your_script.py  To change the default location where pyc-files are stored you could use cfile parameter of the [py_compile.compile() function]("http://docs.python.org/release/3.2.3/library/py_compile.html#py_compile.compile").

[/TD]
[/TR]
[/TABLE]

---

### Post by ian-weisser on 2014-09-09
> **nusr said:**
> After a clean install, everything was working. Then I started installing python3.4 and Idle3. 

/usr/bin/python: bad interpreter: No such file or directory

How can I install these two packages to reinstall software-center?

Hi, welcome to the forums.
And welcome to Ubuntu.

You seem to be running 14.04. Is that correct?

The specific answer to your question is that pyclean and pycompile are provided by the python-minimal package.

Losing /usr/bin/python is real bad. It means your Python2.7 is missing. Big chunks of the system (including Software Center) rely upon finding Python2.7 and/or Python 3.4 at expected locations. Try to avoid overwriting them with different versions. 

Python 3.4 is already installed out-of-the-box on 14.04. You shouldn't need to install it. 
How,  exactly did you install Python3.4? From the Software Center? Off the  internet? Following instructions from someplace? Using terminal  commands? 

You can install all the versions of python that you wish, but do  not change the versions that /usr/bin/python and /usr/bin/python3 link to. The system needs those.

---

