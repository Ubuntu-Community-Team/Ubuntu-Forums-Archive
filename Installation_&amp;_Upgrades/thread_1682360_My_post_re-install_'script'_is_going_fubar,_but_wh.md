---
title: "My post re-install 'script' is going fubar, but why?"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Tenebraxis on 2011-02-05
I want to repartition the hard drive my operating systems are on and I thought it might be a good idea to look for a way to automatically remove and and install the packages so it resembles the exact packages installed on my current system and overwrite my new /etc directory with my old one.

It's a bit crude but it seems like a good enough idea to me.
If anyone has a better idea, please feel free to share it ;)

I tested this with a package I don't have installed, firefox in this case.

I made a text file with the list of my currently installed packages with the following command:

```
dpkg -l | cut -d " " -f 3 | cat > oldpackagelist.txt
```

Then I installed firefox with *apt-get install firefox* and it installs **7** new packages.

```
apturl apturl-common firefox-branding python-webkit ubufox xul-ext-ubufox
```

I made a second text file with an updated package list:

```
dpkg -l | cut -d " " -f 3 | cat > newpackagelist.txt
```

And I run *diff* through these two text files and it comes up with a difference of **4** packages, this is obviously where things start to go wrong.

```
diff oldpackagelist.txt newpackagelist.txt | grep "[<>]" | sed "s/>/\t/g;s/<//g" | cut -d " " -f 2
```

Without grep, sed and cut I come up with the same list, it's just not formated right for apt-get to handle it. 
I could probably clean up that command a bit but it does the trick.

I went ahead and removed those packages but suddenly it wants to install 87 other packages as well.

```
apt-get remove apturl firefox-branding python-webkit ubufox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  akonadi-server apturl-kde exiv2 kdebase-runtime kdebase-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins kdesudo kdoctools kubuntu-debug-installer libakonadi-kabc4 libakonadi-kcal4
  libakonadi-kde4 libakonadi-kmime4 libakonadiprivate1 libattica0 libboost-program-options1.42.0 libclucene0ldbl libdbusmenu-qt2 libexiv2-6 libiodbc2 libkabc4 libkatepartinterfaces4 libkcal4 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkfile4 libkhtml5 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpimutils4 libkpty4 libkresources4
  libkrosscore4 libkrossui4 libktexteditor4 libkutils4 libmailtransport4 libmicroblog4 libnepomuk4 libnepomukquery4a libplasma3 libpolkit-qt-1-0 libqapt-runtime libqapt1 libqca2 libqt4-qt3support libraptor1 librasqal2 librdf0
  libreadline5 libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0 mysql-client-core-5.1 mysql-server-core-5.1 oxygen-icon-theme plasma-scriptengine-javascript python-kde4 qapt-batch
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
Suggested packages:
  djvulibre-bin hspell libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqca2-plugin-ossl libqca2-plugin-pkcs11 raptor-utils librdf-storage-postgresql librdf-storage-mysql librdf-storage-sqlite redland-utils
The following packages will be REMOVED:
  apturl firefox firefox-branding python-webkit ubufox xul-ext-ubufox
The following NEW packages will be installed:
  akonadi-server apturl-kde exiv2 kdebase-runtime kdebase-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdepim-runtime kdepimlibs-kio-plugins kdesudo kdoctools kubuntu-debug-installer libakonadi-kabc4 libakonadi-kcal4
  libakonadi-kde4 libakonadi-kmime4 libakonadiprivate1 libattica0 libboost-program-options1.42.0 libclucene0ldbl libdbusmenu-qt2 libexiv2-6 libiodbc2 libkabc4 libkatepartinterfaces4 libkcal4 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkfile4 libkhtml5 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpimutils4 libkpty4 libkresources4
  libkrosscore4 libkrossui4 libktexteditor4 libkutils4 libmailtransport4 libmicroblog4 libnepomuk4 libnepomukquery4a libplasma3 libpolkit-qt-1-0 libqapt-runtime libqapt1 libqca2 libqt4-qt3support libraptor1 librasqal2 librdf0
  libreadline5 libsolid4 libsoprano4 libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0 mysql-client-core-5.1 mysql-server-core-5.1 oxygen-icon-theme plasma-scriptengine-javascript python-kde4 qapt-batch
  shared-desktop-ontologies software-properties-kde soprano-daemon ttf-dejavu virtuoso-minimal virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common
0 upgraded, 87 newly installed, 6 to remove and 0 not upgraded.
Need to get 62.6MB/62.8MB of archives.
After this operation, 186MB of additional disk space will be used
```

That's obviously not the result I was looking for, and that brings me here.

Does anyone have an idea on what went wrong and maybe even on how I could do this in a way that doesn't have the exact opposite effect of what I want to do?

---

