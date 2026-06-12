---
title: "[SOLVED] Installing Eclipse"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Pioneer5000 on 2008-05-25
Can anyone walk me through installing this and getting it to work, i seem to have it installed but it just gives me a huge error. Ive tried follow a couple of guides but they are all old and don't work. Can anyone help me out?

---

### Post by hbarshak on 2008-05-25
> **Pioneer5000 said:**
> Can anyone walk me through installing this and getting it to work, i seem to have it installed but it just gives me a huge error. Ive tried follow a couple of guides but they are all old and don't work. Can anyone help me out?

there is no need to install it... just download the version you want from: [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)
extract it to a folder and just run it.
just dont forget to make sure you have java installed on your machine.

---

### Post by Pioneer5000 on 2008-05-25
Thanks, lol alot easier then i was expecting it to be, lol expect now im trying to get the PDT extension to work, i downloaded that all in one package thing but it doesnt seem to work.

---

### Post by Dan++ on 2008-05-25
I had trouble too. Into eclipse, go to Help > Software Updates > Find and Install and use the update manager like so:

**From [here]("http://www.eclipse.org/pdt/install.php"):**
> Update Manager - The update manager installation is done via the update manager of the already installed Eclipse.
Go to Help Software Updates Find and Install. Choose the "Search For New Feature to Install" and add a new site with the following link "http://download.eclipse.org/tools/pdt/updates/" and press Next to start the update process. 

---

### Post by Pioneer5000 on 2008-06-01
Ok got it working, pretty easy just download an all in one Eclipse:

[http://downloads.zend.com/pdt/all-in-one/](http://downloads.zend.com/pdt/all-in-one/)

choose the latest version and then just download, make sure java installed

```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```

then extract downloaded Eclipse file and run. To switch to PHP mode do the following, in Eclipse normal screen (not welcome screen) in the top right hand corner click on the Open Perspective button and then click on PHP. Pretty easy but thought i would add this just in case anyone else out there who is new and needed help like me with this.

---

