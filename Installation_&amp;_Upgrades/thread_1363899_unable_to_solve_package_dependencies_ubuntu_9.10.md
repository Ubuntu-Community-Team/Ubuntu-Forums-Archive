---
title: "unable to solve package dependencies ubuntu 9.10"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by durga11 on 2009-12-25
Hi folks,
i had installed ubuntu 9.10 on my laptop one month back,while installing some of the packages, I am facing the  error.
when trying to install filght gear from ubuntu s/w centre

**Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

while reading through the forms related to this kind of error,
i tried the following -:

$sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

even in **synaptic package manager->Edit->Fix dependency error **is not showing any packages with dependecies

my sources.list is below

durga@durga-laptop:~$ cat /etc/apt/sources.list
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free #Medibuntu - Ubuntu 8.04 LTS "hardy heron"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free #Medibuntu (source) - Ubuntu 8.04 LTS "hardy heron"

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main 
deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) hardy main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse



Thanks in advance

---

### Post by mikewhatever on 2009-12-25
You have a lot of lines for Hardy Heron in your sources, while you are saying you are running Karmic. Furthermore, that can't be all of it. Try opening the file with gedit and copy/pase properly.

gedit /etc/apt/sources.list

---

### Post by durga11 on 2009-12-25
Hi ... thanks for the reply..
I didnt get u exactly,but i am pasting the output of the file

## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free #Medibuntu - Ubuntu 8.04 LTS "hardy heron"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free #Medibuntu (source) - Ubuntu 8.04 LTS "hardy heron"

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main 
deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) hardy main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

---

### Post by mikewhatever on 2009-12-25
Right, if that's the whole output, you are missing most of Karmic's repositories. Go to System->Admin->Software-Sources. under 'Download From' select 'other', and then click on 'Select the best server'. Let it run, and then post the content of sources.list again.

---

### Post by durga11 on 2009-12-25
I tried way u mentioned,
after selecting "select best server", and selecting all chk boxes for repositories, it downloaded the package information, but there is no install or download option. only revert and close buttons were there..

How can i install those packages....:confused:

---

### Post by durga11 on 2009-12-25
sorry,Another thing i missed out is that, after selecting Revert option.. it was showing that package info is out of date and prompting for new package info.then dowloading new package info.

---

### Post by mikewhatever on 2009-12-26
Just select a server and hit 'Close'. There is nothing to install there, and you'll be prompted to reload the package info, do it. Do not hit 'Revert'.

---

### Post by durga11 on 2009-12-26
I had done what u said


here is the output of sources.list

-------------------------------------------------------------------------------------
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free #Medibuntu - Ubuntu 8.04 LTS "hardy heron"
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free #Medibuntu (source) - Ubuntu 8.04 LTS "hardy heron"

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) hardy main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb [http://ubuntuarchive.hnsdc.com/](http://ubuntuarchive.hnsdc.com/) karmic main universe restricted multiverse
deb-src [http://ubuntuarchive.hnsdc.com/](http://ubuntuarchive.hnsdc.com/) karmic main universe restricted multiverse #Added by software-properties
#cricket
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) dapper main
-------------------------------------------------------------------------------------------------


now i am able to install packages. let me know if my ubuntu is fine with all the required packages installed, so that it wont cause any problems...

I had few queries
1. I am using clamav antivirus and it is working fine. what is the cmd to know the infected files. It was just showing the number of infected files and when given --remove , the infected files are removed.

2. I am intrested in games, how can i install free open source games which are not listed in ubuntu s/w centre

Thanks in advance

---

### Post by tommcd on 2009-12-26
Why do you have Hardy and Dapper repos in your sources.list if you are running Karmic? Was this a clean install of Karmic? Dapper reached EOL a long time ago.
I would try commenting out (i.e., put a # if front of) all the lines for Hardy and Dapper in your sources.list. I would also get the medibuntu repos for Karmic instead of Hardy:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then go to: system > administration > software sources, and check the boxes for the Karmic repos. Reload the repos when you are prompted. Your sources.list should only point to Karmic.
Also, use caution with those ppa repos. They have been problematic for a lot of people.

---

### Post by tommcd on 2009-12-26
For reference, here is my sources.list. I use the USA repos:
```

tom@ubuntu:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Beta i386 (20090929.2)]/ karmic main restricted

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Beta i386 (20090929.2)]/ karmic main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
tom@ubuntu:~$ 

```
NOTE: Comments were removed from the sources.list for brevity and clarity.

---

