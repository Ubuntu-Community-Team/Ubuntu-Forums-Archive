---
title: "wine messed up"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by wirate on 2009-12-30
I followed some instructions on a forum i do not remember and deleted some files. now when i do
```

sudo apt-get remove wine

```> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-liberation ttf-mscorefonts-installer cabextract winbind
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 55.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135509 files and directories currently installed.)
Removing wine ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing wine (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)
and when i do
```

sudo apt-get install wine

```> Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up wine (1.0.1-0ubuntu8) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing wine (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by wirate on 2009-12-30
8  ) became a smiley:P

---

### Post by MelDJ on 2009-12-30
have you tried sudo dpkg --configure -a

---

### Post by wirate on 2009-12-30
yes. no difference :(

---

### Post by wirate on 2009-12-31
I just discovered i cant install ANY software. help please

---

### Post by MelDJ on 2009-12-31
try sudo apt-get -f

---

### Post by wirate on 2009-12-31
how do i use this? typing

sudo apt-get -f

gives the manual. and typing

sudo apt-get -f wine

gives 

E:Invalid operation wine

---

### Post by MelDJ on 2009-12-31
i am sorry.
it should have been sudo apt-get install -f

---

### Post by wirate on 2009-12-31
still the same
> 
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up wine (1.0.1-0ubuntu8 ) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing wine (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by wirate on 2010-01-03
I wonder why only one person is responding

---

### Post by Mark Phelps on 2010-01-03
> **wirate said:**
> I wonder why only one person is responding

Probably because: (1) most of us do not use Wine -- it's more trouble than it's worth and it's not doing things "the Linux way".

And, (2), you did not post this in the Wine subforum.  

If you're going to whine about lack of support, at least TRY going to the right subforum first!

---

### Post by wirate on 2010-01-04
well i thought the problem was me deleting some files relating to the wine package and hence an installation problem so i posted it here. And I would be very happy if i could remove wine completely but i cant :(

---

