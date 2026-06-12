---
title: "from 13.10 to 14.04 - how do I avoid pkgs I've removed"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by keratos2 on 2014-05-10
I've trimmed down my ubuntu 13.10 install to get rid of much of the pre-installed apps (provided they were not included in the "base" or "desktop" virtual packages - arghh!)

Now, when I do "apt-get dist-upgrade" the system wants to re-install many of the packages I've removed. Can I prevent this or is there another set of commands more appropriate?

---

### Post by ibjsb4 on 2014-05-10
First, [COLOR=#000000]"apt-get dist-upgrade" is not a version (release) upgrade.

[/COLOR]https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands
[COLOR=#000000]
I also suppect that you still have the metapackage "ubuntu-desktop" still installed.  That package will instruct your download manager to  download all packages.

This package should be safe to remove.  Try that and take note of whats being removed.

```
sudo apt-get remove -s ubuntu-desktop
```

What I am not sure about is the version upgrade to 14o4.  I'm thinking it will reinstall this package.


[/COLOR]

---

### Post by deadflowr on 2014-05-10
dist-upgrade shouldn't re-install packages unless said package is a dependency of an existing package.

So it's advisable to see whether or not the removed package is dependant or a dependency of something else.

Two ways to do this is:
1)synaptic package manager, right-click on the package > go to properties > dependencies tab.

2)the command line apt-cache showpkg <packagenamehere> will list dependencies.

---

### Post by keratos2 on 2014-05-10
its okay, I'm not explaining myself very well - looking at the responses. 
What I've done is deliberately break dependencies. This is because virtual packages like kde-desktop contain Kmail which I never use. Now I dont know why Canonical feel that its fine to promote Kmail as part of kde-desktop. Absolutely crap. No way Kmail is ESSENTIAL part of the kde-desktop. So I removed it. I did same for other packages. CHOICE is king in linux so I wish Canonical would stop building in crap I dont need and just keep it simple and if people want to add Kmail then they can. 
KDE5 framework offers better loose integration so lets hope they wake up and smell the coffee and make a lean distro that people can add from the software sources if they need.

---

### Post by monkeybrain20122 on 2014-05-10
> **keratos2 said:**
> its okay, I'm not explaining myself very well - looking at the responses. 
What I've done is deliberately break dependencies. This is because virtual packages like kde-desktop contain Kmail which I never use. Now I dont know why Canonical feel that its fine to promote Kmail as part of kde-desktop. Absolutely crap. No way Kmail is ESSENTIAL part of the kde-desktop. So I removed it. I did same for other packages. CHOICE is king in linux so I wish Canonical would stop building in crap I dont need and just keep it simple and if people want to add Kmail then they can. 
KDE5 framework offers better loose integration so lets hope they wake up and smell the coffee and make a lean distro that people can add from the software sources if they need.

It has nothing to do with canonical, just the way KDE is designed. It is not modular on purpose, it is its design goal that they bundle a lot krap for a 'komplete desktop'. I have tried out kde some times ago and couldn't stand it after a few months, I remember it came with konqueror as the official browser which no one really used especially since not all the parts were installed by default,--you needed to install an additonal package so Kongueror could do some basic thing like using tabs or whatever..I can't remmeber what is was now except my reaction was "WTF", you gotta be kidding. You could install a real browser like Firefox but no,  you couldn't get rid of konqueror without breaking kde. It may not be the case any more I hope.

---

### Post by deadflowr on 2014-05-10
> What I've done is deliberately break dependencies.

Did you read my post?

Anyway,
The package kde-plasma-desktop is a lot lighter, many of the extra package you don't want aren't a part of it.
Maybe that would be more toward the system you want.

---

### Post by keratos2 on 2014-05-11
> **deadflowr said:**
> Did you read my post?

Anyway,
The package kde-plasma-desktop is a lot lighter, many of the extra package you don't want aren't a part of it.
Maybe that would be more toward the system you want.

?? OF COURSE I DID

Ive sorted it now anyway - I'll just live with broken packages and have marked certain elements so they are not (re)installed later by  a upgrade/update

