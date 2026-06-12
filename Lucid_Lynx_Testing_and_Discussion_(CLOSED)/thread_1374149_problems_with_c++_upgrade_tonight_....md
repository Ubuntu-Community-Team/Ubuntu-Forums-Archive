---
title: "problems with c++ upgrade tonight ..."
date: 2010-01-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-01-06
This is the output of upgrade attempt...> Current status: 3 updates [+3].
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  cpp g++ gcc 
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 43.3kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main cpp 4:4.4.2-3ubuntu1 [36.8kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main gcc 4:4.4.2-3ubuntu1 [5066B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main g++ 4:4.4.2-3ubuntu1 [1440B]
Fetched 43.3kB in 0s (131kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 163087 files and directories currently installed.)
Preparing to replace cpp 4:4.4.1-1ubuntu2 (using .../cpp_4%3a4.4.2-3ubuntu1_amd64.deb) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Unpacking replacement cpp ...
Preparing to replace gcc 4:4.4.1-1ubuntu2 (using .../gcc_4%3a4.4.2-3ubuntu1_amd64.deb) ...
Removing old gcc doc directory.
Unpacking replacement gcc ...
Preparing to replace g++ 4:4.4.1-1ubuntu2 (using .../g++_4%3a4.4.2-3ubuntu1_amd64.deb) ...
Unpacking replacement g++ ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct
Setting up cpp (4:4.4.2-3ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Setting up gcc (4:4.4.2-3ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Setting up g++ (4:4.4.2-3ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 0 updates [-3].

---

### Post by LKjell on 2010-01-06
Looks like ok to me. I just notice I have some locale problems but still my LC_CTYPE is still set. You can try to use locale to see what is set on your computer. Should be LC_CTYPE="en_US.UTF-8"> locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

---

### Post by zika on 2010-01-06
It seems it did not have anything to do with c++... It went away as suddenly as it came... It went either with some upgrade or with fsck ... It kinda scared me...

---

