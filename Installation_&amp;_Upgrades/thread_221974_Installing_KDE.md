---
title: "Installing KDE"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by thewweundertaker on 2006-07-24
I'm a novice using Ubuntu. I wish to know how to install KDE on the default Ubuntu Desktop installation USING the Kubuntu Desktop Installation CD. I have a dial-up connection and so can't download the files, but I do have the Kubuntu CD. I'm using DapperDrake. I want to keep both the Gnome and KDE environments together so I can switch between them.

Thanks.:KS

---

### Post by mogelhead on 2006-07-24
It's been asked before: [How can I add KDE desktop to Gnome with Kubuntu CD]("http://www.ubuntuforums.org/showthread.php?t=215882")
There is a possible solution there. Although, the person never reported back how/if it worked.

Also, have a look at [InstallingKDE]("https://help.ubuntu.com/community/InstallingKDE").

---

### Post by aysiu on 2006-07-24
You cannot install Kubuntu on top of Ubuntu using the Kubuntu **Desktop CD**.

The only way to install Kubuntu on top of Ubuntu is to use the internet: ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
``` or to use a Kubuntu **Alternate CD**: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by ioannis on 2006-07-25
I tried this:
```
sudo aptitude update && sudo aptitude install kubuntu-desktop
``` 

and I got the following output:

...
Need to get 119MB of archives. After unpacking 363MB will be used.
The following packages have unmet dependencies:
  libpoppler1-qt: Depends: libpoppler1 (= 0.5.1-0ubuntu7) but 0.5.3-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gwenview [Not Installed]
kdegraphics-kfile-plugins [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
libpoppler1-qt [Not Installed]

Score is 62

Accept this solution? [Y/n/q/?]


I am kind of new to Linux, but it seems to me that this means that some packages will be not installed, and therefore there could be some dependency issues. Should I accept this solution or not? If not, what else can I do?
If I try to install with
sudo apt-get install kubuntu-desktop
I get the same problem as in:
[http://www.ubuntuforums.org/showthread.php?t=214424](http://www.ubuntuforums.org/showthread.php?t=214424)

Thanks!

---

### Post by aysiu on 2006-07-25
Try this, then: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list
``` Delete (Control-K) every single line except the one for the CD-ROM source. Save (Control-X, Y, Enter). Then ```
sudo aptitude update
sudo aptitude isntall kubuntu-desktop
```

---

### Post by ioannis on 2006-07-25
Actually, I don't have any CD-ROM source listed. I upgraded to Dapper from Breezy through the Internet. Is there any one repository I could leave in to make it work, or should I download the Dapper Ubuntu CD and add it to the repository? If so, what would the line for the CD-ROM be like?

Thanks again.

---

### Post by aysiu on 2006-07-25
Oh, then can you try getting a fresh sources.list?
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Do that (it backs up your current repositories list) and then ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
``` Sorry. I didn't realize you were a different person.

---

### Post by Swab on 2006-07-25
just stick in the cd and do

sudo apt-cdrom add

---

### Post by ioannis on 2006-07-25
Thanks for the quick reply. I did create the new repository list and run the aptitude lines again, same result as before: 

Keep the following packages at their current version:
gwenview [Not Installed]
kdegraphics-kfile-plugins [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
libpoppler1-qt [Not Installed]

Score is 62

Accept this solution? [Y/n/q/?]


Anything else I should try? May there be some repository that is down temporarily? BTW, my internet connection is very fast, so don't worry about that. Thanks for everything!

---

### Post by ioannis on 2006-07-26
I also downloaded the Kubuntu alternate CD and followed aysiu's suggestion:

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop

I still got the same aptitude message:

The following packages have unmet dependencies:
  libpoppler1-qt: Depends: libpoppler1 (= 0.5.1-0ubuntu7) but 0.5.3-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gwenview [Not Installed]
kdegraphics-kfile-plugins [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
libpoppler1-qt [Not Installed]

Score is 62

Accept this solution? [Y/n/q/?]


Any other options?
Thanks!](*,)

---

