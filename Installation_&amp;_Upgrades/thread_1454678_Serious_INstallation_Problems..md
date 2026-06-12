---
title: "Serious INstallation Problems."
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by msrsooraj on 2010-04-15
I used to use ubuntu 9.10. i had to format my comp for some reasons and then i reinstalled 9.10. then  tried installing some of the important packages like Ubuntu-restricted packages. i gave it a search in Ubuntu software centre and the list came. i clicked on the approproate app and i cant find the "INSTALL" or the "WEBSITE" buttons which were supposed to be there. i tried it with so many apps but i simply cant find the install button. So i tried terminal and it says No such package found. i tried synaptic still no luck.
then i installed Ubuntu 8.10 the same problem. then i tried Kubuntu 9.10. but there i gave it a search in the Ksoftware center. it only shows the installed packages. i cant find the installable app. i tried terminal it says no such package. i tried the firefox installer it says these packages are already installed.
then i downloaded ubuntu 10.04. but this time it says error woth ur internet connection. what should i do???
is there anyway i can fix these probs or do i have to get a new copy of the os??
Thankxxxx

---

### Post by tommcd on 2010-04-15
Reinstall Ubuntu 9.10.
Open a terminal (applications > accessories > terminal) and run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
This will get you all of the updates for 9.10. Keep in mind though, that we are late in the release cycle for 9.10, since it is now April, and 10.04 will be out in about 2 weeks. So there will be a lot of updates for 9.10 after you install it.
Then to install the ubuntu-restricted-extras:
```
sudo apt-get install ubuntu-restricted-extras

```
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Restricted_Extras](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Restricted_Extras)
If you have problems with getting the updates, or installing the ubuntu-restricted-extras, then post the errors here.

For the quick and easy way to install anything in Ubuntu:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

And welcome to the Ubuntu forums!

---

