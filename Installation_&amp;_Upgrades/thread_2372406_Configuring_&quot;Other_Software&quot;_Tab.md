---
title: "Configuring &quot;Other Software&quot; Tab"
date: 2017-09-25
forum: Installation &amp; Upgrades
---

### Post by SMButler on 2017-09-25
sudo ap-get updae is reporting some warnings.  What changes do I need to make to the Other Software tab to resolve these?

I'm running Ubuntu 16.04

The following entries are check marked:
```
Canonical Partners
Canonical Partners (Source Code)
[http://download.ebz.epson.net/dsc/op/stable/debian/](http://download.ebz.epson.net/dsc/op/stable/debian/) lsb3.2 main
[http://archive.getdeb.net/ubunu](http://archive.getdeb.net/ubunu) xenial-getdeb apps
[http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
[http://ppa.launchpad.net/inaddy/lp1415880ubuntu](http://ppa.launchpad.net/inaddy/lp1415880ubuntu) vivid main
[http://ppa.launchpad.net/rosco2/backports/ubuntu](http://ppa.launchpad.net/rosco2/backports/ubuntu) xenial main
```

The following are not checked marked:
```
[http://ppa.launchpad.net/inaddy/lp1415880ubuntu](http://ppa.launchpad.net/inaddy/lp1415880ubuntu) vivid main (Source Code)
[http://ppa.launchpad.net/rosco2/backports/ubuntu](http://ppa.launchpad.net/rosco2/backports/ubuntu) xenial main (Source Code)
[http://ppa.launchpad.net/subsurface/subsurface-daily/ubuntu](http://ppa.launchpad.net/subsurface/subsurface-daily/ubuntu) xenial main
[http://ppa.launchpad.net/subsurface/subsurface-daily/ubuntu](http://ppa.launchpad.net/subsurface/subsurface-daily/ubuntu) xenial main (Source Code)
```

```
steve@stevelaptop:~$ sudo apt-get update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                                                                                                                                  
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                                                                                                                                                  
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease                                                                                                                                          
Ign:6 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid InRelease                                                                    
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                                                                                
Ign:8 [http://download.ebz.epson.net/dsc/op/stable/debian](http://download.ebz.epson.net/dsc/op/stable/debian) lsb3.2 InRelease                                           
Hit:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease                                                                                            
Hit:11 [http://download.ebz.epson.net/dsc/op/stable/debian](http://download.ebz.epson.net/dsc/op/stable/debian) lsb3.2 Release                                                                                                         
Hit:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security InRelease                                                                                                             
Hit:14 [http://ppa.launchpad.net/rosco2/backports/ubuntu](http://ppa.launchpad.net/rosco2/backports/ubuntu) xenial InRelease                      
Hit:9 [http://screenshots.getdeb.net](http://screenshots.getdeb.net) xenial-getdeb InRelease
Ign:15 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid Release          
Ign:16 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 Packages
Ign:17 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main i386 Packages
Ign:18 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main all Packages
Ign:19 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en_US
Ign:20 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en
Ign:21 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 DEP-11 Metadata
Ign:22 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main DEP-11 64x64 Icons
Ign:16 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 Packages
Ign:17 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main i386 Packages
Ign:18 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main all Packages
Ign:19 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en_US
Ign:20 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en
Ign:21 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 DEP-11 Metadata
Ign:22 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main DEP-11 64x64 Icons
Ign:16 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 Packages
Ign:17 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main i386 Packages
Ign:18 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main all Packages
Ign:19 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en_US
Ign:20 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en
Ign:21 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 DEP-11 Metadata
Ign:22 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main DEP-11 64x64 Icons
Ign:16 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 Packages
Ign:17 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main i386 Packages
Ign:18 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main all Packages
Ign:19 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en_US
Ign:20 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en
Ign:21 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 DEP-11 Metadata
Ign:22 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main DEP-11 64x64 Icons
Ign:16 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 Packages
Ign:17 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main i386 Packages
Ign:18 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main all Packages
Ign:19 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en_US
Ign:20 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en
Ign:21 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 DEP-11 Metadata
Ign:22 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main DEP-11 64x64 Icons
Err:16 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 Packages
  403  Forbidden
Ign:17 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main i386 Packages
Ign:18 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main all Packages
Ign:19 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en_US
Ign:20 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main Translation-en
Ign:21 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main amd64 DEP-11 Metadata
Ign:22 [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu) vivid/main DEP-11 64x64 Icons
Reading package lists... Done
W: Target Sources (universe/source/Sources) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:42
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: [http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg:](http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg:) Signature by key E5220FB7014D0FBDA50DFC2BE5E86C008AA65D56 uses weak digest algorithm (SHA1)
W: The repository 'http://ppa.launchpad.net/inaddy/lp1415880/ubuntu vivid Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/inaddy/lp1415880/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/inaddy/lp1415880/ubuntu/dists/vivid/main/binary-amd64/Packages)  403  Forbidden
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Sources (universe/source/Sources) is configured multiple times in /etc/apt/sources.list:5 and /etc/apt/sources.list:42
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:40
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:41
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:4 and /etc/apt/sources.list:46
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:50
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:30 and /etc/apt/sources.list:68
```

---

### Post by Bucky Ball on 2017-09-25
Please post the output of this file in its entirety and between code tags (see my signature for how to create those).

```
nano /etc/apt/sources.list
```

You have a 'dog's breakfast' there in that file with duplicate entries and old Vivid entries for dead and duplicated repos. Needs cleaning up. Also looks like you've manually added some PPAs. You do this at your own risk and Canonical/Ubuntu take no responsibility for the reliability, stability or security of such repos.

---

### Post by ajgreeny on 2017-09-25
You appear to have a load of vivid repos in your sources.list file that should not be there at all now as vivid (15.04) lost its support a long time ago, Feb 2016.

Have you upgraded to 16.04 from a previous version of Ubuntu?

---

