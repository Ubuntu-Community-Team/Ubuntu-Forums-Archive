---
title: "Installation Problem on Dell Inspiron 1000"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by nullfactor on 2007-08-08
As the subject would indicate, I have a Dell Inspiron 1000 laptop that I would like to install Feisty on.  When I pop in the Live CD, it takes literally 2.5 hours to come up to an error that says:

> There was an error starting the GNOME Settings Daemon.  Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in.

After that, I boot up to a blank desktop with only a File Browser window that shows the desktop icons of "Examples" and "Install".  When I double-click "Install", and after waiting 6 hours, nothing happens except for an occasional flicker from the CD-ROM drive and the hard drive.

Specs are:

2.3GHz Intel Processor
256MB RAM
30GB Hard Drive

I've tried 3 other install discs, thinking that it could be media issues... same problem with all discs.

Any thoughts?

Thanks.

---

### Post by foxholeunder on 2007-08-08
Perhaps try an alternate installation version of 7.04 such as Xubuntu, for something lighter on the memory requirements.

The main trouble I think you are experiencing is lack of memory. 7.04 recommends 256 as minimum for runtime. When you load the "live" cd you are loading a fully functional 7.04 desktop environment into memory, leaving virtually nothing left over for installation.

I would suggest Xubuntu with the Xfce desktop environment as it only requires 128megs.

Otherwise if you want the Gnome desktop you will need to install Ubuntu 6.06 LTS, or better yet, install Xubuntu 6.06. You will find it very responsive and quick!

6.06 is the major supported release of Ubuntu, support is for 3years for desktop versions and 5years for server versions.

---

### Post by merlinus on 2007-08-08
FWIW, I have installed ubuntu on a 256MB RAM laptop via the text-based alternate install cd.

Alternatively, you can install xubuntu and then add gnome-desktop if desired.

-merlin

---

### Post by foxholeunder on 2007-08-09
Good point merlinus!

install Xubuntu and if you desire the gnome environment

fire up a terminal and type:
```

sudo apt-get install ubuntu-desktop

```

This will install the Gnome GUI

alternately type:
```

sudo apt-get install kubuntu-desktop

```

this will give you the KDE GUI

Reboot to set the new configurations and at the login screen change from Xfce to Gnome and you will load into Gnome rather than Xfce, You can also choose to make this the default environment from here as well.

---

