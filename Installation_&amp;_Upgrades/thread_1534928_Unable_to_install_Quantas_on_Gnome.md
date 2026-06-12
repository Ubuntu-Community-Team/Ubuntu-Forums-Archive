---
title: "Unable to install Quantas on Gnome"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by rjakes on 2010-07-20
I recently installed Ubuntu 10.04 and am running gnome desktop. I have tried to install Quantas Pro using Ubuntu Software Center and synaptic unsuccessfully. I see from researching the forums that it is possible but I need specific instructions. I don't know what I am doing wrong. I have read that I will need a lot of dependencies. 
How do I load the KDE dependencies with Quantas?  I assumed I had not loaded the needed KDE dependencies for Gnome.

rjakes

---

### Post by lisati on 2010-07-20
Huh? Link please: AFAIK Qantas (without the U) is an airline.

---

### Post by ronnielsen1 on 2010-07-20
If you're talking about quanta, it's in the universe repository. Go to Synaptic > Settings Tab > Repositories and make sure universe repository is enabled. Reload and search and it should pull in all dependencies

---

### Post by rjakes on 2010-07-20
ronnielsen1,

I spelled quanta wrong. I have installed quanta using synaptic including universe and dependencies chosen and installed.

synaptic looks a little different in 10.04 I guess from your "Synaptic > Settings Tab > Repositories and make sure universe  repository is enabled" reference, as there was no Repositories

I successfully installed quanta, kdewebdev-doc-html, kfilereplace-kde3, and quanta-data.

quanta does not appear on any of the menus in Gnome - Applications, Places or System.

rjakes

---

### Post by rjakes on 2010-07-20
ronnielsen1,

synaptic in 10.04 has repositories under settings but there is no universe repository.

rjakes

---

### Post by rjakes on 2010-07-20
I reinstalled quanta and re-booted and now it displays under Applications > Programming > Quanta Plus, however, I got an error message with 3 missing Applications. I managed to install 2, but Cervisia is still missing although I have found it in synaptic. I uninstalled and re-installed, but still get:

Some applications required for full functionality are missing:
- Cervisia [[http://www.kde.org/apps/cervisia]](http://www.kde.org/apps/cervisia]) - CVS management plugin will not be available

---

### Post by ronnielsen1 on 2010-07-21
> synaptic looks a little different in 10.04 I guess from your "Synaptic  > Settings Tab > Repositories and make sure universe  repository  is enabled" reference, as there was no Repositories synaptic in 10.04 has repositories under settings but there is no  universe repository.

I have 10.04 and this is my synaptic - 2nd one down is the universe repository / 3rd one down is restricted repository

[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-SoftwareSources.png[/IMG]

> 
Some applications required for full functionality are missing:
- Cervisia [[http://www.kde.org/apps/cervisia]]("http://www.kde.org/apps/cervisia%5D")  - CVS management plugin will not be available 	
It pulled in cervisia fine for me. 


[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-SynapticPackageManager-1.png[/IMG]

It appears to be in the repository lucid/main (us.archive.ubuntu.com) which I believe is the first checkmark. Have you reloaded synaptic?

---

### Post by rjakes on 2010-07-21
I was able to locate the universe checkbox as well as the restricted checkbox in synaptic and I have both checked.

I re-installed cervisia and apparently have it installed (below). When I launch Applications > Programming > Quanta Plus I still get the error message.

[[IMG]http://a.imagehost.org/t/0229/cervisia.jpg[/IMG]]("http://a.imagehost.org/view/0229/cervisia")

rjakes

---

### Post by ronnielsen1 on 2010-07-22
This one?


[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-MissingApplications-Quanta.png[/IMG]


I can get rid of 2 of the three by installing kimagemapeditor-kde3 and kxsldbg-kde3

I don't know on the other one

Here's the new screenshot
[IMG]http://i80.photobucket.com/albums/j177/ronnielsen1/Screenshot-MissingApplications-Quanta-1.png[/IMG]

---

### Post by rjakes on 2010-07-22
Yes exactly. This is what I get now.

[[img]http://j.imagehost.org/0816/Screenshot_5.png[/img]](http://j.imagehost.org/view/0816/Screenshot_5)

---

### Post by ronnielsen1 on 2010-07-23
I found this post. The problem seems to be a kde3 / kde4 thing. Pay attention to the last post

[http://ubuntuforums.org/archive/index.php/t-1003635.html](http://ubuntuforums.org/archive/index.php/t-1003635.html)


> I've had the same problem, and after ignoring it for a few months,  finally got around to fixing it.

What worked for me (in Jaunty) was open the Configure Plugins window  (Settings > Configure Plugins) and then click Configure for each one  witha red check (Cerevisia, KImageMapEditor, Konsole). I cleared the  file name box for each one and then filled in the location box by  browsing to and selecting the directory for each application, all of  which were contained in usr/share/kde4/apps.

---

### Post by rjakes on 2010-07-25
And what more I can launch the actual Cervisia program!

[[img]http://a.imagehost.org/0774/Cervisia.png[/img]](http://a.imagehost.org/view/0774/Cervisia)

rjakes

---

### Post by rjakes on 2010-07-28
It apparently a KDE3 versus KDE4 issue. The following worked after attempting it a few times:

First download the appropriate libcvsservice0, konsole, and cervisia packages for your architecture from the following URLs:

[http://packages.ubuntu.com/en/hardy-...libcvsservice0]("http://packages.ubuntu.com/en/hardy-backports/libs/libcvsservice0")
[http://packages.ubuntu.com/hardy/konsole](http://packages.ubuntu.com/hardy/konsole)
[http://packages.ubuntu.com/hardy/cervisia](http://packages.ubuntu.com/hardy/cervisia)

Now install a few dependencies:

sudo aptitude install cvs kdelibs4c2a

Now change to the directory that you downloaded the packages to and  execute the following commands to install them (of course changing the  names if the versions are different):

sudo dpkg -i libcvsservice0_3.5.10-0ubuntu1~hardy1_amd64.deb
sudo dpkg -i cervisia_3.5.9-0ubuntu1_amd64.deb
sudo dpkg -i konsole_3.5.9-0ubuntu7_amd64.deb

Now install Quanta Plus and the KDE3 versions of kimagemapeditor and kxsldbg:

sudo aptitude install quanta kimagemapeditor-kde3 kxsldbg-kde3

---

