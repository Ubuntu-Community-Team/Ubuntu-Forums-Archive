---
title: "While trying to upgrade from 18.04 to 20,04 error occurs"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by MickM on 2020-08-11
I was able to start the upgrade from software upgrade, however I receive the below error and then the upgrade stops and does not upgrade. I have done this with various servers with the same results.

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 


W:Updating from such a repository can't be done securely, and is 
therefore disabled by default., W:See apt-secure(8) manpage for 
repository creation and user configuration details., E:The repository 
'http://au.archive.ubuntu.com/ubuntu zesty-updates Release' does not 
have a Release file., W:Updating from such a repository can't be done 
securely, and is therefore disabled by default., W:See apt-secure(8) 
manpage for repository creation and user configuration details., 
E:The repository 'http://security.ubuntu.com/ubuntu zesty-security 
Release' does not have a Release file.

---

### Post by CatKiller on 2020-08-11
Zesty was 17.04. You definitely shouldn't be using any zesty repositories.

---

### Post by MickM on 2020-08-11
Yes I did notice the Zesty thing. I don't know why that shows up as I am using 18.04 not 19.00. I do not have OS 19.00 installed.

---

### Post by Impavidus on 2020-08-12
What's in your /etc/apt/sources.list?

---

### Post by pdv4 on 2020-08-12
I am having the same issue. Trying to avoid editing my sources list. Wondering if using an iso disk would allow me to upgrade and keep files. Hmm.

Patrick

---

### Post by CelticWarrior on 2020-08-12
@pvd4

Very likely NOT the exact same problem. Please open your own thread. And no, it won't make a difference.

---

### Post by MickM on 2020-08-12
deb cdrom:[Lubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es-mirrors.evowise.com/ubuntu/](http://es-mirrors.evowise.com/ubuntu/) bionic main universe restricted multiverse
deb-src [http://es-mirrors.evowise.com/ubuntu/](http://es-mirrors.evowise.com/ubuntu/) bionic main universe restricted multiverse #Added by software-properties
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) zesty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) zesty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) zesty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) zesty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) zesty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) zesty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security restricted universe multiverse main
deb [http://es-mirrors.evowise.com/ubuntu/](http://es-mirrors.evowise.com/ubuntu/) bionic-updates restricted universe multiverse main
deb [http://es-mirrors.evowise.com/ubuntu/](http://es-mirrors.evowise.com/ubuntu/) bionic-backports restricted universe multiverse main

---

### Post by Impavidus on 2020-08-13
There's a lot of rubbish in that sources.list, but the important parts are all there. It looks like a sources.list for zesty that has the sources for bionic appended. In most cases, your package manager should automatically pick the bionic software. I suggest you edit your sources.list with```
sudoedit /etc/apt/sources.list
```
Make the following edits:
- Change the line with "zesty partner" so that it says "bionic partner";
- Remove all other lines mentioning zesty;
- Assuming you don't need the source code repositories, put a # at the start of every line starting with deb-src.
Then save the file, close the text editor

---

### Post by MickM on 2020-08-13
> **Impavidus said:**
> There's a lot of rubbish in that sources.list, but the important parts are all there. It looks like a sources.list for zesty that has the sources for bionic appended. In most cases, your package manager should automatically pick the bionic software. I suggest you edit your sources.list with```
sudoedit /etc/apt/sources.list
```
Make the following edits:
- Change the line with "zesty partner" so that it says "bionic partner";
- Remove all other lines mentioning zesty;
- Assuming you don't need the source code repositories, put a # at the start of every line starting with deb-src.
Then save the file, close the text editor


I was able to do all you said above. However I could not save the changes.

---

### Post by Impavidus on 2020-08-13
Why not? Permissions issue, filesystem mounted read-only, you don't know how to use the text editor?

To write changes to sources.list, you need root permissions, and that's what sudoedit is for. sudoedit opens a text editor (you can configure which one, by default it's nano) with the file you want to edit and after closing the text editor, it will write the changes to the file you wanted to change.

---

### Post by MickM on 2020-08-13
[B]Impavidus,
[/B]I don't know how. I opened an LX Terminal  then opened into **GNU nano 2.9.3            /var/tmp/sourcesXXmGMxd0.list **            and was able to edit the text, I closed the window then opened another LXTerminal and did the same and when the GNU nano window opened the list was the same before I edited it the last time. So I edited the list again then closed and upon checking the list was the same as before.

---

### Post by Impavidus on 2020-08-14
You have to save the file and close the text editor, not the terminal (at least, not until after you closed the text editor). nano shows all keyboard commands ot the bottom of the screen, ^X means ctrl+x etc. So to save a file, hit ctrl+o, to exit the text editor hit ctrl+x. If you close the terminal before closing the text editor, sudoedit and the text editor get killed and have no chance to save the file.

There is a terminal, inside the terminal is a shell, inside the shell is sudoedit, inside sudoedit is nano. And to do it properly, after opening those left to right, you have to close them right to left. First save the temporary file and close the text editor, then sudoedit will detect that, will save the file to the permanent root-owned location and sudoedit will terminate, then it's save to close the terminal and the shell. You see?

---

### Post by MickM on 2020-08-14
**Impavidus**
Thanks for your help. Yes I did figure what the controls at the bottom were. I instead found and uploaded a File Cleaner STACER and used that and found the files and deleted them and changed the two others to BIONIC. I was then I used the terminal to do an upgrade, which worked and upgraded. Problem was that it worked OK but when it rebooted the screen froze at the login screen and I cannot open. I have since (on another PC) downloaded an ISO file onto a usb key and have tried to do a complete new upgrade, without success.

---

### Post by Impavidus on 2020-08-15
I don't like such tools. Installing and learning how to use such a tool is harder than just doing the job manually. If the tool can be used to automate frequent tasks, that's OK, but fixing a broken sources.list is not a frequent task. And I want transparency, want to know what's going on. But if it works for you, that's OK.

So now you attempted a release upgrade, the computer fails to boot now and you decided to try a fresh install after all? Broken release upgrades are hard to fix. Usually fresh install is better. If you've any difficulty with that, better start a new thread, as it's a new problem.

---

### Post by MickM on 2020-08-15
_[[COLOR=#000000]Impavidus[/COLOR]]("https://ubuntuforums.org/member.php?u=1417721")_[COLOR=#000000] 

Thanks for your help[/COLOR]

---

### Post by MickM on 2020-08-17
I finally loaded 20.04.1. After the usb flash drive I had loaded 20.04.1 image would not boot and was unable to operate my laptop, I did some further research and found the website [https://www.balena.io/etcher/](https://www.balena.io/etcher/)  So following instructions, on my borrowed laptop, I formatted my usb flash drive. Then downloaded from Ubuntu the 20.04.1 image onto the hard drive. Then I used the [https://www.balena.io/etcher/](https://www.balena.io/etcher/) website and transferred successfully the Image from the hard drive onto the usb flash drive. which I then tried the flash drive on my laptop, turned on the laptop and I saw it boot up and start to load the 20.04.1. Finally I was in operation again and after a couple of hours, had my laptop back and in full operation.
I will now close this thread with a solved.  :)

---

