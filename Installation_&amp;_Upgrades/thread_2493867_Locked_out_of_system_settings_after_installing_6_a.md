---
title: "Locked out of system settings after installing 6 apps."
date: 2023-12-27
forum: Installation &amp; Upgrades
---

### Post by smokingwheels on 2023-12-27
Ubuntu 22.04.3 LTS on Asus pro laptop I5 12 GB 1 TB ssd

I have 3 other systems that have all the same apps installed one at a time.
I have just done 2 fresh installs and I'm locked out of system settings. 

sudo apt install -y ssh playonlinux ffmpeg python3-pip fuse libfuse2

Can't upload file in firefox with nextcloud.
I saved the install logs will have a look.

So a 3rd install, I will try apps one at a time and hopefully will have a system.

---

### Post by MAFoElffen on 2023-12-27
If you can post them to a pastebin, I will help look.

One of the things I have found in the past, is if something changes the gnome-control-center settings db to an invalid option for the machine type, then it locks up that database and locks the user out of "Settings". The Gnome Control Center will try to start, see an invalid option, then fail.

If you make a backup copy of that user dconf database file first, you should be able to restore that, then go on from there.

The Gnome Doc's say it is at $XDG_CONFIG_HOME/dconf/... except that is not valid in Ubuntu... In Ubuntu, that VAR is not populated. For Ubuntu it is really located at, and the dconf database file is called $HOME/.config/dconf/user.

Like this:
```

mafoelffen@Mikes-ThinkPad-T520:~$ file $HOME/.config/dconf/user
/home/mafoelffen/.config/dconf/user: GVariant Database file, version 0

```

---

