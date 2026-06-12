---
title: "Downgrading Transmission 2.0 to 1.93"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by razlken on 2010-09-12
UPDATE: Actually it's version 2.04 not 2.0, guess the site i followed was a little dated.

Hi,

so i was a little hasty in upgrading Tranmission to version 2.0 and after a while i noticed that the new version is really slow especially for public torrents my question is; is it possible to downgrade to version 1.93? after some time searching around the net i can't find an asnwer to that question.

i followed these command to install the new version.

```

$ sudo add-apt-repository ppa:transmissionbt/ppa
$ sudo apt-get update
$ sudo apt-get upgrade
```

any help in the matter would be extremely appreciated and thx in advance :D

---

### Post by zpletan on 2010-09-12
See ppa-purge: [https://code.edge.launchpad.net/~xorg-edgers/ppa-purge/ubuntu](https://code.edge.launchpad.net/~xorg-edgers/ppa-purge/ubuntu)

---

### Post by pastalavista on 2010-09-12
You should be able to do what you ask in Synaptic PM (System-->Administration-->Synaptic Package Manager)
Under settings/repostiores you can remove the new ppa. Search for transmission, completely remove the newer and reinstall the older.

---

### Post by razlken on 2010-09-13
Thx to both of you i was able to downgrade!! hopefully the next ubuntu can make the operation less confusing and long :D

---

### Post by nexus6replicant on 2012-01-08
I had a similar problem too.
Was using Transmission 2.03 version.
Liked the fact that when you d***loading it displayed 2 decimal places for accuracy and in the speed status bar.
Tried the 2.33 version via synaptic install and upgrade inc update.
Didn't like the fact that it only showed one decimal space.
So downgraded via synaptic package manager by unchecking the settings>repositories namely the other software tab [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) uncheck and [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) uncheck removed the launchpad ppa for transmission from the authentication tab.
Then removed transmission completely via synaptic package manager.

Then reinstalled Transmission via Ubuntu software centre and voila back version 2.03!

There's nothing more annoying when you are 99.9% finished a file but when you have the extra decimal space it makes a huge difference especially when a file is greater than 1gig.

---

