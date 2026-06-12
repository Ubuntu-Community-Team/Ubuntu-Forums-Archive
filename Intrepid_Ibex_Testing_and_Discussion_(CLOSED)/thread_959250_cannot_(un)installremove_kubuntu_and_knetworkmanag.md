---
title: "cannot (un)install/remove kubuntu and knetworkmanager"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bro on 2008-10-26
I'm working on Intrepid. Gnome works fine. I thought I'd try to: 

```
sudo aptitude install kubuntu-desktop
```

That installed a lot of KDE stuff but not the desktop. In synaptic the kubuntu-desktop remained in status uninstalled. On reboot I couldn't select KDE even though I tried to install kubuntu-desktop from synaptic. It did start knetworkmanager in Gnome (which didn't work)

Since it didn't work anyway I uninstalled a lot of KDE packages via synaptic to get rid of them.

On reboot however it started knetworkmanager again (which still didn't work). I just put turned it off in Sessions because I cannot uninstall it. Synaptic thinks it is unintalled! and "sudo aptitude purge knetworkmanager" offered to uninstall a bunch more kde packages. But knetworkmanager is still installed!

```
me@my-laptop:~$ whereis knetworkmanager
knetworkmanager: /usr/bin/knetworkmanager /usr/share/man/man1/knetworkmanager.1.gz
me@my-laptop:~$ sudo aptitude purge knetworkmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

1. How do I uninstall knetworkmanager?
2. How to find out if there are more packages installed that apt and synaptic don't show?
3. Can this database from apt/synaptic be rebuild somehow?
4. Why did apt and synaptic at some point show contradictory information?
5. Why does Synaptic still not show a list of 'installed programs ordered by install date' so that it is easy to remove the last installed packages?'

---

### Post by BGrigg on 2008-10-26
I was in the same boat, and found this:

[http://psychocats.s465.sureserver.com/ubuntu/puregnome](http://psychocats.s465.sureserver.com/ubuntu/puregnome)

Psychocats is worth bookmarking, for sure!

---

### Post by bro on 2008-10-26
sorry but that doesn't do it. It is just a sum of all programs to remove. But apt doesn't remove knetworkmanager with apt-get remove / aptitude remove (or 'purge'). It looks like a bug really...

---

### Post by BGrigg on 2008-10-26
Well, it worked for me! Perhaps becuase you started removing programs in a hit or miss fashion, it broke the uninstall routine?

---

### Post by gjoellee on 2008-10-26
I fyou want ot remove all the KDE software:
```
sudo apt-get remove kde*
```

---

### Post by bro on 2008-10-26
I don't want to remove all. Things like Amarok i like. I just want to remove one program now: knetworkmanager, and it just isn't going away.

---

