---
title: "Error when trying to use the automatic upgrade tool to the latest version of ubuntu"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Fenix on 2007-10-20
Hey all,

whenever I try to update to the latest edition of Ubuntu I get the following error:

[HTML]Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2 Could not resolve 'wine.lowvoice.nl'
Failed to fetch http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz Could not resolve 'wine.lowvoice.nl'[/HTML]

Here is a screenshot of it, if it helps:
[IMG]http://img183.imageshack.us/img183/7627/screenshot1nb7.png[/IMG]

Any ideas?

---

### Post by blank89 on 2007-10-20
I'm getting this too. I thought it was a network problem on my end, but I checked everything and I can't figure it out.

Edit:
Try unchecking that repository from your thirdparty software sources. This error is thrown when apt fails to update the repository list.

---

### Post by nitro99 on 2007-10-20
sorry dude but how do u disable the third party list ?

---

### Post by Fenix on 2007-10-20
> **blank89 said:**
> I'm getting this too. I thought it was a network problem on my end, but I checked everything and I can't figure it out.

Edit:
Try unchecking that repository from your thirdparty software sources. This error is thrown when apt fails to update the repository list.

That worked! Thanks!

---

### Post by elmerfud on 2007-10-20
I had the same problem. 

I went into Adept-> Manage Repositories-> 3rd Party Software and deselected all my 3rd party software entries.  Then it ran without problems. 

I wish I had known this sooner.  I must have started upgrade manager a dozen times before I realized it wasn't a network error.

---

### Post by slappgat on 2007-10-20
Thanks you just solved my problem too :)

---

### Post by spazsui on 2007-10-20
Here's an issue that maybe someone has an idea about.   Update manager doesn't even see the Gutsy 7.10 distribution is available.  It says my system is up to date.  I have it recheck and it still says everything is up to date.  I'm trying to upgrade from 7.04 Fiesty.  So why won't my system see that Gutsy is now available?

---

### Post by spazsui on 2007-10-20
Forgot to mention, obviously I do have a working intenet connection otherwise I wouldn't be posting this right now.

---

