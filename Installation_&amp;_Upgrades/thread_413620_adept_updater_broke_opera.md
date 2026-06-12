---
title: "adept updater broke opera"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by howardde on 2007-04-19
hi,
Adept update told me that there was an update available for opera, my primary browser.
This seemed a bit weird, because I had already used the Adept Manager to update, and upgrade-all today.

Anyway, I let it, but it broke opera, which then would not boot at all. I tried uninstalling opera with Adept Manager, and have since tried reinstall with no success. 

I get the following error from a GUI box:

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 

Please can someone help, as I am unsire how to fix this. I am quite happy to go back to the old version of opera if need be. 

Thanks in advance,
Howard.

ps I'm using Kubuntu 6.10: the Edgy Eft

---

### Post by rillip on 2007-04-19
My recommendation:

sudo apt-get remove opera

If it gives you an error, please post the exact output, as there shouldn't be a package dependancy issue.

After that, visit here:

[http://www.opera.com/download/](http://www.opera.com/download/)

And install the latest 92.  If you're using KDM, you can just right click and chose "install pacakge."  For me, Ark gave me a path error when I simply tried running the file.  Not sure how it works in Gnome, but it should at least set you on the right path.

---

### Post by howardde on 2007-04-19
thanks rillip :)

well i seem to have managed to remove it ok.

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package opera is not installed, so not removed
The following packages were automatically installed and are no longer required:
  apache2-utils libapr0 apache2-common apache2-mpm-worker libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

then:
sudo apt-get install opera
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.


ok...so  go to the opera download page, grab it, sudo mv it to /usr/bin
and cd there, then :

sudo aptitude install opera_9.20-20070409.6-shared-qt_en_i386.deb
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "opera_9.20-20070409.6-shared-qt_en_i386.deb"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  opera: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
         Depends: libgcc1 (>= 1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
         Depends: libqt3-mt (>= 3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3.1 is to be installed
         Depends: libstdc++6 (>= 4.1.2) but 4.1.1-13ubuntu5 is to be installed
E: Broken packages

So...I have it..I can see it in the console with ls, but the os can't see it?
I am confused...

---

### Post by Ambimom on 2007-04-19
I found a solution that might work for you:

[http://ubuntuforums.org/showthread.p...ighlight=Opera](http://ubuntuforums.org/showthread.p...ighlight=Opera)

---

### Post by rillip on 2007-04-19
I think you should review your repositories.  Something doesn't seem right here, that install is good, because I could do it!  And it's trying to install old packages by the looks of it, like it's not recognizing the new ones you have.  Did you make sure you chose the right distro?  I'm using dapper drake and had no problems installing.  Might try just waiting and upgrading to Fiesty if the above doesn't work.

---

### Post by chek2fire on 2007-04-19
i have the same problem here :(

---

### Post by Big_J on 2007-04-19
> sudo aptitude install opera_9.20-20070409.6-shared-qt_en_i386.deb
That's not how you install a local deb file.
In gnome you simply have to double click it and it will be handled by the correct manager. Save the file to desktop and double click it, then you will be able to install it.

---

### Post by howardde on 2007-04-19
Ambimom-
That link doesn't actually take me to a thread, but a catagories page..?

rillip-
Did you make sure you chose the right distro? I'm using dapper drake and had no problems installing. Might try just waiting and upgrading to Fiesty if the above doesn't work.

I'm not certain! I had feisty installed, but had such trouble getting .avis working that i reinstalled this version. As i recall, that was an adept updater that asked me to upgrade then as well. 

Big_J
That's not how you install a local deb file.
 In gnome you simply have to double click it and it will be handled by the correct manager. Save the file to desktop and double click it, then you will be able to install it.

My bad.
I'm using kubuntu though, not gnome. Clicking on it brings it up in ark, from where I don't know how to install it either.

Thanks for your thoughts folks..

---

### Post by Big_J on 2007-04-19
You can use KPackage in KDE. it does a beautiful job.

Edit:
And you might want to use the static deb if you're using 7.04

---

### Post by howardde on 2007-04-19
what does static mean in this context?
I had another look at their site, but couldn't find a static version

---

### Post by Big_J on 2007-04-19
I reasonably believe that the static deb is simply a deb file designed to install on most, if not all distros that support the deb packaging system. As in, they are not made for a specific distro.
But if you're using edgy, then they have a version for it. 

How's KPackage working out for you?

---

### Post by howardde on 2007-04-19
thanks!
KPackage installed it jut fine.

I had to install KPackage with adept first, then there was a small error, KPackage finding a lock somewhere - closing adept sorted that.

thanks again..

---

### Post by Big_J on 2007-04-19
Yup. Now if only someone can help me with my problem :)

---

