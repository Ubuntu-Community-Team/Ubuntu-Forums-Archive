---
title: "VirtualBox broke my apt"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by kliklik on 2007-01-26
I've tried to install [VirtualBox]("http://www.virtualbox.org"), it broke my apt and I cannot fix it, please help!

```
**$** sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.**
```

```
**$** sudo dpkg --remove --force-remove-reinstreq virtualbox
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 121067 files and directories currently installed.)
Removing virtualbox ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing virtualbox (--remove):
 subprocess pre-removal script returned error exit status 1
-e 
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox
```

And when I try reinstalling it (by doubleclicking on a deb file), I get (attachment 1):
```
**Could not open 'VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb'**
The package might be corrupted or you are not allowed to open the file. Check permissions of the file.
```
But the deb is ok and I have permissions.

```
**$** sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
```

Also
```
**$** sudo dpkg -i VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb 
Selecting previously deselected package virtualbox.
(Reading database ... 121069 files and directories currently installed.)
Preparing to replace virtualbox 1.3.2-20070114_Ubuntu_edgy (using VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb) ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
(Kernel module not found)...fail!
invoke-rc.d: initscript virtualbox, action "stop" failed.
dpkg: error processing VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb (--install):
 subprocess new pre-removal script returned error exit status 1
-e 
Creating group 'vboxusers'. VM users must be member of that group!

No precompiled module for this kernel found -- trying to build one
Messages displayed during module compilation will be logged to /var/log/vbox-install.log
Compilation of kernel module failed, aborting installation
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb
```

Please, tell me what else I can try. I'm getting desperate.

---

### Post by carlos.gil on 2007-01-27
Same problem here

---

### Post by carlos.gil on 2007-01-27
Found it!

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

---

### Post by kliklik on 2007-01-27
Thanks! I've looked for the solution on their site but somehow missed it.

[QUOTE=virtualbox.org]
Debian packages: If the installation of the VirtualBox_*.deb package was not successful because the compilation of the kernel module fails, it might not be possible to remove the package nor to install other packages as the pre-remove (prerm) script of the package (which is executed prior to package removing or upgrading) aborts with an error "(Kernel module not found)...fail!". In that case do the following:
[LIST]
[*]Edit /etc/init.d/virtualbox and change line 129 from 'exit 1' to 'exit 0'
[*]Reinstall the virtualbox package by 'dpkg -i <the VirtualBox package for your distribution>'. An installation failure of this package is expected.
[*]Edit /var/lib/dpkg/info/virtualbox.postinst and change line 39 from 'exit 1' to 'exit 0'
[*]Execute 'dpkg --configure --pending'
[*]The package should now be installed successfully. However, the kernel module is still not compiled. Before you will be able to execute VirtualBox you have to create a kernel module for your current kernel, as described in the User Manual (see our Downloads section).
[/LIST][/QUOTE]

---

### Post by Rich78 on 2007-02-04
I*

---

