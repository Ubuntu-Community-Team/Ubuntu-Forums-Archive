---
title: "[ASK] Tracking Package Dependencies in /var/cache/apt/archives"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by Malsasa on 2013-03-08
[COLOR=#333333]**Place: **[/COLOR]
[COLOR=#333333]/var/cache/apt/archives[/COLOR]

[COLOR=#333333]**Condition:**[/COLOR]
I have downloaded Netbeans after 20+ another applications (Eclipse, pbuilder, Quassel, etc.). There are **hundreds** of DEB there. I use Ubuntu 12.04 now.

[COLOR=#333333]**Problem:**[/COLOR]
I don't know which DEB dependencies in the cache **for Netbeans**. I can't distinct which are DEB dependencies for netbeans between those hundreds of DEB there.

[COLOR=#333333]**Wish: **[/COLOR]
I wanna track/filter/find DEB dependencies exactly for Netbeans (no others) from cache for doing **sudo dpkg -i *.deb** in my another PCs with same Ubuntu 12.04 version. Assume I have 30 PCs. I wanna install Netbeans offline, because no bandwidth for downloading again.

**What Makes I Brave to Wish:**
When I do **sudo dpkg -i *.deb** in a folder contains only Netbeans and DEB dependency packages, **dpkg** can track which package to install first, which to next, what's next, until end. It can track dependencies of many DEB **in one folder, in local directory**. And this type of installation is so useful in low internet bandwidth country like Indonesia, my country.

**What I Don't Wish:**
[LIST]
[*]Standard preparation mode for offline installation in case you can see this page for example: [http://www.tuxradar.com/answers/517](http://www.tuxradar.com/answers/517). I don't want that method because I have all I need in my cache, I don't want to download again. That waste my limited bandwidth.
[*]Method of **Aptoncd**. I wanna Netbeans only, not whole DEB of my cache.
[/LIST]

[FONT=system][COLOR=#333333]**Question: **[/COLOR][COLOR=#333333]
[/COLOR]How to do dependency tracking only for Netbeans (only Netbeans, not others) with all file name completely shown? It should complete and not only front name like *kde-standard* or *build-essential*. I wanna command result like this:

Dependencies for Netbeans in the /var/cache/apt/archives:
[/FONT][COLOR=#333333]anu_1.0_i386.deb [/COLOR]
[COLOR=#333333]ani_1.0_i386.deb [/COLOR]
[COLOR=#333333]ano_1.0_i386.deb[/COLOR]
[COLOR=#333333]
[/COLOR][COLOR=#333333]I know only **apt-cache**, **apt-rdepends**, **apt-offline**, and **dpkg -l packagename**. Only them. I have read some documentations like dpkg manpage, apt-offline manpage, [a webupd8 page]("http://www.webupd8.org/2009/11/get-list-of-packages-and-dependencies.html"), [a debianadmin manual]("http://www.debian-administration.org/article/Offline_Package_Management_for_APT"), and more. All not satisfy my curiosity. Only **apt-cache depends packagename** that almost perfectly suite my wish. Any solution from you all? Thank you before.[/COLOR]

[COLOR=#333333]Respect from Indonesia.[/COLOR]

---

### Post by Malsasa on 2013-03-09
It was 23 hours after post :) Any suggestion?

---

### Post by tgalati4 on 2013-03-09
On 12.10, netbeans looks like a clean package:

tgalati4@Mint14-Extensa ~/Desktop $ apt-cache search netbeans
gcj-4.7-source - GCJ java sources for use in IDEs like eclipse and netbeans
gcj-4.6-source - GCJ java sources for use in IDEs like eclipse and netbeans
libbeansbinding-java - Beans Binding API (library)
libbeansbinding-java-doc - Beans Binding API (documentation)
libnb-absolutelayout-java - Java LayoutManager to allow placement in absolute positions
libnb-apisupport3-java - Common NetBeans Platform Development Related Libraries for NetBeans
libnb-ide14-java - Common Integrated Development Environment Libraries for NetBeans
libnb-java5-java - Common Java Related Libraries for NetBeans
libnb-javaparser-java - Parser for the Java language which is good for use in tools
libnb-org-openide-modules-java - Utility classes for modules from the NetBeans Platform
libnb-org-openide-util-java - Utility classes from the NetBeans Platform
libnb-org-openide-util-lookup-java - Utility lookup classes from the NetBeans Platform
libnb-platform-devel-java - Build harness for NetBeans Platform
libnb-platform13-java - NetBeans Platform for building rich desktop applications in Java
libnb-platform13-java-doc - NetBeans Platform javadoc
libnetbeans-cvsclient-java - NetBeans CVS Client library
libsezpoz-java - Lightweight library for modular service lookups
libsezpoz-java-doc - Documentation for SezPoz
libswing-layout-java - Extensions to Swing layout
libswing-layout-java-doc - Extensions to Swing layout - contains Javadoc API documentation
**netbeans - Extensible Java IDE**
python-envisage - Extensible Application Framework
python-envisagecore - Extensible Application Framework

tgalati4@Mint14-Extensa ~/Desktop $ apt-cache depends netbeans
netbeans
  Depends: libnb-platform13-java
 |Depends: openjdk-6-jdk
 |Depends: <java6-sdk>
    openjdk-6-jdk
    default-jdk
    openjdk-7-jdk
  Depends: <java7-sdk>
    default-jdk
  Depends: libnb-ide14-java
  Depends: libnb-java5-java
  Depends: libnb-apisupport3-java
  Conflicts: <netbeans-ide>
  Conflicts: <netbeans-ide:i386>
  Conflicts: <netbeans5.5>
  Conflicts: <netbeans5.5:i386>
  Replaces: <netbeans-ide>
    netbeans
  Replaces: <netbeans-ide:i386>
  Replaces: <netbeans5.5>
  Replaces: <netbeans5.5:i386>

So, take machine #1, delete /var/cache/archives/*.* using:

```
sudo apt-get clean
```

Verify that the cache is empty.  Now install netbeans and any other packages that you need for your build/development environment.

Make a list of the packages in /var/cache/archives and copy them to a local project directory.  Rsync that project directory to the other machines and use a dpkg script to install.

---

### Post by andrewsomething on 2013-03-19
I think you might want to take a closer look at apt-offline. It can pull the contents from a cache directory instead of re-downloading them.

On the off-line machine, run:

```
sudo apt-offline set --install-packages netbeans -- ~/apt-offline.sig

```
Then copy the apt-offline.sig file to the machine that has the packages in cache directory and run:

```
apt-offline get --cache-dir='/var/cache/apt/archives' apt-offline.sig

```
From apt-offline's manpage:

```
       -s, --cache-dir DIR_NAME
                 Look for data in the cache before  downloading  it  from  the
                 internet. If you are on a Debian box, you would want to spec&#8208;
                 ify /var/cache/apt/archives here. If the data is  not  avail&#8208;
                 able  in the cache, the downloaded data is also copied to the
                 cache.
```

---

