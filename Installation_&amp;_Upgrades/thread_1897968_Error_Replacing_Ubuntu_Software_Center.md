---
title: "Error Replacing Ubuntu Software Center"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by ravi sharan on 2011-12-20
I was trying to install security/software updates using Update Manager. When Update Manager began applying changes, I got the following error message:

installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
 LANGUAGE = (unset),
 LC_ALL = (unset),
 LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
 LANGUAGE = (unset),
 LC_ALL = (unset),
 LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
 LANGUAGE = (unset),
 LC_ALL = (unset),
 LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ...
dpkg: warning: files list file for package `libfontenc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfolks25' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfolks-telepathy25' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfribidi0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfontconfig1' missing, assuming package has no files currently installed.

(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 236440 files and directories currently installed.)
Preparing to replace app-install-data-partner 12.11.10 (using .../app-install-data-partner_12.11.10.1_all.deb) ...
Unpacking replacement app-install-data-partner ...
dpkg: error processing /var/cache/apt/archives/app-install-data-partner_12.11.10.1_all.deb (--unpack):
 trying to overwrite '/usr/share/app-install/desktop', which is also in package app-install-data 0.11.10.6
Preparing to replace software-center 5.0.2ubuntu0.1 (using .../software-center_5.0.3.1_all.deb) ...
Unpacking replacement software-center ...
dpkg: error processing /var/cache/apt/archives/software-center_5.0.3.1_all.deb (--unpack):
 trying to overwrite '/usr/share/app-install/desktop', which is also in package app-install-data-partner 12.11.10
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/app-install-data-partner_12.11.10.1_all.deb
 /var/cache/apt/archives/software-center_5.0.3.1_all.deb
Error in function:

I tried 'sudo apt-get clean' and then tried to update. But, still I am unable to install/replace Ubuntu Software Center and Applications Installer. Please help me.

---

### Post by raja.genupula on 2011-12-20
try this 
sudo apt-get install -f
sudo apt-get update

give here the results if you got any error

---

### Post by ravi sharan on 2011-12-20
> **raja.genupula said:**
> try this 
sudo apt-get install -f
sudo apt-get update

give here the results if you got any error
Still same problem persists ! Is this some sort of Bug ???

---

### Post by raja.genupula on 2011-12-20
> **ravi sharan said:**
> Still same problem persists ! Is this some sort of Bug ???

you got no errors ?

---

### Post by ravi sharan on 2011-12-20
> **raja.genupula said:**
> you got no errors ?
same errors shown every time I try to update ! No change yet !

---

### Post by raja.genupula on 2011-12-21
open your synaptic once ...look for any broken packages if they are then fix them and try again.

---

