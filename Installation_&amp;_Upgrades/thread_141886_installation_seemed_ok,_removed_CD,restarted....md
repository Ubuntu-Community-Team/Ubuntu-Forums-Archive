---
title: "installation seemed ok, removed CD,restarted..."
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by tinonetic on 2006-03-09
I installed and partitioned correctly, I think. Problem arose when it said remove CD and it restarted. It gets stuck where it says

Loading Ubuntu
...

It dosent go any further from that.
I thought it's because of my very old PC... best I can afford for now (yeah, i'm in the other side of the devide)
anyway, these are the specs:

166MHz P1
180MB RAM
CDROM

I installed the /,/tmp,/home and /swap directories on a 3,4GB harddrive

I had no error, re-installed from another CD, still nothing.

Could anyone help.

I picked up a suggestion elsewhere that one can install server then try installing the desktop using

sudo apt-get install ubuntu-desktop

If I do manage to get through that, would anyone know how I could install Mono? If at all possible

Thanx!

---

### Post by taurus on 2006-03-09
How did you partition your HD anyway?  Was / on /dev/hda1, /tmp on /dev/hda2, etc.?  Just so you know, you shouldn't be using Gnome as your window manager since you have only 180MB of RAM.  You can run it but it is so slow you would hate it.  I think you need at least 256MB to get Gnome function properly.  Therefore, type "server" at the prompt and once you have it up and running, install XFce4 or fluxbox and use that as your desktop then,

```

sudo apt-get install xubuntu-desktop
-or-
sudo apt-get install fluxbox

```

---

### Post by cilynx on 2006-03-09
Mono is packaged as well.  Once you're up and running with XFce4 or whichever lightweight window manager you decide to go with, just:
```

sudo apt-get install mono

```

---

### Post by tinonetic on 2006-03-10
[QUOTE=cilynx]Mono is packaged as well.  Once you're up and running with XFce4 or whichever lightweight window manager you decide to go with, just:
```

sudo apt-get install mono

```[/QUOTE]

thanks!

---

### Post by tinonetic on 2006-03-10
[quote=taurus]How did you partition your HD anyway?  Was / on /dev/hda1, /tmp on /dev/hda2, etc.?  Just so you know, you shouldn't be using Gnome as your window manager since you have only 180MB of RAM.  You can run it but it is so slow you would hate it.  I think you need at least 256MB to get Gnome function properly.  Therefore, type "server" at the prompt and once you have it up and running, install XFce4 or fluxbox and use that as your desktop then,

```

sudo apt-get install xubuntu-desktop
-or-
sudo apt-get install fluxbox

```[/quote] Thanx!

The other problem is that I'm not sure what directories I should create, in what sizes or ratios and leaving out which ones. ie how big should any one of /,/home,/var,/usr,/swap (swap has to be as big as the memory,right?),/tmp
I dont know whether /var,/usr,/tmp are necessary and I dont know what their uses are. I think it would help if i knew.

This is the partition table



[B]directory                                                                partition                                                                           ~size
[/B]-------------------------------------------------------------------------

/                                     **| **                                       /dev/hda1             **| **               900MB

/swap                              **| **                                 /dev/hda2                    **| **     180MB

/home                              **| **                                 /dev/hda3                    **| **    1GB

/tmp                                **| **                                  /dev/hda4                                                                  500MB

/var                                 **| **                                 /dev/hda5                    **| ** 250MB

                         
/usr                                 **| **                                /dev/hda6                     **| ** 250MB

-------------------------------------------------------------------------


thanx again!

---

### Post by tinonetic on 2006-04-03
i managed to finally install it. but I have two problems now.

**1-**Grub correctly identified that I have Windows 98 installed. It included it in the bootloader menu. Problem now arises when I select Windows 98. It has the following error:
> Command line Iine interpreter not found. Please state the command line interpreter (e.g. C:\Windows\COMMAND.COM)
A>

The error may not be the exact words but thts what it says.
I've tried everything I could think of. Inserted the Windows 98 CD, I couldnt see the C drive. Re-installed Ubuntu 4 times and gave up. There's no fixmbr in Windows 98. How do I solve this. I'm really worried about my data. F1!!!!!

**2-**I Installed the default Ubuntu installation. IE the one that includes the desktop. I didnt see any errors but I still get command line. I tried xtart and xconfig, I didnt achieve anything. Switched to runlevels using CTRL+F-key, still no desktop. If I try CTRL+F7 its just a blank screen...

anyone?

---

