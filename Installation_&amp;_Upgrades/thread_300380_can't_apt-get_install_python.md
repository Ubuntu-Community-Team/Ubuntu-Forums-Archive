---
title: "can't apt-get install python"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by cotn on 2006-11-15
Hi,

This has been a week full of problems and could fix everything except the following issue. I tried, searched and tried.. but this nasty thing just won't go away... 

When I try to install Python2.4 I get the folloing error:

```

sudo apt-get install python2.4
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  python2.4-doc python2.4-profiler
The following packages will be upgraded:
  python2.4
1 upgraded, 0 newly installed, 0 to remove and 135 not upgraded.
14 not fully installed or removed.
Need to get 0B/3497kB of archives.
After unpacking 1880kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 65894 files and directories currently installed.)
Preparing to replace python2.4 2.4.1-0 (using .../python2.4_2.4.1-2_i386.deb) ...
Unpacking replacement python2.4 ...
dpkg: error processing /var/cache/apt/archives/python2.4_2.4.1-2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/ConfigParser.py', which is also in package python2.4-minimal
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Compiling python modules in /usr/lib/python2.4 ...
Compiling optimized python modules in /usr/lib/python2.4 ...
Errors were encountered while processing:
 /var/cache/apt/archives/python2.4_2.4.1-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@magnetbox:/media/harddisk1/muziek$ sudo apt-get install python2.4-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python2.4-dev: Depends: python2.4 (= 2.4.1-2) but 2.4.1-0 is to be installed
  python2.4-examples: Depends: python2.4 (>= 2.4.1-2) but 2.4.1-0 is to be installed
  python2.4-gdbm: Depends: python2.4 (= 2.4.1-2) but 2.4.1-0 is to be installed
  python2.4-tk: Depends: python2.4 (= 2.4.1-2) but 2.4.1-0 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

When I try to remove 'webmin' (just want to get rid of it) or try to intall ruby (want to have it :)) then I get Python dependencie issues. So I think Pyton is half broken....


my sources list

```

deb http://http.us.debian.org/debian stable main contrib non-free
#deb http://download.videolan.org/pub/videolan/debian sarge main
#deb-src http://download.videolan.org/pub/videolan/debian sarge main
## Ubuntu Hoary packages
## The following lines pertain to supported packages:
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## The following lines pertain to security updates:
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

```


sudo apt-get -f install python2.4 doesn't work also.

Can somebody help please ?

Thanks in advance,

---

### Post by raul_ on 2006-11-15
The errors are pretty self explanatory. Try to install with aptitude instead of apt-get, or even synaptic. that should take care of dependency problems

---

### Post by cotn on 2006-11-15
Whell I have tried it with aptitude, and also he can't fix it. I get the same error's. 
I also understand the error's: 

Except this part. Wich is the problem: 
He is trying to overwite ConfigParse.py which is also in package python2.4-minimal. 
Why is it? Why is it bothering him..? What causes it? How did it happen? If I knew I maybe could do something about it.

```

dpkg: error processing /var/cache/apt/archives/python2.4_2.4.1-2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/ConfigParser.py', which is also in package python2.4-minimal

```

---

### Post by raul_ on 2006-11-15
If it happened to me i would go with a clean install, that means removing python completely and then installing it again (with synaptic just to keep track of the packages). There seems to be a conflict with those 2 packages but i'm not sure. Try a clean install and then tell me the results :)

EDIT: i also noted that u're using hoary. Unless you have a damn good reason i would suggest updating to dapper. Some packages may not work with hoary and dapper has a lot of big fixes. but it's up to you

---

### Post by cotn on 2006-11-16
Yup, I wan't to do an upgrade but therefore I need python to be stable.

See my weird list of errors

```

