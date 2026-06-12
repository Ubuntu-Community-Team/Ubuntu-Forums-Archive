---
title: "LC / Locales issues on Ubuntu 14.04 server"
date: 2015-03-10
forum: Installation &amp; Upgrades
---

### Post by ubu_Leno on 2015-03-10
Hello

I am setting up and Ubuntu server on a VPS.  I am having problem with with locale.  When I run commands like apt-gt or adduser I get errors like below

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_TIME = "en_IE.UTF-8",
    LC_MONETARY = "en_IE.UTF-8",
    LC_COLLATE = "C",
    LC_ADDRESS = "en_IE.UTF-8",
    LC_TELEPHONE = "en_IE.UTF-8",
    LC_NAME = "en_IE.UTF-8",
    LC_MEASUREMENT = "en_IE.UTF-8",
    LC_IDENTIFICATION = "en_IE.UTF-8",
    LC_NUMERIC = "en_IE.UTF-8",
    LC_PAPER = "en_IE.UTF-8",
    LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package locales.
```

I had this problems before on a debian server and resolved it by doing 

```
apt-get purge locales
apt-get install locales
dpkg-reconfigure locales
```

But when I try this on Ubuntu it fails and the errors persist like this

```
# dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = (unset),
    LC_PAPER = "en_IE.UTF-8",
    LC_ADDRESS = "en_IE.UTF-8",
    LC_MONETARY = "en_IE.UTF-8",
    LC_NUMERIC = "en_IE.UTF-8",
    LC_TELEPHONE = "en_IE.UTF-8",
    LC_IDENTIFICATION = "en_IE.UTF-8",
    LC_COLLATE = "C",
    LC_MEASUREMENT = "en_IE.UTF-8",
    LC_TIME = "en_IE.UTF-8",
    LC_NAME = "en_IE.UTF-8",
    LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
```


Can any persons recommend a solution or is this something that can be ignore?

---

### Post by slickymaster on 2015-03-10
Can you please post back the output you get when in a terminal you run```
locale
```

---

### Post by ubu_Leno on 2015-03-10
```
# locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB.UTF-8
LANGUAGE=
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC=en_IE.UTF-8
LC_TIME=en_IE.UTF-8
LC_COLLATE=C
LC_MONETARY=en_IE.UTF-8
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER=en_IE.UTF-8
LC_NAME=en_IE.UTF-8
LC_ADDRESS=en_IE.UTF-8
LC_TELEPHONE=en_IE.UTF-8
LC_MEASUREMENT=en_IE.UTF-8
LC_IDENTIFICATION=en_IE.UTF-8
LC_ALL=


```

---

### Post by slickymaster on 2015-03-10
Generate the missing locale```
sudo locale-gen en_GB.UTF-8
```Afterwards reconfigure locales```
sudo dpkg-reconfigure locales
```

---

### Post by ubu_Leno on 2015-03-10
That got rid of some of the messages but still getting one for LC_ALL

```
# locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB.UTF-8
LANGUAGE=
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC=en_IE.UTF-8
LC_TIME=en_IE.UTF-8
LC_COLLATE=C
LC_MONETARY=en_IE.UTF-8
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER=en_IE.UTF-8
LC_NAME=en_IE.UTF-8
LC_ADDRESS=en_IE.UTF-8
LC_TELEPHONE=en_IE.UTF-8
LC_MEASUREMENT=en_IE.UTF-8
LC_IDENTIFICATION=en_IE.UTF-8
LC_ALL=

```

---

### Post by slickymaster on 2015-03-10
Let's solve that then, by adding it to your **/etc/default/locale** file. Again in terminal:```
sudo nano /etc/default/locale
```With the file opened in edit mode add ```
LC_ALL=en_GB.UTF-8
```Save and close the file and check again.

---

### Post by ubu_Leno on 2015-03-10
/etc/default/locale  did not exist so I vi'd it and added the line as you suggested.

Giving the same results

```
# locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_GB.UTF-8
LANGUAGE=
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC=en_IE.UTF-8
LC_TIME=en_IE.UTF-8
LC_COLLATE=C
LC_MONETARY=en_IE.UTF-8
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER=en_IE.UTF-8
LC_NAME=en_IE.UTF-8
LC_ADDRESS=en_IE.UTF-8
LC_TELEPHONE=en_IE.UTF-8
LC_MEASUREMENT=en_IE.UTF-8
LC_IDENTIFICATION=en_IE.UTF-8
LC_ALL=


```

---

### Post by slickymaster on 2015-03-10
> **ubu_Leno said:**
> /etc/default/locale  did not exist so I vi'd it and added the line as you suggested.<--snip-->

[/CODE]
That's weird. Assuming you're using bash, try to add it to your **.bashrc** file```
export LC_ALL="en_GB.UTF-8"
```If that still fails to do it, try reinstalling the package```
sudo apt-get install --reinstall language-pack-en-base
```

---

### Post by ubu_Leno on 2015-03-10
the export fails by error:

```
# export LC_ALL="en_GB.UTF-8"
-bash: warning: setlocale: LC_ALL: cannot change locale (en_GB.UTF-8)
```

But the other look to work

```
# apt-get install --reinstall language-pack-en-base
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following extra packages will be installed:
  language-pack-en
The following NEW packages will be installed:
  language-pack-en language-pack-en-base
0 upgraded, 2 newly installed, 0 to remove and 30 not upgraded.
Need to get 474 kB of archives.
After this operation, 4,329 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main language-pack-en-base all 1:14.04+20150219 [472 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main language-pack-en all 1:14.04+20150219 [1,828 B]
Fetched 474 kB in 0s (685 kB/s)        
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package language-pack-en-base.
(Reading database ... 13216 files and directories currently installed.)
Preparing to unpack .../language-pack-en-base_1%3a14.04+20150219_all.deb ...
Unpacking language-pack-en-base (1:14.04+20150219) ...
Selecting previously unselected package language-pack-en.
Preparing to unpack .../language-pack-en_1%3a14.04+20150219_all.deb ...
Unpacking language-pack-en (1:14.04+20150219) ...
Setting up language-pack-en (1:14.04+20150219) ...
Setting up language-pack-en-base (1:14.04+20150219) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
```
```
# locale
LANG=en_GB.UTF-8
LANGUAGE=
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
LC_ALL=en_GB.UTF-8


```

Am I correct in saying, I could have skipped all other steps and just done final one?

---

### Post by slickymaster on 2015-03-10
Theoretically, either the solution proposed in [post #4]("http://ubuntuforums.org/showthread.php?t=2268614&p=13242719&viewfull=1#post13242719") or ultimately in [post #6]("http://ubuntuforums.org/showthread.php?t=2268614&p=13242728&viewfull=1#post13242728") should have worked. As it turned out, and due to the fact that you were missing the **/etc/default/locale** file, the solution was in fact to reinstall the language-pack-en-base package.

Anyway, what it matters is that you're all set up now with no errors. Please don't forget to mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

