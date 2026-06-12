---
title: "installing software via terminal"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by jjb945025 on 2011-02-26
Hello all.I was wondering if someone out ther could give me the steps on installing wine 1.2 via the terminal..I've tried running the config,make-install files inthe terminal but don't see that wine is installed uner applications.btw I am running lucid lynx and never was successful installing software via the terminal,I. Always used synaptic package manager.I can't do that this time because I haven't internet access on the lucid lynx computer,I should though once I get wine running because. I have a driver I need to use to let this android phone be recognised by the lucid lynx computer..the phone has hotspot capability but first I need to get wine 1.2 installed and running..any help would be greatly appreciated...

---

### Post by davidmohammed on 2011-02-26
wine will not help with your internet connection problems - wine and device drivers will unlikely work.

use a google search such as "use android phone as modem for ubuntu" to enable your android phone to act as a modem for ubuntu.

---

### Post by jjb945025 on 2011-02-26
Dude..the post was a question on how to install wine 1.2.guess that's all I should've said..the drivers I have may make things work but I can't install them without wine 1.2 being installed.again, can anyone teach me how to install wine 1.2 via terminal???

---

### Post by davidmohammed on 2011-02-26
sudo apt-get install wine1.2

you really dont want to try installing this one manually - it pulls in various stuff from the internet.

You'll need to get a working internet connection first.

---

### Post by jjb945025 on 2011-02-27
I tried that, I get an error.can't paste the error cause I'm on the android phone right now..

---

### Post by jjb945025 on 2011-02-27
It seems there is no way to install software without an internet connection;I don't see why...I'm having a problem adding winev1.2 to the repositories.wine 1.2 was put onto the desktop from my thumb drive..wtf. do I do???

---

### Post by davidmohammed on 2011-02-27
as I said before - wine1.2 downloads stuff from the internet (for example true type fonts from sourceforge) - you cant just install the deb package you've downloaded on your memory stick.

You'll need to tether ubuntu with your android phone first as a modem.

---

### Post by AlexDudko on 2011-02-27
As it was written before wine won't let you connect to Internet.
Instead you should look for the Linux native way creating Internet connection.
This thread will be of some interest for you [http://www.backports.ubuntuforums.org/showthread.php?t=1628531]("http://www.backports.ubuntuforums.org/showthread.php?t=1628531")

---

### Post by jjb945025 on 2011-02-27
Thanks alex but what I did was blacklist the default wireless drivers.I have a driver called "globetrotter" for the 3g network and can't install it because I need wine 1.2 installed,and it won't install...

---

### Post by AlexDudko on 2011-02-28
A windows driver installed in wine won't let you connect to Internet. Have you tried to connect in the Linux way, as it was suggested?
But if you still need **wine**, download the package itself from this [page]("http://packages.ubuntu.com/lucid/wine1.2") and all its dependencies (which you lack in your installation). And install them one by one (dependencies first) using terminal command:
> dpkg -i deb_package_name
You'll need much more packages installed, if you want to compile and install wine from source.

---

### Post by jjb945025 on 2011-03-02
Guys..I tried using the provided linux drivers.obviously they wouldn't work.I received no indication that linux was detecting a signal.well I uninstalled ubuntu 10.04 and installed linux mint 9.the standard wireless drivers in ubuntu were blacklisted by me and I wasn't going to try figuring out how to enable them again.so now I'm using mint 9 and I need to have the hotspot feature enabled again with sprint.ill let ya,s know what happens....

---

### Post by jjb945025 on 2011-03-03
alright guys,i am now online. thanks to my own intuition..but thank you guys for all the help..

---

