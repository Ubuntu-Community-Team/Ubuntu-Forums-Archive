---
title: "installing seahorse"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by williamburn on 2007-05-26
I am running VMware with a Ubuntuu 7.04 server image, and trying to isntall seahorse.  Can anyone help with the commands and or how to install seahorse.  I am very new to linux and have been searching forums and wikis for the answer.  Any help would be greatly appreciated

Currently from the shell i am logged in as notroot

notroot@ubuntu:~$
I type dir and see my files that i want to load, but need to load them and have them available when i launch startX

so: notroot@ubuntu:~ dir ::::shows
Desktop seahorse-1.0.1  seahorse-1.0.1.tar.gz

Thank you for helping this noobsauce linux user!

---

### Post by williamburn on 2007-05-26
System &#8594; Administration &#8594; Synaptic Package Manager

I think I found my answer

---

### Post by Hendrixski on 2007-08-03
> **williamburn said:**
> I am running VMware with a Ubuntuu 7.04 server image, and trying to isntall seahorse.  Can anyone help with the commands and or how to install seahorse.  I am very new to linux and have been searching forums and wikis for the answer.  Any help would be greatly appreciated

Currently from the shell i am logged in as notroot

notroot@ubuntu:~$
I type dir and see my files that i want to load, but need to load them and have them available when i launch startX

so: notroot@ubuntu:~ dir ::::shows
Desktop seahorse-1.0.1  seahorse-1.0.1.tar.gz

Thank you for helping this noobsauce linux user!

you'll want to use ls instead of dir, it's more flexable
if you want to install things, as a beginner synaptic is the way to go, otherwise try the dirty way which is using apt-get
```
  sudo apt-get install myProgram
```

If you want to find it just search using apt-cache
```
 sudo apt-cache search searchParameter
```

enjoy

---

### Post by Hendrixski on 2007-08-08
Also, when installing seahorse, you may want to change the option where it remembers your passphrases.  This just leads to a whole slew of problems, such as debuild and dpkg-buildpackage not being able to ask you for your password (you also need to install pinentry-gtk2 for that, but it won't work if seahorse thinks it remembers your password).

---