plasma-desktop already installed.

---

### Post by deadflowr on 2014-05-11
> **keratos2 said:**
> 
plasma-desktop already installed.

Of course it is, it's part of kubuntu-desktop:)
But it can be installed standalone.
It's very barebones, and only installs very few extra things, like dolphin,konsole,kwrite, and a couple of other things.
Unlike kubuntu-desktop, which brings in the entire kubuntu system.

---

### Post by keratos2 on 2014-05-11
Ive uninstalled ubuntu-desktop (one package!!) and every other "session" / "desktop" , installed plasma-desktop. Now I've got a "lean" system but the distro install size is some 7.2GB. How come the ISO does everything and is 1.5GB? I'd just like a 1.5GB install too - ultimately that is where I'd like to be, I dont get how a liveCD can do (or seemingly for me at least) everything I need (and more) and be 1/5 of the size of my hard disk installation?

---

### Post by deadflowr on 2014-05-11
[MetaPackages]("https://help.ubuntu.com/community/MetaPackages")
and more specifically,
[Creating MetaPackages]("https://help.ubuntu.com/community/MetaPackages#Creating_Metapackages")

Should explain why uninstalling ubuntu-desktop alone doesn't clear up much space.

---

### Post by sudodus on 2014-05-12
> **keratos2 said:**
> Ive uninstalled ubuntu-desktop (one package!!) and every other "session" / "desktop" , installed plasma-desktop. Now I've got a "lean" system but the distro install size is some 7.2GB. How come the ISO does everything and is 1.5GB?

1. A large part of the iso file is compressed, and it is extracted (uncompressed) during the installation.
2. The installer is also (often if not always) downloading packages via the internet. These packages are also extracted (uncompressed) during the installation.
> 
I'd just like a 1.5GB install too - ultimately that is where I'd like to be, I dont get how a liveCD can do (or seemingly for me at least) everything I need (and more) and be 1/5 of the size of my hard disk installation?

When you run live, the packages that you use are extracted and read into RAM.

The smallest [installed] Ubuntu is to make a text only installation from the mini.iso. It will be less than 1.5 GB when installed, and it needs 'only' 160 MB RAM to run reasonably well. Lubuntu, which is the smallest and most light-weight Ubuntu flavour with a graphical desktop environment is between 2 and 2.5 GB (disk usage) when installed, and it needs 'only' 512 MB RAM to run reasonably well. You can get something between those sizes, if you only install a window manager for example fluxbox or openbox and still have a graphical desktop.

---

### Post by keratos2 on 2014-05-13
> **sudodus said:**
> 1. A large part of the iso file is compressed, and it is extracted (uncompressed) during the installation.
2. The installer is also (often if not always) downloading packages via the internet. These packages are also extracted (uncompressed) during the installation.


When you run live, the packages that you use are extracted and read into RAM.

The smallest [installed] Ubuntu is to make a text only installation from the mini.iso. It will be less than 1.5 GB when installed, and it needs 'only' 160 MB RAM to run reasonably well. Lubuntu, which is the smallest and most light-weight Ubuntu flavour with a graphical desktop environment is between 2 and 2.5 GB (disk usage) when installed, and it needs 'only' 512 MB RAM to run reasonably well. You can get something between those sizes, if you only install a window manager for example fluxbox or openbox and still have a graphical desktop.

Thanks bud
I have since obtained the minimal ISO for 13.10 , installed that then plasma-desktop, wicd-kde, kix, muon, bmcwl-kernel-source and a few other things inlcuding chromium, filezilla, libre office, k3b. And tha'ts it. 2.9GB and really responsive.
Really happy and content

---

### Post by sudodus on 2014-05-14
Congratulations :KS

If you think that the problem of the thread is solved, please click on Thread Tools at the top of the page and mark this thread as SOLVED

---

### Post by keratos2 on 2014-05-14
> **sudodus said:**
> Congratulations :KS

If you think that the problem of the thread is solved, please click on Thread Tools at the top of the page and mark this thread as SOLVED

Agreed.
And thanks to everyone else for their valued inputs

---

