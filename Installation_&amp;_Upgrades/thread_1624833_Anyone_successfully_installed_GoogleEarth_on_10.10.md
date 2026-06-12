---
title: "Anyone successfully installed GoogleEarth on 10.10?"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by demonboy on 2010-11-18
... because I keep failing. I know in the official documentation it is not yet available for 10.10... is this correct because I keep coming across guides on how to do it, like this one:

[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

Unfortunately after downloading the file it didn't work for me.

---

### Post by dino99 on 2010-11-18
enable canonical partner repo into synaptic, and update, then it can be installed

---

### Post by oldos2er on 2010-11-18
Yes, I've installed it from the *bin file (v5.2.1.1588) 
downloaded from [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

---

### Post by desnaike on 2010-11-18
> **demonboy said:**
> ... because I keep failing. I know in the official documentation it is not yet available for 10.10... is this correct because I keep coming across guides on how to do it, like this one:

[http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

Unfortunately after downloading the file it didn't work for me.

I tried the site and installed google earth on kubuntu 10.10 without problems look in your home folder for the deb file it created and double click it enjoy.

---

### Post by freshmeatz on 2010-11-18
synaptic package manager, not one issue...5.1.3533.1731-0medibuntu0.9.10.1

---

### Post by raymondvillain on 2010-11-18
A question for dino99.  You suggest
"enable canonical partner repo into synaptic, and update, then it can be installed"

How do I do that?  I opened synaptic, and under the settings tab I clicked on repositories, but it's not clear to me which choice is appropriate for canonical partner repo.

When I go to the directory with GoogleEarthLinux.bin and try to run it with the "sh" command I get this error message:

"setup.data/setup.xml:1: parser error : Document is empty"
and
"setup.data/setup.xml:1: parser error : Start tag expected, '<' not found"
and
"Couldn't load 'setup.data/setup.xml'"

---

### Post by Crempel on 2010-11-19
Thanks desnaike; I used the link you quoted and the installation worked without any problem on Maverick 64-bit. I think it's the "--force" parameter that is required. On previous atempts I also had the "file empty" message.

---

### Post by oldos2er on 2010-11-19
> **raymondvillain said:**
> When I go to the directory with GoogleEarthLinux.bin and try to run it with the "sh" command I get this error message:

"setup.data/setup.xml:1: parser error : Document is empty"
and
"setup.data/setup.xml:1: parser error : Start tag expected, '<' not found"
and
"Couldn't load 'setup.data/setup.xml'"

[http://www.google.com/support/forum/p/earth/thread?tid=6f59e15bf811d4e2](http://www.google.com/support/forum/p/earth/thread?tid=6f59e15bf811d4e2)

---

