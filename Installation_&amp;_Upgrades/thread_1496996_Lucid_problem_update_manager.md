---
title: "Lucid problem update manager"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by Coppper on 2010-05-30
Hi ,
When trying to run update manager , I'm getting this error 
NO_PUBKEY D6B6DB186A68F637

Today I've update from Hardy to Lucid

---

### Post by wojox on 2010-05-30
Import the key:

```

gpg --keyserver hkp://subkeys.pgp.net --recv-keys D6B6DB186A68F637  
gpg --export --armor D6B6DB186A68F637 | sudo apt-key add -

```

---

### Post by Coppper on 2010-05-30
I have alrealdy tried that , bun it does not work
I get this message
gpgkeys: HTTP fetch error 7: couldn't connect to host

---

### Post by abdusamed on 2010-06-29
> **Coppper said:**
> I have alrealdy tried that , bun it does not work
I get this message
gpgkeys: HTTP fetch error 7: couldn't connect to host


same here

---

### Post by ilabor on 2010-12-27
> **Coppper said:**
> Hi ,
When trying to run update manager , I'm getting this error 
NO_PUBKEY D6B6DB186A68F637

Today I've update from Hardy to Lucid

thats the jDownloader repo:

edit file /etc/apt/sources.list (put # in front of both deb and deb-src)

# jdownloader
#deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main
#deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main

---

### Post by earthmeLon on 2011-01-17
> **ilabor said:**
> thats the jDownloader repo:

edit file /etc/apt/sources.list (put # in front of both deb and deb-src)

# jdownloader
#deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main
#deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) maverick main


This doesn't actually *solve* anything.  The whole point of adding this to his source list is so that he can install/keep up to date with JDownloader.

To fix your problem, try running this command:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
```

This will add the key for JDownloader.  If you commented those lines, be sure to un-comment them.


Edit:  If you turn your computer off, it will also solve your problem, but I'm sure that it's not the solution you were looking for, either.

---

