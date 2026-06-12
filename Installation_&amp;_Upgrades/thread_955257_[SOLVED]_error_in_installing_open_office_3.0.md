---
title: "[SOLVED] error in installing open office 3.0"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by scotcella on 2008-10-22
Hi All,

I had OO.org 3.0 installed about two weeks ago with out any problems. I needed to install Java so I can enable to macros to work, and when I installed the Java thingy OO.org was completely removed. 

So installed OO again, following the instructions I used last time...I found on this [wesbite]("http://www.linuxpromagazine.com/online/blogs/productivity_sauce_dmitri_s_open_source_blend_of_productive_computing/installing_openoffice_org_3_0?blogbox") (it was a smooth installation)

An error came up..  which was the following but I dont know what it means.

Anyhelp appreciated!

```
ella@ella-laptop:~/OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration$ sudo dpkg -i *.deb
dpkg: regarding openoffice.org3.0-debian-menus_3.0-9354_all.deb containing openoffice.org-debian-menus:
 openoffice.org-core conflicts with openoffice.org-unbundled
  openoffice.org-debian-menus provides openoffice.org-unbundled and is to be installed.
dpkg: error processing openoffice.org3.0-debian-menus_3.0-9354_all.deb (--install):
 conflicting packages - not installing openoffice.org-debian-menus
Errors were encountered while processing:
 openoffice.org3.0-debian-menus_3.0-9354_all.deb

```

---

### Post by scotcella on 2008-10-22
Okay Update...

I thought I'd take everything off....

So I put in the terminal

```
sudo apt-get remove openoffice*.*
```

I extracted my download```


tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz
```

Then followed the commands

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS/
```
```

sudo dpkg -i *.deb
```

This gave me an error which now says:

```
Errors were encountered while processing:
 openoffice.org3
 openoffice.org3-base
 openoffice.org3-calc
 openoffice.org3-dict-en
 openoffice.org3-dict-es
 openoffice.org3-math
 openoffice.org3-writer
ella@ella-laptop:~/OOO300_m9_native_packed-1_en-US.9358/DEBS$
``` 

Any help appreciated!

---

### Post by Kowloon on 2008-10-22
I think you've missed one command.

cd OOO300_m9_native_packed-1_en-US.9358/DEBS/
cd desktop-integration
sudo dpkg -i *.deb

---

### Post by scotcella on 2008-10-22
Solved this....  refer to post [http://ubuntuforums.org/showthread.php?t=955375](http://ubuntuforums.org/showthread.php?t=955375)

---

