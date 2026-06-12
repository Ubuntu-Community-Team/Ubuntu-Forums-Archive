---
title: "Can't install google chrome on 11.04"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by kokusayb on 2011-08-17
I attempted to install Google Chrome on Ubuntu 11.04 after downloading it using Ubuntu Software Center but th[FONT=Verdana]e loading wheel on USC just spins around and around without end.

Attempting to install from the command line using this command:

[/FONT]"sudo dpkg -i google-chrome-stable_current_i386.deb"
[FONT=Verdana]gets me this:

dpkg: error processing google-chrome-stable_current_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 google-chrome-stable_current_i386.deb

When I try opening Synaptic to install it I get this message:

E: Type '--2011-06-27' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/FONT][FONT=Verdana]Any ideas??[/FONT]
[LEFT]
[/LEFT]

---

### Post by infamous-online on 2011-08-17
> **kokusayb said:**
> I attempted to install Google Chrome on Ubuntu 11.04 after downloading it using Ubuntu Software Center but th[FONT=Verdana]e loading wheel on USC just spins around and around without end.

Attempting to install from the command line using this command:

[/FONT]"sudo dpkg -i google-chrome-stable_current_i386.deb"
[FONT=Verdana]gets me this:

dpkg: error processing google-chrome-stable_current_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 google-chrome-stable_current_i386.deb

When I try opening Synaptic to install it I get this message:

E: Type '--2011-06-27' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/FONT][FONT=Verdana]Any ideas??[/FONT]
[LEFT]
[/LEFT]

I always downloaded it from google itself instead of synaptic, because it finds all the dependencies and installs them so mark it for complete removal and try the other method and see if that helps.

---

### Post by valantis on 2011-08-17
> **infamous-online said:**
> I always downloaded it from google itself instead of synaptic, because it finds all the dependencies and installs them so mark it for complete removal and try the other method and see if that helps.
Download it from chrome home page then don't run it from your browser , go to downloads and click the file.
the pacage manager will startup and it make the installation for you just give the root password.

---

### Post by MARP1961 on 2011-08-17
Before right clicking the downloaded deb. file, it might be worth checking that you have 'gdebi' installed. gdebi is a deb. file installer and can be found from the Software Centre.

---

### Post by Raygreen on 2011-08-17
[SIZE="3"]I got [COLOR="Red"]Google Chrome[/COLOR] to load after 3 attempts. First I went to Google Chromes website and downloaded it there. Then it took 3 tries before it loaded through [COLOR="Indigo"]The Ubuntu Software Center[/COLOR]. I am actually on Google Chrome right now entering this thread.[/SIZE]

---

### Post by infamous-online on 2011-08-17
> **Raygreen said:**
> [SIZE="3"]I got [COLOR="Red"]Google Chrome[/COLOR] to load after 3 attempts. First I went to Google Chromes website and downloaded it there. Then it took 3 tries before it loaded through [COLOR="Indigo"]The Ubuntu Software Center[/COLOR]. I am actually on Google Chrome right now entering this thread.[/SIZE]

Google Chrome works everytime for me when I download it from Google and letting synaptic take care of the rest.

---

### Post by kokusayb on 2011-08-18
When I click on the file in downloads it automatically opens up ubuntu software centre. Ubuntu software centre proceeds to load forever with no results.

---

### Post by MARP1961 on 2011-08-18
Install 'Gdebi Package Installer' from the Ubuntu Software Centre for all downloaded deb.files.

---

### Post by kokusayb on 2011-08-21
The software center it apparently broken. It just gives me the loading symbol. I tried apt-get install gdebi and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gdebi

---

### Post by oboedad55 on 2011-08-21
> **kokusayb said:**
> The software center it apparently broken. It just gives me the loading symbol. I tried apt-get install gdebi and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gdebi

Looks like your software sources are messed up. Go in and comment out the medibuntu lines for now and retry.

---

