---
title: "Incomplete installation: How to pick up where it left off?"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by Jamie Jackson on 2006-11-15
Is there any way to resume a half-complete installation? I did a network Edgy installation that was interrupted after selecting timezone and entering user information.

Now, when I boot into Ubuntu, I'm dropped into the command line. I can login, but I don't know what I need to do from there to finish the installation.

Is there a way to pick up where I left off? [This was a long process (it took two weeks to get this far), and might weep if I have to completely redo it. :cry: ]

Thanks,
Jamie

P.S. I posted a [thread]("http://ubuntuforums.org/showthread.php?t=299932") earlier, but maybe I described my problem in an unattractive way. I'm trying a simpler description.

---

### Post by taurus on 2006-11-15
I guess you can run these two commands from the prompt!

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by Jamie Jackson on 2006-11-15
Thanks for the reply!

```
# aptitude update
# <snip about 15 lines of Get/Hit, etc.>
# Fetched 3B in 0s (8B/s)
# Reading package lists... Done
```

Looks promising

```
# aptitude dist-upgrade
# <snip>
# No packages will be installed, upgraded, or removed.
# 0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
# Need to get 0B of archives. After unpacking 0B will be used.
```

Hmm, not sure what to make of that.

How'd that look to you? What to do next?

I know nothing. :confused: 

Thanks again,
Jamie

---

### Post by taurus on 2006-11-15
Are you at the console right now or does it boot into GUI login screen?  If you are at the console, no X, then install Gnome with

```
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by Jamie Jackson on 2006-11-15
In the console...

Well the first command wants >500MB of stuff, so that seems like good news.

I'll update the thread in a half hour, or however it long it takes.

Big thanks again!!!
Jamie

---

### Post by taurus on 2006-11-15
So looks like you only have the server running on your machine right now so go for the Gnome.  Then, install anything else you need later.  If you are not sure about the name, you can always use synaptic to search for it.

---

### Post by Jamie Jackson on 2006-11-15
ubuntu-desktop will have Gnome, correct?

Also hmm, this download could take a while... Is there a way to do this apt-get stuff from a machine on my network? I could set up HTTP or FTP (hitting the alternate install disc, I guess). I've go the HTTP/FTP server part covered, but I don't know if I could do such a thing with apt-get, nor how to tell apt-get to hit my local(ish) repository. Do you know?

---

### Post by taurus on 2006-11-15
Yes, ubuntu-desktop will give you Gnome.

I believe you can install Gnome from either desktop CD/LiveCD or the alternate CD.  Insert the CD and at the prompt, run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by Jamie Jackson on 2006-11-16
```
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

This did the trick! Thank you!!!

It now boots to Gnome. :-D

Last question: Is this now a normal ubuntu installation, or does the normal installation have more packages?

Thanks!
Jamie

---

### Post by taurus on 2006-11-16
> **Jamie Jackson said:**
> ```
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

This did the trick! Thank you!!!

It now boots to Gnome. :-D

=D> 

> Last question: Is this now a normal ubuntu installation, or does the normal installation have more packages?

Thanks!
Jamie
Should be the same.  Again, if you need to install something else, just use synpatic/apt-get/aptitude to install it on your machine.  Don't forget to enable both universe & multiverse in /etc/apt/sources.list so that there are more apps available for you to install.  Open a terminal, Applications -> Accessories -> Terminal, and open an editor.  While in there, remove the # sign in front of those lines.

```
gksudo gedit /etc/fstab
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ChadMC on 2006-11-16
Hello.
I'm kind of in the same boat that he was in, except not quite as far. Grub never got to install, so I can't boot to the command prompt? Is there someway for me to get grub installed? I'm sure there is some way I can use the CD and into rescue mode and install it from there, but I'm not so sure..

EDIT:
Actually I went into rescue mode, mounted root on hda1, and did: apt-get upgrade
It seems to have picked up installing the packages where I left off. So we'll see what happens.. I still don't know if it will install grub, but I guess I could do that myself from the command line.

---

### Post by taurus on 2006-11-16
Yes, you can install GRUB from a command line with

```
grub-install /dev/hda
(assuming you have created /boot/grub/menu.lst first...)
```

---

