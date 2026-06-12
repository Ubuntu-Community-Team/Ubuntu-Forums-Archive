---
title: "Basic only installation of 10.04.2 Server on RAID1"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by netwidget on 2011-06-02
I am trying to install ubuntu 10.04.2 Server basic (command line only) on 2 SATA 500GB HD's while using the installer to configure the 2 HD's a software RAID1 (all this at install).  I searched the net and found a site recommending to use the alternate install CD for this to access additional RAID configuration options.  

I used the Alternate CD to do this and was able to set up the system, however it does not give any options to forgo installation of the desktop environment.  Is there an another alternate CD for Server or is the only option to also install the desktop environ.  

Is there a way to uninstall the desktop so that all I have is a command line interface?

---

### Post by netwidget on 2011-06-02
I found a solution to boot into text mode in instead of booting the GUI.  I found it here:

[http://andrew.org/index.php/archives/2010/05/07/ubuntu-10-04-lucid-lynx-boot-in-text-mode/]("http://andrew.org/index.php/archives/2010/05/07/ubuntu-10-04-lucid-lynx-boot-in-text-mode/")

1.  open the following in a text editor (I used nano) as root:

```
$ sudo nano /etc/default/grub
```

2.  Find the following line :

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

3.  And change to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
```

4.  Also if you want to change the text resolution (set to use smaller font size) uncomment the following line and change the resolution to your preferred resolution (make sure your video card and monitor can support the new res):

```
GRUB_GFXMODE=640x480
```

To *- example for 1024x768*

```
GRUB_GFXMODE=1024x768
```

5.  Save file and exit, then update grub (run as root):

```
$ sudo update-grub
```

Regarding the Alternate Installation CD it seems odd that this CD would have all of the extended options for RAID configuration but not provide the option to install only the basic server.  I would think that the Server Installation would be the more pat choice for the more detailed RAID installation along with the additional options to install or not install add on or GUI environments.

Just a thought - It would have saved me a lot of lost time.

---

