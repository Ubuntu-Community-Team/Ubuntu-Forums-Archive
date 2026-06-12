---
title: "Problem with Automatix NTFS/FAT32 read/writer"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by crazyblackmage on 2007-05-10
I was installing the Automatix NTFS/FAT32 read/writer in Feisty, it finished installing, and a message box said I should restart my computer. I went to the shutdown button, and the options for shutdown and restart were missing! Now, my windows volumes are unmounted, I don't know how to remount them, I can't shutdown or restart without manually hitting the power button, and to top it off, Beryl isn't working correctly. Can anyone help?

---

### Post by jjmatt on 2007-05-10
> **crazyblackmage said:**
> I was installing the Automatix NTFS/FAT32 read/writer in Feisty, it finished installing, and a message box said I should restart my computer. I went to the shutdown button, and the options for shutdown and restart were missing! Now, my windows volumes are unmounted, I don't know how to remount them, I can't shutdown or restart without manually hitting the power button, and to top it off, Beryl isn't working correctly. Can anyone help?

well to shut down the computer you can simply Alt+F2 then type

```
gnome-terminal
```

in terminal type one of the next four lines to reboot, shutdown, reboot in 5 minutes shutdown in 5 minutes respectively

```
sudo reboot
sudo halt
sudo shutdown -rt secs 5
sudo shutdown -ht secs5
```

As for automatix, if I were you I would avoid using it as I've heard nothing but bad things about it and easyubuntu If you get this problem resolved you should try 

```
sudo apt-get install ntfs-config
```

then go to system tools > ntfs configuration tool > enable read/write

---

### Post by Saphira on 2007-05-11
Automatix is a waste of your time and energy. Refer to these sites for more formalized documentation -- [http://wiki.ubuntu.com](http://wiki.ubuntu.com) [http://ubuntuguide.org](http://ubuntuguide.org) [http://doc.gwos.org](http://doc.gwos.org).

Automatix is known for breaking systems and you'll find that you really don't need it. It may also make upgrading your system later difficult. With Feisty most of the stuff you'll use Automatix to install is already a one click install either via add/remove applications or by referral to one of the above sources.

---

### Post by kelvin spratt on 2007-05-11
That's strange i use the automatix ntfs 3g and i find it a much better setup than the Fiesty version as it solves all issues with write permission on my system. I once had a problem with shut-down on 6.10 but i just restarted Gnome in safe mode or what ever it is and that was that.

---

### Post by crazyblackmage on 2007-05-11
Thanks, I'll just use the add/remove programs. How do you uninstall Automatix? It's not in the Add/Remove list...

---

### Post by taurus on 2007-05-11
Applications -> Accessories -> Terminal
```
sudo aptitude --purge remove automatix2
```
Then, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove everything in the Automatix section.  Save it.  Then run

```
sudo aptitude update
sudo aptitude upgrade
```
And if you want to install ntfs-3g, use this guide.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

