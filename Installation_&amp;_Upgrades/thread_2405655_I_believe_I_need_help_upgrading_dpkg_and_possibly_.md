---
title: "I believe I need help upgrading dpkg and possibly apt-get on 10.04 precise"
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by millerxcrunning on 2018-11-09
Hi everyone, 

I am trying to sudo apt-get update and then sudo apt-get dist-upgrade to 12.04 and possibly newer, but let's just get that far first! I just came from 8.04 hardy heron. 

I get the following message executing sudo apt-get dist-upgrade:

```
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  lzma (due to dpkg)
1139 upgraded, 646 newly installed, 86 to remove and 0 not upgraded.
Need to get 951MB of archives.
After this operation, 19.8MB of additional disk space will be used.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 
```

So, I then looked around the internet and found a possible workaround. I tried sudo apt-get install dpkg thinking I could upgrade dpkg this way. As far as I could tell, a person had quite the same experience and upgrading dpkg in this way worked for him. However, I got the following output when I ran sudo apt-get install dpkg:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libasound2: Breaks: libasound2-plugins (< 1.0.24) but 1.0.22-0ubuntu6 is to be installed
  libglib2.0-0: Breaks: gvfs (< 1.8) but 1.6.1-0ubuntu1build1 is to be installed
  libpango1.0-0: Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu2.2 is to be installed
  ppp: Breaks: network-manager (<= 0.8.0.999-1) but 0.8-0ubuntu3.3 is to be installed
       Breaks: network-manager-pptp (<= 0.8.0.999-1) but 0.8-0ubuntu3 is to be installed
E: Broken packages

```
The version of dpkg on my computer is: 

```
Debian `dpkg' package management program version 1.15.5.6ubuntu2 (i386).
```

I do not know... Is my issue perhaps needing a newer version of apt-get? My current version of apt-get is:

```
apt 0.7.25.3ubuntu9.17.1 for i386 compiled on Sep 23 2014 12:42:01
```

However, if this is the route I should take, I do not know how to update apt-get.

It should be noted, coming from 8.04 hardy heron, I went into /etc/apt/sources.list and modified the source to 

```
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted
```

and then updated and dist-upgraded. I cannot do-release-upgrade either, I should note.

Thank you so much for any insight you can provide me into this situation, or the meaning behind the output... especially of the dpkg!

---

### Post by Autodave on 2018-11-09
12.04 was too many releases ago to count.  You need to download a newer release and do a clean install after making sure that you backed up all import files to an external source first.

  	 	 	 	   Every 2 years, a long term service release is made.  18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.
  

Some specs on your machine may help us make some recommendations on which flavor of Ubuntu to install.  With the machine that old, you may not want full-blown Ubuntu because of the RAM and speed requirements.

---

### Post by coffeecat on 2018-11-09
The repositories for 10.04 Lucid Lynx have long been closed, the desktop version of 10.04 going end of life in May 2013, and the server version eol in April 2015. 12.04, Precise Pangolin, went end of life in April 2017. It is theoretically possible to upgrade your system, LTS to LTS, until you get to a supported version but that way lies a world of pain and frustration, and a high likelihood of you ending up with a broken system without much hope of rescuing it.

Please do yourself a huge favour by backing up your personal files and then making a fresh installation of something both currently supported and with the expectation of some years' worth of support. 16.04 or 18.04 would be your choice, bearing in mind that support for 14.04 ends in April of next year.

---

### Post by Impavidus on 2018-11-09
8.04, 10.04 and 12.04 are long dead, buried and reprocessed by fungi. If you want to play with old releases, feel free to do so, but you'll be on your own. This forum is to help people with real issues. If you don't want to play with old releases, try a fresh install of 16.04 or 18.04. We can provide help with that, if needed.

---

