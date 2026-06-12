---
title: "Unable to install Google Chrome"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by thailandxi on 2013-06-18
I have downloaded the Chrome and run the command 

sudo dpkg -i google-chrome-stable_current_i386.deb

but failed, 

dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on gconf-service; however:
  Package gconf-service is not configured yet.
 google-chrome-stable depends on libgconf-2-4 (>= 2.31.1); however:
  Package libgconf-2-4 is not installed.
 google-chrome-stable depends on libstdc++6 (>= 4.6); however:
  Version of libstdc++6 on system is 4.5.2-8ubuntu4.
 google-chrome-stable depends on libx11-6 (>= 2:1.4.99.1); however:
  Version of libx11-6 on system is 2:1.4.2-1ubuntu3.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured


My Ubuntu version is 11.04

---

### Post by Frogs Hair on 2013-06-18
11.04 has reached end of life and the repository is closed .This may account for the dependency problem because there is no active repository to download the dependencies from.

---

### Post by vasa1 on 2013-06-18
It's worth looking at [http://googlechromereleases.blogspot.in/2013/06/stable-channel-update_17.html](http://googlechromereleases.blogspot.in/2013/06/stable-channel-update_17.html)

> The Stable channel has been updated to 28.0.1500.45 for Linux.

The minimum requirements for Linux have also been updated:

Ubuntu **12.04+**
Debian 7+
OpenSuSE 12.2+
Fedora Linux 17+

---

### Post by thailandxi on 2013-06-18
Thank you very much!

---

### Post by deadflowr on 2013-06-18
> **Frogs Hair said:**
> 11.04 has reached end of life and the repository is closed .This may account for the dependency problem because there is no active repository to download the dependencies from.

I don't even know if the latest chrome's needed dependencies are even available to use on natty.
Your options are thus
1) Backup your system and install a supported version of Ubuntu
2) Back up your files and switch to a different distribution
3) Scrap plans to install chrome
4) Risk it and try to find and install the needed dependencies
5) Switch your repos to the old-release repos, which undoubtedly will not have the needed dependencies anyway.

I highly recommend option #1.

---

### Post by thailandxi on 2013-06-18
I choose the third option. I removed Google Chrome because I updated Java and then Chrome blocked Java, but I don't know I can't install Chrome again, What a pity.  I will use Opera instead. Your other options are too difficult for me. Thank you

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by malangaman on 2013-06-18
I found this thread. After EOL repositories are moved to :
[http://old-releases.ubuntu.com]("http://old-releases.ubuntu.com") which can still be accessed if needed. Some computers will run best on the older Ubuntu distributions (non PAE, BIOS, not EUFI  and  if they have old Broadcom or Realtek IC controllers). I intend to keep many of my older machines on 10.04 indefinitely. I will do option 4 above.

---

### Post by deadflowr on 2013-06-18
> **ahallubuntu said:**
> The longer you continue to use 11.04, the worse it's going to get with other software having issues, too, and no more updates.  Sooner or later you'll need to upgrade.  Why not sooner to spare yourself more pain?

People tend to sit on natty and maverick because of unity and the switch to gnome3.
Which is why I suggested option #2 of changes to another distro.
Be it something like mint or family member like xubuntu or lubuntu.

As an aside, last week I was digging through my backups and found my old iso of maverick.
I decided to install it in a VM so I could test converting the repos to the old-release archives.
PITA.
You end up reloading apt-get update like ten times, and commenting out various lines in the sources.list, until finally it works. Error free.Sort of, not really sure if I'm getting the full maverick repos or some kind of quasi-built repo system. I know I don't have the partner repos or the extras repos. 
Not really worth the effort, and far easier just to upgrade to a support system.

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by Cheesemill on 2013-06-18
Even if you don't have a PAE enabled kernel you can install the non-PAE version of 12.04.

---

### Post by thailandxi on 2013-06-18
I downloaded Chrome of version 27 from the website Uptodown.com, and installed successfully.


> **ahallubuntu said:**
> The longer you continue to use 11.04, the worse it's going to get with other software having issues, too, and no more updates.  Sooner or later you'll need to upgrade.  Why not sooner to spare yourself more pain?

I am just a beginner, and don't know to upgrade Ubuntu, I'm afraid to have some problems if I upgrade Ubuntu. Thanks

---

### Post by vasa1 on 2013-06-18
> **thailandxi said:**
> I downloaded Chrome of version 27 from the website ....com ...
Never heard of that site.  Hope you stay safe.

---

### Post by stec2 on 2014-05-11
> **deadflowr said:**
> I don't even know if the latest chrome's needed dependencies are even available to use on natty.
Your options are thus
1) Backup your system and install a supported version of Ubuntu
2) Back up your files and switch to a different distribution
3) Scrap plans to install chrome
4) Risk it and try to find and install the needed dependencies
5) Switch your repos to the old-release repos, which undoubtedly will not have the needed dependencies anyway.


One more reliable option
6) Download version of Chrome which was the last one supported by your OLD ubuntu.
For example: for Ubuntu 10.04 last supported Chrome is v.27

[http://95.31.35.30/chrome/pool/main/g/google-chrome-stable/google-chrome-stable_27.0.1453.110-r202711_i386.deb](http://95.31.35.30/chrome/pool/main/g/google-chrome-stable/google-chrome-stable_27.0.1453.110-r202711_i386.deb)
[http://95.31.35.30/chrome/pool/main/g/google-chrome-stable/google-chrome-stable_27.0.1453.110-r202711_amd64.deb](http://95.31.35.30/chrome/pool/main/g/google-chrome-stable/google-chrome-stable_27.0.1453.110-r202711_amd64.deb)

More releases here:
[http://95.31.35.30/chrome/pool/main/g/google-chrome-stable/](http://95.31.35.30/chrome/pool/main/g/google-chrome-stable/)

---

