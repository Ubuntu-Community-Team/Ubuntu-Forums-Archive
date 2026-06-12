---
title: "Can't upgrade from Feisty to Gutsy"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by astrobit on 2007-11-18
I can't update... :(
whenever i use the update manager i get this message at the end:

-----------------------------------------------------------------------------------------------------------------------
The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
-----------------------------------------------------------------------------------------------------------------------

does anybody knows why? :confused:


Launchpad Log:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/163710](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/163710)

---

### Post by zvacet on 2007-11-19
```
sudo aptitude update && sudo aptitude upgrade
```

Then try to upgrade with upgrade manager.

---

### Post by Kumera on 2007-11-19
I also cannot upgrade from Feisty to Gutsy, but the message I get is:
"Failed to fetch [http://packages.medibuntu.org/feisty/dists/free/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/feisty/dists/free/non-free/binary-i386/Packages.gz) 404 Not Found
"

A check with the browser confirms that there is no directory starting "http://packages.medibuntu.org/feisty/dists/..." although there is a tree under "http://packages.medibuntu.org/dists/feisty/..."
(although I am not sure why the system would need to acces any such when it is supposed to be upgrading to "gutsy")

Any suggestions as to how I can get past this glitch?

---

### Post by zvacet on 2007-11-19
```
gksudo gedit /etc/apt/sources.list
```

put # sign in front of  medibuntu lines and any other unofficial you added.Save and close.

```
sudo aptitude update
```

Try to upgrade again.

---

### Post by Kumera on 2007-11-20
That worked, thanks!

---

### Post by zvacet on 2007-11-20
If you didn´t do it until now you can add this lines to your sources list

```
gksudo gedit /etc/apt/sources.list
```


deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Save and close.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

```
sudo aptitude update
```

---

### Post by Cariboo1938 on 2007-11-28
> **zvacet said:**
> If you didn´t do it until now you can add this lines to your sources list
```
gksudo gedit /etc/apt/sources.list
```
[COLOR="Red"]deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner[/COLOR]

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free


UPGRADE PREPARATIONS.
Right now I run "Feisty 7.04-amd64" and I'm thinking to upgrade to "Gutsy 7.10-amd64". 
To avoid as much trouble as possible - DVD playback issues, nvidia and Xserver issues - I want to make sure that I do the proper preparations before I hit the 'Upgrade' button In the 'Update Manager Menu. I read through the posts at the Forum concerning this issue and I found this post. Here is my question:
What would the repository [COLOR="Red"]"deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner"[/COLOR] be necessary for?

Thanks in advance
Cariboo

---

