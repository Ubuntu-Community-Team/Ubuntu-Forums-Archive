---
title: "package installation error"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by ooZAFLE on 2006-10-27
hey all

i tried to install the package for k3d, the 3d program, not the cd burning app. And it intalled and worked but it spit out an error while installing and now I can't install or uninstall anything else including k3d. just wondering if anyone has any advice for fixing this. I would really just like to remove the software...

i've already tried dpkg --configure -a and most of the removal options. any help would be great

```
~$ sudo aptitude install k3d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by ooZAFLE on 2006-10-27
ok nvm

i removed the file "pycentral" from /usr/bin then ran #aptitude upgrade again and it worked. just dropped the "pycentral" file back into its folder and everything is working. amazing how simple it can be sometimes. thanks anyway

---

### Post by litodrache on 2006-11-02
Thanks a lot! I did have the same problem and your solution worked just right! :D

---

### Post by bizna on 2006-11-04
Just for those who need a step-by-step help, these are the procedures that are done from the command line:

[LIST=1]
[*]sudo mv /usr/bin/pycentral /
[*]sudo apt-get update
[*]sudo mv /pycentral /usr/bin/
[/LIST]

This should update the k3d package. If you want to remove it, it is done by replacing the second line with the following command:
sudo apt-get remove k3d

Good luck!
Dotan

---

### Post by traveller on 2007-03-30
> **bizna said:**
> Just for those who need a step-by-step help, these are the procedures that are done from the command line:

[LIST=1]
[*]sudo mv /usr/bin/pycentral /
[*]sudo apt-get update
[*]sudo mv /pycentral /usr/bin/
[/LIST]

This should update the k3d package. If you want to remove it, it is done by replacing the second line with the following command:
sudo apt-get remove k3d

Good luck!
Dotan
Just a quick note to thank you for this step-by-step help: I finally managed to remove k3d. I had a similar problem, now it's gone I think.

---

