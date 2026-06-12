---
title: "Google Earth not installed in Ubuntu 10.10"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by gpdas on 2010-11-25
Hi, I am not able to install Google earth in 10.10 version. 
Any help will be appreciated.

---

### Post by Swagman on 2010-11-25
[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

or use medibuntu repos

---

### Post by gpdas on 2010-11-25
In my case nothing like 

googleearth-package

is displayed when I search.

---

### Post by I'mGeorge on 2010-11-25
if you have the x86-64 Ubuntu architecture than you will need to install the ia32 libs before before doing something like 
```

make-googleearth-package --force

```

If you wanna use the googleearth-package from your repos

---

### Post by Swagman on 2010-11-25
> **gpdas said:**
> In my case nothing like 

googleearth-package

is displayed when I search.


Sounds like you haven't switched on the multiverse.

[img]http://localhostr.com/files/YiSYFsI/Ubuntu121.jpeg[/img]



or use Synaptic

---

### Post by gpdas on 2010-11-25
I could not find googleearth-package. 
So I directly run 
sudo make-googleearth-package [COLOR=#008000]--force
Then
Alt F2
Then Install
[/COLOR]Google earth icon came in Applications->Internet.
But when I click on it, it opens and terminates immediately.

---

### Post by Swagman on 2010-11-25
> **gpdas said:**
> I could not find googleearth-package. 
So I directly run 
sudo make-googleearth-package [COLOR=#008000]--force
Then
Alt F2
Then Install
[/COLOR]Google earth icon came in Applications->Internet.
But when I click on it, it opens and terminates immediately.

turn off the startup tips..You'll have to be quick though !!

---

### Post by gpdas on 2010-11-29
[SOLVED] Thanks Swagman. I unchecked the 'Start up Tips'. Now my problem is over.

---

