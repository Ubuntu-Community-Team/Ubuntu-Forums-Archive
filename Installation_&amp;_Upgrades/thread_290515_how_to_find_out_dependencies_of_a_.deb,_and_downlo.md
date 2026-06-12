---
title: "how to find out dependencies of a .deb, and download all of them as .deb's"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by syxbit on 2006-11-01
my wireless won't work without network-manager-gnome. (it does now, but after a format it's a pain to have to plug in to an ethernet to get network manager)
is there an easy way to find out what the dependencies are, and get the .deb's for all of them, so i can install it after i format.
also, one i have all the .deb's, to install it would it just be
```
sudo dpkg -i prog.deb prog2.deb
```

---

### Post by bsussman on 2006-11-01
'man apt-get'  tells me that -d means download only.

---

### Post by Ramses de Norre on 2006-11-01
[Here](http://packages.ubuntu.com) you can find info about packages.

---

### Post by TigerC10 on 2007-09-05
I have the same question, but for a different reason.

I am running a network of ubuntu machines, and I want to control the packages that each workstation is permitted to download without restricting access to the apt-get command.


My solution is to create a local repository on the network and add that to the sources.list while replacing everything else.  I have no issues with editing sources.list appropriately, but I am running into a roadblock for creating the local network repository.



I want to download only those .deb packages I need for the i386, and amd64 architectures (as well as the debs made for all) - but when I started to download these debs manually I found that the dependency list is VERY long for some things.



So I need a way to download a package and all of its dependencies as their respective .debs so that I can setup my network's repository appropriately.

---

### Post by K.Mandla on 2007-09-05
> **TigerC10 said:**
> I have the same question, but for a different reason. ...
I don't know if this will be a help to you -- or to the OPer for that matter -- but this was the only solution I had to offline updates.

[http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/](http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/)

It's not perfect but it kept me content for about a month or so.

---

### Post by TigerC10 on 2007-09-05
It's a nice workaround, but manually going through the packages that I need shows that the dependancies go deeper than the 3 levels covered by this method.

---

### Post by rsambuca on 2007-09-05
"AptonCD might help you out in this area, although I haven't tried it out myself yet.  Other than that, if you go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and search for your file, it lists all dependencies with links.

---

### Post by TigerC10 on 2007-09-05
I did look through AptonCD - but it only allows the packages that are for the particular architecture it was run on (it was designed for backup purposes, after-all).  I have both amd64 and i386 to manage - so I'd have to go through AptonCD two times.  Since I have more than just a couple of packages it'd be quite irritating - but less so than the packages site.

I spent about 3 hours on it downloading package after package manually from the site, going through dependencies etc.  When I got to gnome I went through 2 dependencies of gnome and said forget it - because there were so many dependencies of those dependencies.


Is there really nothing else that can be done?

---

### Post by Nythain on 2007-09-05
sudo apt-get build-dep -d packagename might work... not sure if build-dep will recognize the -d flag or if its going to want to install teh deps... basically build-dep will search the repos for the source of what you are trying to install, and get any necessary dependencies required... great when you want to compile a newer version of software in teh repos but dont want to hassle with individually getting each dep... hopefully this helps you with your problem... downloaded packages are usually stored in /var/cache/apt/archives i believe, so look there for the packages if the command actually works successfully

---

### Post by rsambuca on 2007-09-05
Oh, I see what you are trying.  Wow, from scratch with all of those dependencies is pretty tough.  Personally, I would just restrict the root privileges!

---

### Post by TigerC10 on 2007-09-05
Heh, I can't exactly do that either.  There are different departments that need different applications - so I don't want every app on every machine.  Plus, I want to be able to add the new software in the future to the repo on the network and then let the department heads deal with telling the pions to do apt-get.  The boss doesn't want any unathorized apps getting downloaded via apt-get thanks to a repo from an outside source...


I think I'm just going to have to write a script for this...

EDIT:
If I write a script, I can use wget to get the initial package...  But how can I get a list of the dependencies?

---

### Post by K.Mandla on 2007-09-06
You can use apt-cache depends to get dependencies. The problem is that the package list on the host machine is already outdated, which means you don't know what version is in the repositories, which means wget can't help much.

Or at least, that was the problem I had when I  was trying to do the same thing. :-k

---

### Post by jim_p on 2007-09-06
Please see my post here [http://ubuntuforums.org/showthread.php?t=501236](http://ubuntuforums.org/showthread.php?t=501236)
and tell me if it fits your needs.

I am too tired to go through the procedure again, sorry :(

---

### Post by rsambuca on 2007-09-06
I also had a thought that you might use gentoo instead of ubuntu.  Then you could mask certain keywords.

---

### Post by TigerC10 on 2007-09-06
> **K.Mandla said:**
> You can use apt-cache depends to get dependencies. The problem is that the package list on the host machine is already outdated, which means you don't know what version is in the repositories, which means wget can't help much.

Or at least, that was the problem I had when I  was trying to do the same thing. :-k

Well I would have the only machine that has an outside repository so that I can properly deposit any new packages to our local repo.  Just running apt-get update would make sure I've got the latest stuff in the apt-cache, right?


@jim_p - Excellent solution.  I think that will work beautifully for my purposes.  However, I think I'd still have to run through it twice for both the amd64 architecture machines and the i386 machines.

---

