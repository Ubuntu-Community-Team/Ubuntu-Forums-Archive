---
title: "Firefox does not open after 3.6.6 update"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by finsyourfriend on 2010-06-30
Hey all,

This morning my Ubuntu 8.04 Hardy box was all Hardy. The Update Manager told me to install some updates, which included a Firefox 3.6.6 update. That update failed to install, and now I everytime I click on the panel launcher or go to "Applications," then "Internet" and then "Firefox" I get the following error: Could not launch menu item Failed to execute child process "firefox" (No such file or directory)

Thanks to any and all in advance.

Jon

Note: When running Firefox from Terminal:

```
jonathan@ubuntu-desktop:~$ firefox 
The program 'firefox' is currently not installed.  You can install it by typing: 
sudo apt-get install firefox-3.0 
bash: firefox: command not found 
jonathan@ubuntu-desktop:~$ sudo apt-get install firefox-3.0 
[sudo] password for jonathan:  
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following extra packages will be installed: 
  firefox firefox-branding 
Suggested packages: 
  firefox-gnome-support latex-xft-fonts 
The following NEW packages will be installed: 
  firefox firefox-3.0 firefox-branding 
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B/11.4MB of archives. 
After this operation, 30.5MB of additional disk space will be used. 
Do you want to continue [Y/n]? Y 
(Reading database ... 140604 files and directories currently installed.) 
Unpacking firefox-branding (from .../firefox-branding_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/firefox-branding_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb (--unpack): 
 trying to overwrite `/usr/share/pixmaps/firefox.png', which is also in package firefox-2 
Unpacking firefox (from .../firefox_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb (--unpack): 
 trying to overwrite `/usr/share/bug/firefox/presubj', which is also in package firefox-2 
Selecting previously deselected package firefox-3.0. 
Unpacking firefox-3.0 (from .../firefox-3.0_3.6.6+nobinonly-0ubuntu0.8.04.1_all.deb) ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/firefox-branding_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb 
 /var/cache/apt/archives/firefox_3.6.6+nobinonly-0ubuntu0.8.04.1_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
jonathan@ubuntu-desktop:~$ 

```

---

### Post by ozp on 2010-06-30
I have this bug too!!! help

---

### Post by varunendra on 2010-06-30
You can try uninstalling it via synaptic if it is listed there & then installing an older, stable version via synaptic or by manually downloading it from firefox's website (3.5, for instance).


EDIT: As far as I remember, if you downloaded manually, the download will contain an archive of a working ff directory which you may need to extract & create a shortcut to the executable manually (I'm not sure though). It won't integrate in your previous installation. So it is better if you could do it via synaptic.

---

### Post by ozp on 2010-06-30
they had released a fix. Just download the package again and install

really good to have a new firefox

---

### Post by mobilediesel on 2010-06-30
I found that when you click links in an email they would no longer open in firefox. I figured out that I had to go to the terminal and do this:
```
sudo update-alternatives --config x-www-browser
```
and then pick firefox as the default browser.
I'm not sure why that got un-set when firefox was updated but it was easy enough to fix.

---

### Post by finsyourfriend on 2010-06-30
UPDATE: I uninstalled all the installed packages with references to firefox and then reinstalled the package marked "firefox." It installed both the firefox package and the firefox branding package and sucessfully installed 3.6. Even my bookmarks are there. \\:D/ Looks like I can still take the wife out to dinner and be relaxed tonight after all. Thanks everyone for your help.

---

