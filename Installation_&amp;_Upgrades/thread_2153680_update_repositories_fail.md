---
title: "update repositories fail"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by gweinstein on 2013-06-11
Seems to be some problem with some repositories. Here are the warnings at the end of the update command output:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 3BDAAC08614C4B38 Launchpad otto06217

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)


W: Failed to fetch [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/Release](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu/dists/precise/Release)  


W: Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-amd64/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-amd64/Packages)  404  Not Found [IP: 74.125.237.128 80]


W: Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages)  404  Not Found [IP: 74.125.237.128 80]




Any clue what to do?

Thanks in advance!

---

### Post by fantab on 2013-06-11
Try:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update && sudo apt-get dist-upgrade
```

If you still get Errors then post the output of '*sudo apt-get update*'.

---

### Post by gweinstein on 2013-06-12
Thanks Fantab!

Seems to be fewer warnings and errors, but still a few:

> W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-amd64/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-amd64/Packages)  404  Not Found [IP: 74.125.237.72 80]


W: Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages)  404  Not Found [IP: 74.125.237.72 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.


Let me know if you want to whole output of sudo apt-get update or if this is enough. Thanks in advance!

---

### Post by claracc on 2013-06-12
About the google repositories, where you find the 404 not found error, they aren't in the specified address so you will have to disable them in software sources (unthick).

About the first error surely, there is an error in the line "non-free/binary-amd64/Packages" in your /etc/apt/sources.list file (which is used for updating).

Could you please post your sources.list file in order to fix this error?

After fixing these errors, you will have to run ```
sudo apt-get update
```

---

### Post by gweinstein on 2013-06-12
Thanks claracc!

Indeed, only one error left:

> W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.


Here is my sources.list:

> #############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse


###### Ubuntu Update Repos
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse


###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################


###### 3rd Party Binary Repos


#### Audacity - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BB901940
deb [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) precise main


#### Gimp - [https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp)
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main


#### Google Chrome Browser - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


#### Google Linux Software Repositories - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free


#### Google Linux Software Repositories (Testing) - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add  -
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free


#### LibreOffice - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main




####### 3rd Party Source Repos


#### Audacity (Source) - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BB901940
deb-src [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) precise main


#### Gimp (Source) - [https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp)
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) precise main


#### LibreOffice (Source) - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main


---

### Post by claracc on 2013-06-12
I see two errors in the sources.list file you have posted:

The lines:

#### Google Chrome Browser - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


#### Google Linux Software Repositories - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

These two repositories are not in the pointed addresses, so try to comment the two deb lines, i.e. write a # sign in front each of the two lines:

#### Google Chrome Browser - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
# deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


#### Google Linux Software Repositories - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

After saving new sources.list, try again sudo apt-get update.

---

### Post by gweinstein on 2013-06-12
Thanks claracc! No more errors! :-)

But does that mean my google chrome will no longer be updated? That's my preferred browser. Will there be a way for me to fix that later. Thanks in advance.

Best,

---

### Post by claracc on 2013-06-12
Glad you got fixed your problem.

Yes as you have disable the chrome repository you won't receive more updates, but holding it have not any use since the in the address pointed the software packages are not found.

I t is important to know waht ubuntu are you running in order to add the proper chrome repository to your system.

I have found this link: [http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/](http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/) to install google chrome browser from repository, also there is google documentation: [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/) about their own working repositories.

You can use both links in order to have installed and updated your google chrome browser. Read them carefully

---

### Post by gweinstein on 2013-06-12
Thanks, claracc! All fixed now, and turns out I am now using a different Chrome. I had installed the Chromium from the Ubuntu Software Center, and I think that's the one that added those repositories which were broken.

Now, I am using a brand new google-chrome (stable) which seems to be the right version for this OS. Appreciate all the help (both you and fantab)! Please mark the thread solved, or tell me how to do it.

---

### Post by claracc on 2013-06-12
> **gweinstein said:**
> Thanks, claracc! All fixed now, and turns out I am now using a different Chrome. I had installed the Chromium from the Ubuntu Software Center, and I think that's the one that added those repositories which were broken.

Now, I am using a brand new google-chrome (stable) which seems to be the right version for this OS. Appreciate all the help (both you and fantab)! Please mark the thread solved, or tell me how to do it.

You are very welcome.

Only you can mark your thread as solved. See this link: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) to know how mark the thread as solved.

---

### Post by fantab on 2013-06-12
> **gweinstein said:**
> Thanks, claracc! All fixed now, and turns out I am now using a different Chrome. I had installed the Chromium from the Ubuntu Software Center, and I think that's the one that added those repositories which were broken.

Now, I am using a brand new google-chrome (stable) which seems to be the right version for this OS. Appreciate all the help (both you and fantab)! Please mark the thread solved, or tell me how to do it.

Chromium from Software Center will NOT install those repos/ppas. You must have tried to install Google Chrome from somewhere else that may have left you with those bad links or that when you recreated your sources.list, the bad links got in.

---

