---
title: "Package Operation failed"
date: 2013-05-12
forum: Installation &amp; Upgrades
---

### Post by CamPsych on 2013-05-12
Hi all, 

Every time that I try to do any upgrades or installations I keep getting the error message Package Operation Failed - The
installation or removal of a package operation failed. 

```
installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 303314 files and directories currently installed.) 
Preparing to replace libasound2:i386 1.0.25-3ubuntu3 (using .../libasound2_1.0.25-3ubuntu3.1_i386.deb) ... 
Unpacking replacement libasound2:i386 ... 
Preparing to replace alsa-utils 1.0.25-3ubuntu2 (using .../alsa-utils_1.0.25-3ubuntu2.2_i386.deb) ... 
Unpacking replacement alsa-utils ... 
Preparing to replace telepathy-idle 0.1.12-1 (using .../telepathy-idle_0.1.12-1ubuntu0.1_i386.deb) ... 
Unpacking replacement telepathy-idle ... 
Processing triggers for man-db ... 
Processing triggers for ureadahead ... 
Setting up openemr (4.1.1-1) ... 
dpkg: error processing openemr (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Setting up libasound2:i386 (1.0.25-3ubuntu3.1) ... 
Setting up alsa-utils (1.0.25-3ubuntu2.2) ... 
Setting up telepathy-idle (0.1.12-1ubuntu0.1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 openemr 
Setting up openemr (4.1.1-1) ... 
dpkg: error processing openemr (--configure): 
 subprocess installed post-installation script returned error exit status 1
```

It looks like an Issue with Open EMR (a medical records program) when I try to uninstall this program, it tells me that it cannot be removed and that the Software Centre needs to fix errors? 

Any ideas on this one?

---

### Post by ibjsb4 on 2013-05-12
How and from where did you install openemr?

---

### Post by CamPsych on 2013-05-12
Installed directly from the Software Centre

---

### Post by ibjsb4 on 2013-05-12
You may of used the software center to install it, but your download either came from SourceForge or OpenEMR home page.  Which would make it either a tar file or a deb file that you downloaded.  The deb file (made for Ubuntu) from the home page would be the better way to go.

---

### Post by ibjsb4 on 2013-05-12
You may of used the software center to install it, but your download either came from [SourceForge]("http://sourceforge.net/projects/openemr/") or [OpenEMR home]("http://www.open-emr.org/wiki/index.php/OpenEMR_Downloads") page.  Which would make it either a tar file or a deb file that you downloaded.  The deb file (made for Ubuntu) from the home page would be the better way to go.

---

### Post by CamPsych on 2013-05-12
Yes, I believe that it was the OpenEMR page, now that you say, so is there a fix for the problem that I am having?

---

### Post by ibjsb4 on 2013-05-12
Im going to load it and see what happens.  Get back to you later tonight :)

---

### Post by ibjsb4 on 2013-05-12
Ok, I could not get the .deb download to install so I tried the .tar.gz install and was successful.  But now am hitting this snag with the site.

[ATTACH=CONFIG]242542[/ATTACH]

So all I can tell you at this point is to install the .tar.gz package.  And then go to the OpenEMR forum and ask for help.

[http://www.open-emr.org/forum.shtml](http://www.open-emr.org/forum.shtml)

Good luck :)

---

### Post by CamPsych on 2013-05-19
Cheers for the help, checking out the forums to see if I can get any answers.

---

### Post by CamPsych on 2013-05-22
OK, so I have found a fix for this. It involves deleting files from /var/lib/dpkg/info/openemr. I deleted all the openemr files in this folder. Seems to have fixed the issue and no more error message at this time.

---

