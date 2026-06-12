---
title: "openoffice 3.3 installation error with desktop-integration"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by noel4God on 2011-08-22
[SIZE=3]Hello all! Thank you for reading this! 
It's what I encounter when I  try to finish the installation of openoffice 3.3 with  desktop-integration. The other .deb packages install ok.[/SIZE]

```
noel@noel-SN12E200:~/Downloads/OOO330_m20_native_packed-1_en-US.9567/DEBS/desktop-integration$ sudo dpkg -i *.deb
(Reading database ... 152680 files and directories currently installed.)
Unpacking openoffice.org-debian-menus (from openoffice.org3.3-debian-menus_3.3-9556_all.deb) ...
dpkg: error processing openoffice.org3.3-debian-menus_3.3-9556_all.deb (--install):
 trying to overwrite '/usr/share/mime/packages/openoffice.org.xml', which is also in package libreoffice-common 1:3.3.3-1ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
Processing triggers for shared-mime-info ...
Unknown media type in type 'virtual/bluedevil-input'
Unknown media type in type 'virtual/bluedevil-audio'
Unknown media type in type 'virtual/bluedevil-sendfile'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for menu ...
Errors were encountered while processing:
 openoffice.org3.3-debian-menus_3.3-9556_all.deb
```[SIZE=3]I tried several times to uninstall openoffice from Kpackagekit, but I still have the same errors.
Please provide a solution, if you can! Any quick help will do.
Thank you! have a nice day![/SIZE]

---

### Post by 655dmd on 2011-09-07
I had the same problem.  LibreOffice kept crashing in right click  and 3.3.4 & 3.4.3 would not work for me.

1.Go to Synaptic Package Manager.  

2.Search for "libreoffice".  This will pull everything that is installed for libreoffice.  

3.Sort the results by clicking the first column it has an "S".  Click on it once or twice to get the installed packages to appear on the top.  

4.Select all the packages with green boxes by selecting the first package and holding shift down arrow until the last installed package is highlighted.  

5.Right click highlighted selection and choose "mark for removal".  

6.Go back to term session and cd desktop-integration, then sudo dpkg -i *.deb.  Enjoy OO!

---

### Post by noel4God on 2011-09-07
Thanks [655dmd]("http://ubuntuforums.org/member.php?u=1422567"), it works now! I was greedy and wanted to use both of them at the same time, to compare them, since I'm kind of new to linux.... but I guess OOO is better, and I'll stick with it.

Thank you, may God bless you!
Noel

---

