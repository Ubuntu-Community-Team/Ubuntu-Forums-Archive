---
title: "Accidentally deleted /etc/init.d/gdm  help"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by cashmoney on 2008-11-15
Like I said in the title I installed the latest kernel 2.6.27 in Hardy and I was going to install the nvidia drivers from scratch.  I went to delete /etc/init.d/nvi* and due to lack of sleep and not really paying attention I typed gdm and hit enter.  I tried uninstalling gdm and re-installing gdm then I move the gdm file from my desktop to my laptop using scp and migrated it to /etc/init.d/ and it didn't help.  Any suggestions?

Thanks
   Nate

---

### Post by cdtech on 2008-11-15
What do you get with this command:
```
sudo dpkg --audit
```

---

### Post by ad_267 on 2008-11-15
Try:

```
sudo dpkg -P --force-depends gdm
sudo aptitude install gdm
```

That will purge the gdm package without uninstalling packages that depend on it and then reinstall it.

---

### Post by cashmoney on 2008-11-15
> **ad_267 said:**
> Try:

```
sudo dpkg -P --force-depends gdm
sudo aptitude install gdm
```

That will purge the gdm package without uninstalling packages that depend on it and then reinstall it.

That worked great thanks a lot.  Is there any other reason to using Aptitude over apt-get other than it removes the dependencies for you?

---

### Post by cdtech on 2008-11-15
> using aptitude over apt-get are largely irrelevant if you're using Edgy Eft (6.10), Feisty Fawn (7.04), or any future version of Ubuntu.

the new version of apt-get from 6.10 has a function that allows you to remove unused dependencies when removing an application: 
```
sudo apt-get autoremove appname
```

---

### Post by cashmoney on 2008-11-15
Awesome thanks for the quick replies.

---

