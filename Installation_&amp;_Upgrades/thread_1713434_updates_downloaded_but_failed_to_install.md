---
title: "updates downloaded but failed to install"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by sadiqdude on 2011-03-24
hello friends i am new to ubuntu.i installed 10.10 and then went to update manager and selected for update it downloaded all the required files but now while installing it is giving me an error.Which is some thing like this:

installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Segmentation fault
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Segmentation fault
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 118308 files and directories currently installed.)
Preparing to replace login 1:4.1.4.2-1ubuntu3 (using .../login_1%3a4.1.4.2-1ubuntu3.2_i386.deb) ...
Unpacking replacement login ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script killed by signal (Segmentation fault)
Errors were encountered while processing:
 man-db
Setting up login (1:4.1.4.2-1ubuntu3.2) ...
Setting up man-db (2.5.7-4) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script killed by signal (Segmentation fault)

---

### Post by sadiqdude on 2011-03-24
plz plz help me because of this i am not able update anything

---

### Post by Dutch70 on 2011-03-24
Try running this from a terminal...
```
dpkg --configure -a 
```

---

### Post by sadiqdude on 2011-06-05
thanks dude after executing 
dpkg --configure -a
my system was not responding it got hanged then i resatarted it now every thing is fine

---

### Post by Rgibbons on 2011-06-06
same problem here, but dpkg --configure -a didn't fix mine.

---

