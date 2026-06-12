---
title: "General installation question"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by arunsub on 2005-06-08
When we install a package using dpkg -i, Ubuntu installs the package to a particular folder say /usr/lib/firestarter 0.9. You then see the firestarter executable file under /usr/bin or /usr/sbin. Now I want to copy the new version of the program. The file is in tar.gz or tar.bz. If i unpack the tar file to a folder, then do i have to move the executable to /usr/bin to overwrite the old version?  

Also for some programs, i don't find the folder. if i say whereis programname, i get an answer /usr/bin or /usr/sbin. How do i find where it's installed?

Thanks.

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=arunsub]When we install a package using dpkg -i, Ubuntu installs the package to a particular folder say /usr/lib/firestarter 0.9. You then see the firestarter executable file under /usr/bin or /usr/sbin. Now I want to copy the new version of the program. The file is in tar.gz or tar.bz. If i unpack the tar file to a folder, then do i have to move the executable to /usr/bin to overwrite the old version?  

Also for some programs, i don't find the folder. if i say whereis programname, i get an answer /usr/bin or /usr/sbin. How do i find where it's installed?

Thanks.[/QUOTE]
 For new users, if you installed a package as deb, it is highly recommended that you only update it using again pacakges in deb format.

But is you really must use tarballs: 
Files in  tar.gz or tar.bz format are usually source packages - meaning one has to "build" (compile and isntall) it. As part of buiding, an appropriate script will move the files to required locations. Read INSTALL file inside the archive for instructions. You shouldn't move files by  hand: typical "program" is not a single file, but a lot of files (executables, libraries, config files, documantation, ...) --- all of them go to different locations: typically, libraries go to /usr/lib, executables to /usr/bin, docs to /usr/share/docs, etc. 

Sometimes files in tar.gz formats contain binaries  -- but in this case,  they also have some install script and a README. I have never had to move an executable file to /usr/bin or /usr/sbin manually.

---

### Post by arunsub on 2005-06-08
Thanks.  :)

---

