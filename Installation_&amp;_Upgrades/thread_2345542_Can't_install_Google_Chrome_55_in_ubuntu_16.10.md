---
title: "Can't install Google Chrome 55 in ubuntu 16.10"
date: 2016-12-05
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-12-05
I get the following error message:

```
henry@wyatt:~/Downloads$ sudo dpkg -i google-chrome-stable_current_amd64.deb
(Reading database ... 206882 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (55.0.2883.75-1) over (55.0.2883.75-1) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libappindicator1; however:
  Package libappindicator1 is not installed.

dpkg: error processing package google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3+16.10.20160929-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu4) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Errors were encountered while processing:
 google-chrome-stable
henry@wyatt:~/Downloads$
```

Software Manager does not install either.

Henry

PS There is no libappindicator1 to install.

PSS Now every time I reboot I get a red warning on the top bar.

---

### Post by slickymaster on 2016-12-05
Open a terminal window and run ```
sudo apt-get install -f
``` to resolve the dependency issues.

---

### Post by Hewjr100 on 2016-12-05
This is the output:

```
henry@wyatt:~/Downloads$ sudo dpkg -f google-chrome-stable_current_amd64.deb
Package: google-chrome-stable
Version: 55.0.2883.75-1
Architecture: amd64
Maintainer: Chrome Linux Team <chromium-dev@chromium.org>
Installed-Size: 175552
Pre-Depends: dpkg (>= 1.14.0)
Depends: gconf-service, libasound2 (>= 1.0.16), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.11), libcairo2 (>= 1.6.0), libcups2 (>= 1.4.0), libdbus-1-3 (>= 1.1.4), libexpat1 (>= 2.0.1), libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.3.9), libgcc1 (>= 1:4.1.1), libgconf-2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.26.0), libgtk2.0-0 (>= 2.24.0), libnspr4 (>= 2:4.9-2~) | libnspr4-0d (>= 1.8.0.10) | libnspr4 (>= 4.9.5-0ubuntu0), libnss3 (>= 2:3.13.4-2~) | libnss3-1d (>= 3.12.4), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.8.0), libx11-6 (>= 2:1.4.99.1), libx11-xcb1, libxcb1 (>= 1.6), libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxi6 (>= 2:1.2.99.4), libxrandr2 (>= 2:1.2.99.3), libxrender1, libxss1, libxtst6, ca-certificates, fonts-liberation, libappindicator1, libnss3 (>= 3.17.2), lsb-base (>= 4.1), xdg-utils (>= 1.0.2), wget
Provides: www-browser
Section: web
Priority: optional
Description: The web browser from Google
 Google Chrome is a browser that combines a minimal design with sophisticated technology to make the web faster, safer, and easier.
henry@wyatt:~/Downloads$
```

---

### Post by slickymaster on 2016-12-05
> **Hewjr100 said:**
> This is the output:

henry@wyatt:~/Downloads$ **[COLOR=#ff0000]sudo dpkg -f google-chrome-stable_current_amd64.deb[/COLOR]**
Package: google-chrome-stable
Version: 55.0.2883.75-1
Architecture: amd64
Maintainer: Chrome Linux Team <chromium-dev@chromium.org>
Installed-Size: 175552
Pre-Depends: dpkg (>= 1.14.0)
Depends: gconf-service, libasound2 (>= 1.0.16), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.11), libcairo2 (>= 1.6.0), libcups2 (>= 1.4.0), libdbus-1-3 (>= 1.1.4), libexpat1 (>= 2.0.1), libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.3.9), libgcc1 (>= 1:4.1.1), libgconf-2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.26.0), libgtk2.0-0 (>= 2.24.0), libnspr4 (>= 2:4.9-2~) | libnspr4-0d (>= 1.8.0.10) | libnspr4 (>= 4.9.5-0ubuntu0), libnss3 (>= 2:3.13.4-2~) | libnss3-1d (>= 3.12.4), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.8.0), libx11-6 (>= 2:1.4.99.1), libx11-xcb1, libxcb1 (>= 1.6), libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxi6 (>= 2:1.2.99.4), libxrandr2 (>= 2:1.2.99.3), libxrender1, libxss1, libxtst6, ca-certificates, fonts-liberation, libappindicator1, libnss3 (>= 3.17.2), lsb-base (>= 4.1), xdg-utils (>= 1.0.2), wget
Provides: www-browser
Section: web
Priority: optional
Description: The web browser from Google
 Google Chrome is a browser that combines a minimal design with sophisticated technology to make the web faster, safer, and easier.
henry@wyatt:~/Downloads$
That's the wrong command.

See [my last post]("https://ubuntuforums.org/showthread.php?t=2345542&p=13578889&viewfull=1#post13578889") and use the command I asked to be used.

---

### Post by Hewjr100 on 2016-12-05
Ok that worked. So what do I do to install google chrome 55?

