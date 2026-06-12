---
title: "How to get list of packages installed"
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by pbewig on 2012-06-23
I have a desktop computer running Ubuntu 9.04 that I want to upgrade to 12.04. I intend to back up the /home directory, install the 12.04 system as a new install, then restore the data in the /home directory.

Over the last three years I have installed a dozen or so packages. Some I remember, but doubtless there are others that I'll forget.

How can I get a list of the packages that I have installed?

Many thanks,

Phil

---

### Post by drs305 on 2012-06-23
To create a list called "installed-packages", run on old computer:
```
sudo dpkg --get-selections | grep -v "deinstall&#8221; >$HOME/Desktop/installed-packages 

```
Copy installed-packages to $HOME/Desktop on new computer, and to import: 
```
sudo apt-get update
sudo dpkg --clear-selections
sudo dpkg --set-selections <$HOME/Desktop/installed-packages 	
sudo apt-get dselect-upgrade

```
OR
Synaptic: File > Save Markings As, tick the "Save full state, not only changes". If don't tick, you will probably get an empty file. 
You can use this file via Synaptic to import the file list in your new installation, although you will first have to install synaptic

---

### Post by pbewig on 2012-06-23
Sounds good. Thanks

---

### Post by pbewig on 2012-06-23
Oops! That's 1500 packages. I know I didn't install that many; I suppose some packages are installed because I installed packages that depend on them.

Is it possible to get a list of just the dozen or so "top-level" packages I installed?

---

### Post by drs305 on 2012-06-23
> **pbewig said:**
> Oops! That's 1500 packages. I know I didn't install that many; I suppose some packages are installed because I installed packages that depend on them.

Is it possible to get a list of just the dozen or so "top-level" packages I installed?

That list includes all installed packages. Of course many of those packages would be the same in both versions, so the actual number of  *extra* packages would be nowhere near that large.

I'm not sure of a way to filter only the ones you have installed but perhaps someone else will know. 

I personally keep track of each major extra app I install and keep them in a list. My list usually runs about 20-25 packages.

---

### Post by pbewig on 2012-06-23
Can the list be sorted by date?

---

### Post by drs305 on 2012-06-23
> **pbewig said:**
> Can the list be sorted by date?

I thought about discussing that. You can take a look at the log files in /var/log/dpkg.log  The problem is that the logs are split apart and the the logs don't go back as far as your original installation. 

You can take a look at the other files in /var/log and also specifically take a look at /var/log/apt/history.log  I don't know how far back the history.log file goes.

---

### Post by pbewig on 2012-06-23
I looked. Not far enough. And the logs have everything, including regular updates.

I think I'm out of luck.

Thanks for the help.

---

### Post by oldfred on 2012-06-24
I use the dpkg to reinstall apps. It does not reinstall any already installed. But many applications have changed. I found I was still reinstalling python2.5 when 2.7 is now the standard. You also have OpenOffice which is now LibreOffice.

List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt

Aptitude has a way to filter for top level.

Top level only - no depends
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'


HowTo: Create a list of installed packages
Compare two lists: kdford post #70
[http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)
I created a python apt and sqlite data base to compare my lists which kinda worked.

---

### Post by josephmills on 2012-06-24
```
dpkg-query -l 

```
will do all that

---

