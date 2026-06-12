---
title: "Installing Symantec Endpoint Protection (12.1.6) (or other)"
date: 2015-11-27
forum: Installation &amp; Upgrades
---

### Post by Thomaz on 2015-11-27
I am having problem installind Symantec Endpoint Protection (they gave me 12.1.6).
> The Ubuntu version is 14.04 .
 I don't want to downgrade if not necessary.
The installation script aborts based on java version, but I tried w/ 7 and now I have 8.
I found this
[http://www.symantec.com/connect/articles/how-install-symantec-endpoint-protection-1215-supported-linux-operating-systems](http://www.symantec.com/connect/articles/how-install-symantec-endpoint-protection-1215-supported-linux-operating-systems)
Someone tried ?
Thanks, best.

---

### Post by Thomaz on 2015-11-27
I download the package jce_policy-8.zip from Symantec in order to install the Endpoint Protection 12.1.6, 
But unziping, they came w/ 2 .jar files, so I couldn't install the package needed because the install script only recognizes the java version using this patch.
Any ideas ?
I am using UBUNTU 14.04 and tried java 7, but now changed to Java 8.

---

### Post by ajgreeny on 2015-11-27
Threads merged.  Please do not start duplicate threads as it dilutes forum resources and is very confusing for you and all others.

---

### Post by Thomaz on 2015-11-27
I saw, but didn't want to erase 1 , because could erase both. And the messages are different, to avoid someone would suggest the second operation.

---

### Post by Thomaz on 2015-11-27
I put the 2 files came in .zip file in the place of the old ones (backing-up this old).
Tried ./install.sh -i , aborting w/ error:
Starting to install Symantec Endpoint Protection for Linux
Performing pre-check...
Pre-check succeeded
Begin installing virus protection component
(Lendo banco de dados ... 232388 ficheiros e directórios actualmente instalados.)
Preparing to unpack .../App Linux/./Repository/sep.deb ...
Missing package files: //../install.sh, please check the package and use a valid one.
Virus protection component failed to install, with error:  /home/arquitetura/Documentos/App Linux/./Repository/sep.deb

And tried dpkg -i sep.deb (inside Repository directory), but aborted with this:
Starting to install Symantec Endpoint Protection for Linux
Performing pre-check...
Pre-check succeeded
Begin installing virus protection component
(Lendo banco de dados ... 232388 ficheiros e directórios actualmente instalados.)
Preparing to unpack .../App Linux/./Repository/sep.deb ...
Missing package files: //../install.sh, please check the package and use a valid one.
Virus protection component failed to install, with error:  /home/arquitetura/Documentos/App Linux/./Repository/sep.deb


May the package is damaged ?
Thanks,

---

### Post by Thomaz on 2015-11-27
i did it, w/ other package.
The result was:
Pre-check is successful
Unpacking savap-legacy (12.1.6168-6000) ...
Legacy Auto-Protect component failed to install, with error:  savap-legacy
Pre-compiled Auto-Protect kernel modules are not loaded yet, need compile them from source code
Auto-Protect source code package does not exist
Installation completed
=============================================================
Daemon status:
symcfgd                [running]
rtvscand            [running]
smcd                [running]
=============================================================
Error: No drivers are loaded into kernel.
=============================================================
Auto-Protect starting
Protection status:
Definition:    Waiting for update.
AP:        Malfunctioning
=============================================================
The log files for installation of Symantec Endpoint Protection for Linux are under ~/:
sepfl-install.log
sep-install.log
sepap-install.log
sepap-legacy-install.log
sepui-install.log
sepjlu-install.log
sepfl-kbuild.log

And when try to install SEP, they hags with the same result.

What should I do now ?

---

### Post by Thomaz on 2015-11-27
i did it, w/ other package.
The result was:
Pre-check is successful
Unpacking savap-legacy (12.1.6168-6000) ...
Legacy Auto-Protect component failed to install, with error:  savap-legacy
Pre-compiled Auto-Protect kernel modules are not loaded yet, need compile them from source code
Auto-Protect source code package does not exist
Installation completed
=============================================================
Daemon status:
symcfgd                [running]
rtvscand            [running]
smcd                [running]
=============================================================
Error: No drivers are loaded into kernel.
=============================================================
Auto-Protect starting
Protection status:
Definition:    Waiting for update.
AP:        Malfunctioning
=============================================================
The log files for installation of Symantec Endpoint Protection for Linux are under ~/:
sepfl-install.log
sep-install.log
sepap-install.log
sepap-legacy-install.log
sepui-install.log
sepjlu-install.log
sepfl-kbuild.log

The logs files are showing the same.
Is the installation successful ?
How can I test?

---

### Post by Thomaz on 2015-11-30
The Endpoint status is with
Status
Status Malfunctioning
Scan Done
Last connect <blank>
Location Default
Policy Serial Number OK
What should I do ?

---

### Post by Thomaz on 2015-12-07
Someone answered this, but I couldnt finding it and I closed the tab :-(
Type the answer here, please.
Thanks,

---

### Post by Thomaz on 2015-12-07
I saw this solution to SEP 12.1.5 :
**Re: Installing SEP 12.1.5 Ubuntu 14.10 x64**
[INDENT]                     Check logs:

cat ~/sep-install.log
cat ~/sepf-install.log

Seems sep.deb(preinst script) uses empty $PWD

Fastest way - copy endpoint files to root directory(/, not /root) and execute install.sh from there.                 [/INDENT]
            
                         

Do I need to desinstall and try this ?
I don't think it will solve this problem. Probably will result the same error, because isn't an installation error,  but a connection issue.

---

