---
title: "APT vs Adept [Resolved]"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by TJP on 2006-12-22
Hi all. I'm brand new to the forum, so please correct me if I do things wrong.
I've been using Debian at work for awhile and am reasonably confident using APT to install packages. I recently installed kubuntu at home and I see it has both APT and Adept. Do these programs overlap? Adept is fast and easy, but provides very little information about what's happening to the computer. I guess my main question is, is it reasonable to use APT to install individual packages and Adept to do general updates? Or will this mess up dependencies?

---

### Post by aysiu on 2006-12-22
Adept is just a graphical frontend for *apt*.

---

### Post by groggyboy on 2006-12-22
adept is a qt gui frontend to apt (the gnome equivalent is synaptic).  you can use the command line and the gui app quite interchangably (the only problem is when you try to run multiple package managers simultaneously).  i personally alternate between aptitude, apt-get, and adept quite frequently without hassle.  if you wish to use one over the other or if you wish to switch it up a bit, it doesn't matter.  they all work together.

---

### Post by TJP on 2006-12-22
Thanks! It's a relief, since I have nightmares about broken dependencies.

---

### Post by maxamillion on 2006-12-22
I wouldn't advise using two different package managers because each will keep track of and know what packages it has managed but not what the other has... it can cause very strange behavior.

For example: If you install a package with apt-get and remove it with aptitude, aptitude does not see it as installed. As would apt-get not see it installed if aptitude were used to install.

A quote from the #debian channel on irc.freenode.net official bot: "aptitude has more advanced conflict/dependency resolution than other tools, it has far more advanced searching available, and will automatically uninstall unneeded dependencies"

It is my recommendation to use aptitude at all times, and for those who use apt-get now you can simply use the same commands that you are used to but replace "apt-get" with "aptitude" :)

---

### Post by aysiu on 2006-12-22
> **maxamillion said:**
> 
For example: If you install a package with apt-get and remove it with aptitude, aptitude does not see it as installed. As would apt-get not see it installed if aptitude were used to install. This simply isn't true.

Evidence: ```
username@ubuntu:~$ **sudo apt-get install xmms**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmikmod2
The following NEW packages will be installed:
  libmikmod2 xmms
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1235kB of archives.
After unpacking 7746kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com edgy/main libmikmod2 3.1.11-a-6ubuntu2 [124kB]
Get:2 http://archive.ubuntu.com edgy/main xmms 1.2.10+cvs20060429-1ubuntu2 [1111kB]
Fetched 1235kB in 13s (90.6kB/s)                                               
Selecting previously deselected package libmikmod2.
(Reading database ... 118116 files and directories currently installed.)
Unpacking libmikmod2 (from .../libmikmod2_3.1.11-a-6ubuntu2_i386.deb) ...
Selecting previously deselected package xmms.
Unpacking xmms (from .../xmms_1.2.10+cvs20060429-1ubuntu2_i386.deb) ...
Setting up libmikmod2 (3.1.11-a-6ubuntu2) ...

Setting up xmms (1.2.10+cvs20060429-1ubuntu2) ...

username@ubuntu:~$ **sudo aptitude remove xmms**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  xmms 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 7422kB will be freed.
Writing extended state information... Done
(Reading database ... 118210 files and directories currently installed.)
Removing xmms ...
username@ubuntu:~$ 
``` As you can see, *aptitude* fully recognizes XMMS as having been installed, even though I used *apt-get* to install XMMS.

