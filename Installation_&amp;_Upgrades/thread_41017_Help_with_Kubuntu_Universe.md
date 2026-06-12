---
title: "Help with Kubuntu Universe????"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by Matchless on 2005-06-11
Hi,
    I am an absolute novice and have managed to install kubuntu, but want to upgrade OOo to 2.0. After reading the how to's I understand that I must enable the universe and it should be done using sudo cp /etc/apt/sources.list_backup. This works and I can see the file. Then I am supposed to use sudo gedit /etc/apt/sources.list, but  the gedit does not run as I am in KDE! I have tried using kate, but the command comes back with an error  sudo kate /etc/apt/sources.list and the error is:
Error "/var/tmp/kdecache-xxxx" is owned by uid 1000 instead of uid 0
Link points to "/var/tmp/kdecache-root"
Kate Error: Communication problem with kate, it probably crashed.
Thereafter Kate will not work from the KDE desktop and I have to reboot.
I assume that Gedit is for Gnome and that Kate is for KDE? The Ubuntuguide.org gives a guide on how to add extra repositories and how to enable the universe, but this is in Gnome only!
In the Kubuntu. org documentation Sean Wheller gives details on how to use both KDE and Gnome on Kubuntu. He states that one is asked on installation whether one wants Gnome or KDE, I never noticed that and have reinstalled a few times. He also states that the session graphics on startup can give you an option to select either before entering password. I get that, but only get KDE, Default or previous and not Gnome.
I have also read that Kynaptic can be used in KDE same as Synaptic and that one can just go Sudo synaptic and then select system - repositories, then edit to universe in the sources field the same for Kynaptics, but no there is no System - Repositories and I cannot find out how to enable universe!!
Please help me to enable universe and how to get both Gnome and KDE working!!
Thanks
Matchless ](*,)

---

### Post by Hokputooy on 2005-06-11
Have you tried using synaptic to add the repositories?

---

### Post by Xian on 2005-06-11
[QUOTE=Matchless]I have tried using kate, but the command comes back with an error  sudo kate /etc/apt/sources.list and the error is:
Error "/var/tmp/kdecache-xxxx" is owned by uid 1000 instead of uid 0
Link points to "/var/tmp/kdecache-root"
Kate Error: Communication problem with kate, it probably crashed.
Thereafter Kate will not work from the KDE desktop and I have to reboot.[/QUOTE]
Using kate from the sudo command is a no go.
Substitute kwrite instead while in KDE.

```
$ sudo kwrite /etc/apt/sources.list
```

---

### Post by Matchless on 2005-06-12
@Xian,
            Thanks, will give it a go.
Regards
Matchless

---