root@magnetbox:~ # sudo apt-remove python
sudo: apt-remove: command not found
root@magnetbox:~ # sudo apt-get remove python
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  bicyclerepair: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  bittorrent: Depends: python (< 2.5) but it is not going to be installed
              Depends: python (>= 2.4) but it is not going to be installed
  fetchmailconf: Depends: python (>= 2.1) but it is not going to be installed
  hal-device-manager: Depends: python (>= 2.4) but it is not going to be install
                      Depends: python (< 3) but it is not going to be installed
  hwdb-client: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-adns: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-apt: Depends: python (< 2.5) but it is not going to be installed
              Depends: python (>= 2.4) but it is not going to be installed
  python-cddb: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-clientcookie: Depends: python (>= 2.4) but it is not going to be instal
                       Depends: python (< 2.5) but it is not going to be install
  python-crypto: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-egenix-mxproxy: Depends: python (< 2.5) but it is not going to be insta
                         Depends: python (>= 2.4) but it is not going to be inst
  python-egenix-mxstack: Depends: python (< 2.5) but it is not going to be insta
                         Depends: python (>= 2.4) but it is not going to be inst
  python-egenix-mxtexttools: Depends: python (< 2.5) but it is not going to be i
                             Depends: python (>= 2.4) but it is not going to be
  python-egenix-mxtools: Depends: python (< 2.5) but it is not going to be insta
                         Depends: python (>= 2.4) but it is not going to be inst
  python-eunuchs: Depends: python (< 2.5) but it is not going to be installed
                  Depends: python (>= 2.4) but it is not going to be installed
  python-examples: Depends: python (>= 2.4) but it is not going to be installed
                   Depends: python (< 2.5) but it is not going to be installed
  python-gadfly: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-gd: Depends: python (< 2.5) but it is not going to be installed
             Depends: python (>= 2.4) but it is not going to be installed
  python-gdbm: Depends: python (>= 2.4) but it is not going to be installed
               Depends: python (< 2.5) but it is not going to be installed
  python-gdchart: Depends: python (>= 2.4) but it is not going to be installed
                  Depends: python (< 2.5) but it is not going to be installed
  python-genetic: Depends: python (< 2.5) but it is not going to be installed
                  Depends: python (>= 2.4) but it is not going to be installed
  python-geoip: Depends: python (< 2.5) but it is not going to be installed
                Depends: python (>= 2.4) but it is not going to be installed
  python-glade2: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-gnome2: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-gnupginterface: Depends: python (< 2.5) but it is not going to be insta
                         Depends: python (>= 2.4) but it is not going to be inst
  python-gst: Depends: python (< 2.5) but it is not going to be installed
              Depends: python (>= 2.4) but it is not going to be installed
  python-gtk2: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-htmlgen: Depends: python (>= 2.4) but it is not going to be installed
                  Depends: python (< 2.5) but it is not going to be installed
  python-htmltmpl: Depends: python (>= 2.4) but it is not going to be installed
                   Depends: python (< 2.5) but it is not going to be installed
  python-id3lib: Depends: python (>= 2.4) but it is not going to be installed
                 Depends: python (< 2.5) but it is not going to be installed
  python-imaging: Depends: python (< 2.5) but it is not going to be installed
                  Depends: python (>= 2.4) but it is not going to be installed
  python-imaging-sane: Depends: python (< 2.5) but it is not going to be install
                       Depends: python (>= 2.4) but it is not going to be instal
  python-jabber: Depends: python (>= 2.4) but it is not going to be installed
                 Depends: python (< 2.5) but it is not going to be installed
  python-kjbuckets: Depends: python (< 2.5) but it is not going to be installed
                    Depends: python (>= 2.4) but it is not going to be installed
  python-ldap: Depends: python (>= 2.4) but it is not going to be installed
               Depends: python (< 2.5) but it is not going to be installed
  python-musicbrainz: Depends: python (>= 2.4) but it is not going to be install
                      Depends: python (< 2.5) but it is not going to be installe
  python-mysqldb: Depends: python (>= 2.4) but it is not going to be installed
                  Depends: python (< 2.5) but it is not going to be installed
  python-netcdf: Depends: python (>= 2.4) but it is not going to be installed
                 Depends: python (< 2.5) but it is not going to be installed
  python-newt: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-numarray: Depends: python (>= 2.4) but it is not going to be installed
                   Depends: python (< 2.5) but it is not going to be installed
  python-numeric: Depends: python (< 2.5) but it is not going to be installed
                  Depends: python (>= 2.4) but it is not going to be installed
  python-osd: Depends: python (>= 2.4) but it is not going to be installed
              Depends: python (< 2.5) but it is not going to be installed
  python-pam: Depends: python (< 2.5) but it is not going to be installed
              Depends: python (>= 2.4) but it is not going to be installed
  python-parted: Depends: python (>= 2.4) but it is not going to be installed
                 Depends: python (< 2.5) but it is not going to be installed
  python-pexpect: Depends: python (>= 2.4) but it is not going to be installed
                  Depends: python (< 2.5) but it is not going to be installed
  python-pgsql: Depends: python (>= 2.4) but it is not going to be installed
                Depends: python (< 2.5) but it is not going to be installed
  python-pisock: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-pqueue: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-pyao: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-pylibacl: Depends: python (< 2.5) but it is not going to be installed
                   Depends: python (>= 2.4) but it is not going to be installed
  python-pyogg: Depends: python (< 2.5) but it is not going to be installed
                Depends: python (>= 2.4) but it is not going to be installed
  python-pyopenssl: Depends: python (< 2.5) but it is not going to be installed
                    Depends: python (>= 2.4) but it is not going to be installed
  python-pyorbit: Depends: python (< 2.5) but it is not going to be installed
                  Depends: python (>= 2.4) but it is not going to be installed
  python-pyvorbis: Depends: python (< 2.5) but it is not going to be installed
                   Depends: python (>= 2.4) but it is not going to be installed
  python-pyxattr: Depends: python (< 2.5) but it is not going to be installed
                  Depends: python (>= 2.4) but it is not going to be installed
  python-reportlab: Depends: python (< 2.5) but it is not going to be installed
                    Depends: python (>= 2.4) but it is not going to be installed
  python-simpletal: Depends: python (>= 2.4) but it is not going to be installed
                    Depends: python (< 2.5) but it is not going to be installed
  python-soappy: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-sqlite: Depends: python (< 2.5) but it is not going to be installed
                 Depends: python (>= 2.4) but it is not going to be installed
  python-stats: Depends: python (< 2.5) but it is not going to be installed
                Depends: python (>= 2.4) but it is not going to be installed
  python-syck: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-tk: Depends: python (>= 2.4) but it is not going to be installed
             Depends: python (< 2.5) but it is not going to be installed
  python-unit: Depends: python (< 2.5) but it is not going to be installed
               Depends: python (>= 2.4) but it is not going to be installed
  python-xdg: Depends: python (< 2.5) but it is not going to be installed
              Depends: python (>= 2.4) but it is not going to be installed
  python-xml: Depends: python (>= 2.4) but it is not going to be installed
              Depends: python (< 2.5) but it is not going to be installed
  python-xmpp: Depends: python (>= 2.4) but it is not going to be installed
               Depends: python (< 2.5) but it is not going to be installed
  python2.4-examples: Depends: python2.4 (>= 2.4.1-2) but 2.4.1-0 is to be insta
  python2.4-gdbm: Depends: python2.4 (= 2.4.1-2) but 2.4.1-0 is to be installed
  python2.4-tk: Depends: python2.4 (= 2.4.1-2) but 2.4.1-0 is to be installed
  update-manager: Depends: python but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a 

```

---

### Post by cotn on 2006-11-16
I tried it with synaptic:

And this is what I get.
```

Reading package lists... Done
Building dependency tree... Done
python is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python-gtk2: Depends: python2.3-gtk2 (= 2.6.1-2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Omg I think it get's more messier now....

---