Henry

---

### Post by slickymaster on 2016-12-05
It is now installed. To run it from terminal use ```
google-chrome
``` or hit the super key and search Google or Chrome

---

### Post by Hewjr100 on 2016-12-05
Here is the output, tried 3 different ways.

```
henry@wyatt:~$ google-chrome
google-chrome: command not found
henry@wyatt:~$ google-chrome-stable
google-chrome-stable: command not found
henry@wyatt:~$ sudo google-chrome-stable
[sudo] password for henry:          
sudo: google-chrome-stable: command not found
henry@wyatt:~$
```

Henry

---

### Post by slickymaster on 2016-12-05
Hmmm, that's odd. Can you please past the output you get from```
apt-cache policy google-chrome-stable
```

And also, please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting code. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Hewjr100 on 2016-12-05
Here is the output:

```
henry@wyatt:~$ apt-cache policy google-chrome-stable
google-chrome-stable:
  Installed: (none)
  Candidate: (none)
  Version table:
     55.0.2883.75-1 -1
        100 /var/lib/dpkg/status
henry@wyatt:~$
```

Henry

---

### Post by slickymaster on 2016-12-05
Again I ask you to [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output code.

As for your issue and as Chrome is available on [3rd Party Repository: Google Chrome]("http://www.ubuntuupdates.org/ppa/google_chrome?dist=stable") install it this way:```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update 
sudo apt-get install google-chrome-stable
```

---

### Post by Hewjr100 on 2016-12-05
That did the trick, google chrome is installed, thank you very much.

Henry

---

### Post by Hewjr100 on 2016-12-06
Ok, at this point I have removed google chrome, also removed both google chrome keys.  Now I have re downloaded google chrome 64 bit, what is the best way to install it properly.  Ubuntu software did not install it last time.

Henry

---

### Post by slickymaster on 2016-12-07
> **Hewjr100 said:**
> Ok, at this point I have removed google chrome, also removed both google chrome keys.  Now I have re downloaded google chrome 64 bit, what is the best way to install it properly.  Ubuntu software did not install it last time.

Henry
In my opinion, adding Google Chrome PPA. By adding the PPA to your system you'll also receive the latest updates whenever you check for a system update.

---

### Post by vasa1 on 2016-12-07
> **slickymaster said:**
> In my opinion, adding Google Chrome PPA. Adding the PPA to your system you'll also receive the latest updates whenever you check for a system update.
I think that [downloading the Google Chrome deb]("https://www.google.com/chrome/browser/desktop/") and installing it using something like gdebi would automatically (behind the scenes) install the PPA.

---

### Post by slickymaster on 2016-12-07
> **vasa1 said:**
> I think that [downloading the Google Chrome deb]("https://www.google.com/chrome/browser/desktop/") and installing it using something like gdebi would automatically (behind the scenes) install the PPA.

Yes it does, vasa1. Apparently the OP was having issues doing it that way, hence my answer.

---

### Post by howefield on 2016-12-07
> **vasa1 said:**
> I think that [downloading the Google Chrome deb]("https://www.google.com/chrome/browser/desktop/") and installing it using something like gdebi would automatically (behind the scenes) install the PPA.

Using apt to install the locally stored Chrome .deb file will add the PPA.

```
sudo apt install ~/Downloads/google-chrome-stable_current_amd64.deb 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'google-chrome-stable' instead of '/home/hugh/Downloads/google-chrome-stable_current_amd64.deb'
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-47 linux-headers-4.4.0-47-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-47-generic linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-47-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
  google-chrome-stable
0 to upgrade, 1 to newly install, 0 to remove and 2 not to upgrade.
Need to get 0 B/46.1 MB of archives.
After this operation, 180 MB of additional disk space will be used.
Get:1 /Data/Downloads/google-chrome-stable_current_amd64.deb google-chrome-stable amd64 55.0.2883.75-1 [46.1 MB]
Selecting previously unselected package google-chrome-stable.
(Reading database ... 282292 files and directories currently installed.)
Preparing to unpack .../google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (55.0.2883.75-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up google-chrome-stable (55.0.2883.75-1) ...
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/google-chrome (google-chrome) in auto mode
```

```
ls -ll /etc/apt/sources.list.d/
total 4
-rw-r--r-- 1 root root 189 Dec  7 10:16 google-chrome.list
```

```
apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/7FAC5991 2007-03-08
uid                  Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
sub   2048g/C07CB649 2007-03-08

pub   4096R/D38B4796 2016-04-12
uid                  Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
sub   4096R/640DB551 2016-04-12 [expires: 2019-04-12]

pub   4096R/F6D61D45 2015-05-27 [expires: 2017-05-26]
uid                  Opera Software Archive Automatic Signing Key 2015 <packager@opera.com>
sub   4096R/26451C35 2015-05-27 [expires: 2017-05-26]
```

Shrug :)

---

