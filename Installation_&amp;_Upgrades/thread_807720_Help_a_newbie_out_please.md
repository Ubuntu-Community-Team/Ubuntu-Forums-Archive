---
title: "Help a newbie out please"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by TheAJKMan on 2008-05-26
I think I'm running in daft mode at the moment, please let me explain. I'm pretty much a newbie at linux as a whole. Installed Ubuntu 7.10 and managed to get the net connection thing going okay. Now, to the problem at hand, I'm trying to update my Firefox from 2.0.0.6 to 2.0.0.14 

Here's what I've managed to do so far, and where I'm now stuck. I d/l the linux tar.gz from the mozilla.com site, extracted it and now have no idea how to get it installed/running. What I've read on the web has really just confused me totally so I have no idea as to how to actually proceed. I have no real idea how to use the package manager(Synaptec) or how to compile packages, so don't know if that is the problem. THe readme.txt file just says to go to a url on the mozilla site.

If it will help, I'm presuming that the installation was the default one. Otherwise, if this is the wrong place, would some please point me in the right direction.

---

### Post by iaculallad on 2008-05-26
Just use the ever-powerful apt-get utility to do the job for you:

Code:

> sudo apt-get update
sudo apt-get install firefox



Or you could use the Synaptics Package Manager. Navigate through System->Administration->Synaptics Package Manager and search for firefox.

---

### Post by TheAJKMan on 2008-05-26
Thanks for that quick reply. Have some d/l going at the moment for php stuff, which I'm assuming from the error message I got influences the firefox update/installation process. Will wait for that to finish and retry then. Will let you know how it goes. Wanting to try and learn something else new, as if trying to learn and get to grips with linux wasn't enough ;)

---

### Post by TheAJKMan on 2008-05-26
okay, the version displayed in Firefox is now 2.0.0.7, but on the site it's shown to be 2.0.0.14, the above described method has not updated it to that version. What now? How do I get it to install version 2.0.0.14?

Thanks guys in advance :)

---

### Post by iaculallad on 2008-05-26
> **TheAJKMan said:**
> okay, the version displayed in Firefox is now 2.0.0.7, but on the site it's shown to be 2.0.0.14, the above described method has not updated it to that version. What now? How do I get it to install version 2.0.0.14?

Thanks guys in advance :)

Once you input the command:

Code:

> sudo apt-get install firefox
sudo apt-get upgrade

---

### Post by TheAJKMan on 2008-05-26
As soon as I've type in the "sudo apt-get install firefox" command in the terminal window, this is what it looks like,and as far as I understand it, nothing has been changed/updated.

theajkman@theajkman-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
theajkman@theajkman-desktop:~$ 

When I go to Help -> About in firefox it shows version as being 2.0.0.6 now :(

---

### Post by iaculallad on 2008-05-26
> **TheAJKMan said:**
> As soon as I've type in the "sudo apt-get install firefox" command in the terminal window, this is what it looks like,and as far as I understand it, nothing has been changed/updated.

theajkman@theajkman-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
theajkman@theajkman-desktop:~$ 

When I go to Help -> About in firefox it shows version as being 2.0.0.6 now :(

Code:

> sudo apt-get upgrade

Or simply open up firefox, Click on Help->Check for Updates. That could do the update.

---

### Post by TheAJKMan on 2008-05-26
Okay, I typed in both those commands and still no upgrade. :( Here is what was said each time, and this was done when Firefox was closed altogether.

theajkman@theajkman-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
theajkman@theajkman-desktop:~$

theajkman@theajkman-desktop:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
theajkman@theajkman-desktop:~$

Would it help if I rebooted my machine and tried again?

---

### Post by iaculallad on 2008-05-26
If you want the latest version of firefox (Beta I suppose), install it using:

Code:

> 
sudo apt-get update
sudo apt-get install firefox-3.0 

---

### Post by TheAJKMan on 2008-05-26
Sorry, forgot to mention that the Firefox-Help-Check for Updates button is greyed out. Don't want to mess around with Beta's just yet, wanna get the hang of installing/updating software first, then will mess with Beta's and RC type software :)

---

### Post by TheAJKMan on 2008-05-26
Ok, seems that the issue has been resolved now. Tired it again after finishing d/l Thunderbird and it suddenly worked fine. Am now up to date :) 

iaculallad, thanks for your patient helping out of a newb, it is much appreciated :)

---

### Post by oldos2er on 2008-05-26
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by TheAJKMan on 2008-05-30
Thanks oldos2er, only just seen your reply to this query of mine, have bookmarked the page for further reading.

---

