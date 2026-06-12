---
title: "Open office dependency  problem after upgrade"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nukie77 on 2010-04-12
I am having an apparent dependency probelm with open office after an upgrade to 10.04.  It looks like I have part oo 3.2, but 10.04 is expecting 3.1, but I'm just not sure.  apt-get update works fine, but here is what I get after I attempt an apt-get upgrade:

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libevent-execflow-perl: Depends: libanyevent-perl but it is not installed
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
                       Depends: openoffice.org-base-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
                         Depends: openoffice.org-base-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
E: Unmet dependencies. Try using -f.

```

I attempt an apt-get -f upgrade and after a confirmatory yes to a long list of upgrades I get this:

```

Fetched 216MB in 2min 50s (1,268kB/s)                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 285893 files and directories currently installed.)
Unpacking libanyevent-perl (from .../libanyevent-perl_5.240-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb (--unpack):
 trying to overwrite '/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl 0:1.02-0.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried simply removing openoffice, but that gave a similar error as the apt-get upgrade command.  Any suggestions?

---

### Post by nanog on 2010-04-12
You could try the configure and reconfigure commands in my sig. If you have an unmet dependency due to a broken or missing package these will fail. The dpkg error 1 is also often caused by a corrupt package in /var/cache/apt/archives/. 

Try this: 

```
sudo rm /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb && sudo apt-get update && sudo apt-get upgrade

```

---

### Post by nukie77 on 2010-04-12
here is the result.

```

sudo rm /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb && sudo apt-get update && sudo apt-get upgrade
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Get:1 http://us.archive.ubuntu.com lucid Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Get:2 http://us.archive.ubuntu.com lucid Release [57.2kB]
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates Release
Get:3 http://us.archive.ubuntu.com lucid/main Packages [1,380kB]
Get:4 http://us.archive.ubuntu.com lucid/restricted Packages [6,211B]
Get:5 http://us.archive.ubuntu.com lucid/main Sources [652kB]
Get:6 http://us.archive.ubuntu.com lucid/restricted Sources [3,774B]
Get:7 http://us.archive.ubuntu.com lucid/universe Packages [5,476kB]
Get:8 http://us.archive.ubuntu.com lucid/universe Sources [3,178kB]
Get:9 http://us.archive.ubuntu.com lucid/multiverse Packages [179kB]
Get:10 http://us.archive.ubuntu.com lucid/multiverse Sources [117kB]
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 11.0MB in 8s (1,307kB/s)                                                                                                                                       
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libevent-execflow-perl: Depends: libanyevent-perl but it is not installed
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
                       Depends: openoffice.org-base-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
                         Depends: openoffice.org-base-core (= 1:3.2.0-4ubuntu2) but 1:3.1.1-5ubuntu1.1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by nanog on 2010-04-13
Did you try this command:

dpkg --configure -a 


If it doesn't work then you could try to force removal:

sudo dpkg --force-remove-reinstreq -r libevent-execflow-perl

followed by:

sudo dpkg --configure -a

and/or

sudo apt-get update && sudo apt-get upgrade

---

### Post by nanog on 2010-04-13
I knew this sounded familiar:

[http://ubuntuforums.org/showthread.php?p=8907430](http://ubuntuforums.org/showthread.php?p=8907430)

If this is the same issue please comment on the bug to reopen it.

---

