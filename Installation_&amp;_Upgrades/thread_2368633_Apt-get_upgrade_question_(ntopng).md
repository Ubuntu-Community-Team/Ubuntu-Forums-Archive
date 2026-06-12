---
title: "Apt-get upgrade question (ntopng)"
date: 2017-08-13
forum: Installation &amp; Upgrades
---

### Post by dkraut on 2017-08-13
Hi All, I installed Ubuntu server 16.04 and then installed ntopng using instructions here [https://www.vultr.com/docs/how-to-install-ntopng-on-ubuntu-16-04](https://www.vultr.com/docs/how-to-install-ntopng-on-ubuntu-16-04)

This installs ntopng v2.3, but the latest ntopng version is v3.  I was told that simply running apt-get upgrade followed by apt-get update would upgrade ntopng to v3, but it doesn't.  [COLOR=#26282A][FONT=garamond]I also tried  sudo apt-get --only-upgrade install ntopng but [/FONT][/COLOR][COLOR=#26282A][FONT=garamond]it tells me "ntopng is already the newest version (2.2+dfsg1-1build1)"[/FONT][/COLOR]   

Is there any way to troubleshoot why this is not working as expected?   Thanks!

---

### Post by oldos2er on 2017-08-13
2.2+dfsg1-1build1 is the most recent version in the default repositories, so it is working as expected. And seeing as 16.04 is an LTS release, unless there is a serious security bug of some kind I wouldn't expect it to be updated anytime soon.

It looks like there is a nightly-builds repository at [http://packages.ntop.org/](http://packages.ntop.org/), or github [https://github.com/ntop/ntopng](https://github.com/ntop/ntopng)

---

### Post by vocx on 2017-08-13
> **dkraut said:**
> Hi All, I installed Ubuntu server 16.04 and then installed ntopng using instructions here [https://www.vultr.com/docs/how-to-install-ntopng-on-ubuntu-16-04](https://www.vultr.com/docs/how-to-install-ntopng-on-ubuntu-16-04)

This installs ntopng v2.3, but the latest ntopng version is v3.**  I was told that simply running apt-get upgrade followed by apt-get update** would upgrade ntopng to v3, but it doesn't.  [COLOR=#26282A][FONT=garamond]I also tried  sudo apt-get --only-upgrade install ntopng but [/FONT][/COLOR][COLOR=#26282A][FONT=garamond]it tells me "ntopng is already the newest version (2.2+dfsg1-1build1)"[/FONT][/COLOR]   

Is there any way to troubleshoot **why this is not working as expected?**   Thanks!
The commands work as expected. What you were told was wrong.

The command "sudo apt update" only refreshes the list of software available in the repositories. It does not actually install anything new.

The command "sudo apt upgrade" downloads and installs new versions of packages that are in the repositories. If there is a new version it will be installed, if there is no new version it will not be installed.

In Ubuntu the versions in the repositories are fixed, so in general you do not get new software this way, you only get a newer version of the package by upgrading your entire system, say, Ubuntu 16.04 to Ubuntu 17.04.

> **oldos2er said:**
> 2.2+dfsg1-1build1 is the most recent version in the default repositories, so it is working as expected. And seeing as 16.04 is an LTS release, unless there is a serious security bug of some kind I wouldn't expect it to be updated anytime soon.

It looks like there is a nightly-builds repository at [http://packages.ntop.org/](http://packages.ntop.org/), or github [https://github.com/ntop/ntopng](https://github.com/ntop/ntopng)

You can upgrade the package by installing the software from source. Another way is to install specially published .deb packages made by the developer, who maintain a personal package archive (PPA), or simply makes daily builds or something similar. This is what oldos2er suggests.

---

### Post by dkraut on 2017-08-13
Thanks for the info.  Using those links I just ran > 

wget [http://apt-stable.ntop.org/16.04/all/apt-ntop-stable.deb](http://apt-stable.ntop.org/16.04/all/apt-ntop-stable.deb)
dpkg -i apt-ntop-stable.deb

Rebooted, but I'm still showing ntop v2.3.  Am I missing something?  :-k

---

### Post by oldos2er on 2017-08-13
You're looking for [http://packages.ntop.org/apt-stable/16.04/x64/ntopng_3.0.170809-3232_amd64.deb](http://packages.ntop.org/apt-stable/16.04/x64/ntopng_3.0.170809-3232_amd64.deb)

I hope you understand the caveats about installing software from outside the default repositories.

Edit: And now that I look at it more closely, you may need [http://packages.ntop.org/apt-stable/16.04/all/ntopng-data_3.0.170809_all.deb](http://packages.ntop.org/apt-stable/16.04/all/ntopng-data_3.0.170809_all.deb) too.

---

### Post by dkraut on 2017-08-13
Thanks for the push in the right direction guys, I finally got v3 running.  :guitar:  ):P

---

### Post by usmany on 2018-04-16
Hi All,

See what i got when i tried to upgrade my ntopng

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ntopng-dbg : Depends: ntopng (= 2.2+dfsg1-1build1) but 3.3.180416-4303 is to be installed
E: Broken packages


Please need your help guys

---

### Post by induchoodan on 2018-06-05
stable builds are still buggy.....
I;ve spent hours , with the help of the web and knowledge-base to install this app, but in one or other stage of the installation, something would went wrong.
I haven't find such an unfriendly app in the installation process.... Never succeeded in any part of the installation... 
 In the latest release installation, i got the error message:
he following packages have unmet dependencies:
 ntopng-dbg : Depends: ntopng (= 2.2+dfsg1-1build1) but 3.3.180416-4303 is to be installed
E: Broken packages
Never find such an installation buggy app....
Totally incomplete and buggy application.

---

