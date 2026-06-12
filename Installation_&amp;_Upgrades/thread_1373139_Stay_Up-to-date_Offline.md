---
title: "Stay Up-to-date Offline"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by auriza on 2010-01-05
[B][http://auriza.site40.net/notes/ubuntu/stay-update-offline/](http://auriza.site40.net/notes/ubuntu/stay-update-offline/)

[/B]This guide will help you to stay up-to-date and to install packages without Internet connection. It must be annoying when other people can install package instantly but you can't. But don't give up yet, just read the rest of this guide.
  What you need is: your computer with Ubuntu installed (computer A), other computer with Internet connection (computer B), and [DownThemAll!]("https://addons.mozilla.org/en-US/firefox/addon/201") (Firefox extension). I use Ubuntu 9.04 for this guide. This guide hasn't been tested intensively, so comments and suggestions are  welcomed.
  [B]
1. Set Repository Server[/B]

In computer A, choose the best server for your country, the download time will be faster.  In this guide I use Ubuntu main server, [http://archive.ubuntu.com](http://archive.ubuntu.com). You can set this in "*System - Administration - Software Sources*".
  [B]
2. Generate Download Links for List Files[/B]

```
$ sudo apt-get update --print-uris | cut -d "'" -f 2 -s
[http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2)
[http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)
[http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)
...    
```[B]

3. Download List Files, Reserve Full URI[/B]

Download all of those list files in computer B. I use DownThemAll! to download them because it have renaming mask feature. Specify the renaming mask to ***curl*/*name*.*ext***. After the download completed, copy the list files to computer A. The directory structure must looks like below.
 
```
$ ls
archive.ubuntu.com  security.ubuntu.com

$ tree -fi * | grep [PR]
archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg
archive.ubuntu.com/ubuntu/dists/jaunty/Release.txt
archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2
archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2
archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2
archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2
...  
```[B]

4. Rename List Files, Replace / with _[/B]

 ```
$ mkdir new
$ for i in `tree -fi * | grep [PR]`; do cp $i new/${i//\//_}; done
$ cd new
$ ls
archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages.bz2
archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages.bz2
archive.ubuntu.com_ubuntu_dists_jaunty_Release.gpg
archive.ubuntu.com_ubuntu_dists_jaunty_Release.txt
archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages.bz2
archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages.bz2
...  
```[B]

5. Copy to APT Lists Directory[/B]

 ```
$ chmod 644 *
$ bunzip2 *.bz2
$ for i in *.txt; do mv $i ${i%.txt}; done
$ sudo cp * /var/lib/apt/lists  
```[B]

6. Generate Links for Packages to be Upgraded[/B]

 ```
$ sudo apt-get upgrade --print-uris --yes | cut -d "'" -f 2 -s
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.16+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.16+nobinonly-0ubuntu0.9.04.1_all.deb)
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.16+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.16+nobinonly-0ubuntu0.9.04.1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.16+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.16+nobinonly-0ubuntu0.9.04.1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.16+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.16+nobinonly-0ubuntu0.9.04.1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.16+nobinonly-0ubuntu0.9.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.16+nobinonly-0ubuntu0.9.04.1_all.deb)
...  
```[B]

7. Generate Links for Packages to be Installed[/B]

For example I want to install sun-java6-jdk package.
 
```
$ sudo apt-get install --print-uris --yes sun-java6-jdk | cut -d "'" -f 2 -s
[http://archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.30ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.30ubuntu4_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-16-0ubuntu1.9.04_all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-16-0ubuntu1.9.04_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jdk_6-16-0ubuntu1.9.04_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jdk_6-16-0ubuntu1.9.04_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.21_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.21_all.deb)  
```[B]

8. Download and Install Packages[/B]

Download all the package that listed above in computer B. If you use DownThemAll!, set the renaming mask back to default, ***name*.*ext***. Copy all the packages to computer A and install them all by issuing this command.

 ```
$ sudo dpkg -i *.deb
``` 

That's it, I hope you have a save trip until this point too. After you downloaded all of your most wanted packages, you can build your own repository to help others that don't have Internet connection like you. I'll write a guide about it next time, *insyaa'allaah*.

---

