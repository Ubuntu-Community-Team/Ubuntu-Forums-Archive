---
title: "I Can't install Netgear Raidar on Ubuntu 11.04"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by Breadalbane on 2011-08-09
I have recently installed Ubuntu on a new (to me) pc and cannot get raidar to install. I have been through both Netgear and Ubuntu forums and tried the solutions offered without success. For instance, if I try to run setup_linux.sh file nothing happens. If I run it in terminal the jre file unpacks but does not find the browsers and terminates when a browser option is selected. I have copied the setup file to the desktop and tried to run it with autorun but all it does is show the files that are in the setup programme. If I run it file in terminal both with and without the sudo command I get a message that the file does not exist.

I have downloaded the latest setup file but the same happens with that as with the file on the provided CD.

Any help would be appreciated.

Aitionn

---

### Post by Hakunka-Matata on 2011-08-09
```
sudo bash setup_linux.sh
```I didn't know what RAIDar was so I found it, downloaded it, and started it, then Ctr C ed out of it, just to test.
I started the Terminal session in my home directory, and therefore had to point to the script file which is in my  /Downloads directory.  

Excuse if I'm being too verbose.............

```

das@Backoffice-10:~$ sudo bash Downloads/RAIDar_Linux.sh
Starting Installer ...
das@Backoffice-10:~$ ^C
```if that's what you want to do.

---

### Post by Breadalbane on 2011-08-09
Thank you and sorry I did not state what raidar is. I was getting a little engrossed in the issue.

I will try what you suggested when work allows and will post the result.

Thanks

A

---

### Post by Breadalbane on 2011-08-10
Hakunka-Matata

Raidar is now up and running and I am delighted. I have recently ditched Windows following numerous blue screens of death.

I now have a fully operational system all based on Ubuntu. (Just need to get the film scanner connected but that can wait for another day)

Thanks very much for your help

Aitionn

---

### Post by Hakunka-Matata on 2011-08-10
Hey, that's great, you can use _[COLOR=Red]**Thread Tools**[/COLOR]_[COLOR=Red][COLOR=Black] to mark this thread SOLVED.  Thanks[/COLOR][/COLOR]

---