Like you, I wouldn't recommend mixing and matching *apt-get* and *aptitude* for a slightly different reason. *aptitude* will remember the unused dependencies, and *apt-get* won't (unless you're using Edgy and know about *autoremove*). Notice how *apt-get* installed *libmikmod2* along with *xmms* but *aptitude* didn't remove *libmikmod2*? If I had used *aptitude* to install **and** remove XMMS, it would have removed *libmikmod2* as well, as evidenced below: ```
username@ubuntu:~$ **sudo aptitude update && sudo aptitude install xmms**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]
Ign http://archive.ubuntu.com edgy/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy/universe Translation-en_US
Get:3 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages
Ign http://archive.ubuntu.com edgy-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com edgy-updates/universe Translation-en_US
Hit http://archive.ubuntu.com edgy Release
Hit http://archive.ubuntu.com edgy-updates Release                  
Hit http://security.ubuntu.com edgy-security/restricted Packages    
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://archive.ubuntu.com edgy-updates/universe Packages
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libmikmod2 
The following NEW packages will be installed:
  libmikmod2 xmms 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1235kB of archives. After unpacking 7746kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package libmikmod2.
(Reading database ... 118116 files and directories currently installed.)
Unpacking libmikmod2 (from .../libmikmod2_3.1.11-a-6ubuntu2_i386.deb) ...
Selecting previously deselected package xmms.
Unpacking xmms (from .../xmms_1.2.10+cvs20060429-1ubuntu2_i386.deb) ...
Setting up libmikmod2 (3.1.11-a-6ubuntu2) ...

Setting up xmms (1.2.10+cvs20060429-1ubuntu2) ...

username@ubuntu:~$ **sudo aptitude remove xmms**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libmikmod2 
The following packages will be REMOVED:
  xmms 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 7746kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 118210 files and directories currently installed.)
Removing xmms ...
Removing libmikmod2 ...
```

---

### Post by maxamillion on 2006-12-22
run the program, xmms is still there even though one thinks its gone and the other doesn't

for more information:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by aysiu on 2006-12-22
> **maxamillion said:**
> run the program, xmms is still there even though one thinks its gone and the other doesn't

for more information:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)
Yeah, I get ```
username@ubuntu:~$ xmms
bash: xmms: command not found
``` By the way, I wrote that Psychocats page.

The point of the page isn't that *apt-get* and *aptitude* don't talk to each other about what's installed--they're both working off *dpkg* for package management. The point is that they don't talk to each other the same way about associating dependencies with packages. If *apt-get* brings in a dependency, *aptitude* won't remove the dependency. That's not saying it doesn't know what it's installed--it's saying it doesn't know, of the packages that are installed, which are associated with each other.

---

### Post by xabbott on 2006-12-22
> **aysiu said:**
>  By the way, I wrote that Psychocats page.

Can't stop laughing... :D

---

### Post by maxamillion on 2006-12-22
Ok, apt-get install openoffice.org then aptitude remove it ... I swear it stays, does on 4 of my machines at work.

---

### Post by aysiu on 2006-12-22
> **maxamillion said:**
> Ok, apt-get install openoffice.org then aptitude remove it ... I swear it stays, does on 4 of my machines at work.
If that's really true, then you should file a bug report on it.

---

### Post by maxamillion on 2006-12-22
Oh, hrmm... just thought it was an issue between crossing the two package managers. Also, thanks for writing that article ... helps me show people why aptitude is superior. :)

---

### Post by xabbott on 2006-12-23
Well if you remove openoffice.org I think that only removes the metapackage. Unless you installed/removed with aptitude. Again, I'm just guessing.

---

### Post by aysiu on 2006-12-23
> **xabbott said:**
> Well if you remove openoffice.org I think that only removes the metapackage. Unless you installed/removed with aptitude. Again, I'm just guessing.
What xabbott says is true.

Removing *openoffice.org-core*, however, will remove almost all the OpenOffice packages.

---

### Post by melissawm on 2007-09-24
Hey guys, sorry to dig up an old thread but i still have a question. Do you guys know if it's normal for my Adept to not show even half of the applications available through apt-get? I mean, when i search for "aspell" for instance in Adept, it shows no packages. When i do "apt-cache search aspell" it shows a lot of stuff. Is this normal? Where is the conf file for Adept? Is this maybe because there are 2 configuration files, one for apt-get and one for Adept with different repos? Thanks for any help :)

---

