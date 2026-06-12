---
title: "Post 13.04 installation problems..."
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by stuartbh on 2013-05-05
ALCON,

After installing 13.04 followed by GNOME Classic, I am having some very major problems, any assistance would be appreciated!

1) I am unable to resize the system settings. I tried to edit the file /usr/share/gnome-control-center/ui/shell.ui and change <property name="resizable">False</property> to <property name="resizable">True</property> but it had no effect whatsoever.

2) When programs are minimized they disappear! I mean that usually there is a task bar of programs at the bottom when you minimize a program, that never appears at all -- Just a black bar! I have a black bar at the bottom (I had set a background when I first setup gnome) and there is no way to bring the program back, it just evaporates!

3) There used to be a small virtual desktop switcher in the lower right corner, that is gone entirely, any ideas here?

Unfortunately problem number 2 is big enough that it makes the entire installation of 13.04 unusable for me and will likely impel me to install 12.10 again until I can find a resolution.

Thanks in advance for anyone's help!


Stuart

---

### Post by ibjsb4 on 2013-05-05
Sounds like a install gone bad.  Will a terminal update give you any clues?

---

### Post by stuartbh on 2013-05-05
> **ibjsb4 said:**
> Sounds like a install gone bad.  Will a terminal update give you any clues?

do you mean doing an "apt-get update && apt-get dist-upgrade"?

You know, you might be right entirely actually! I remember that the installation had a problem installing kismet (during the upgrade) and it complained about the installation completing properly. Perhaps a fresh install again is a good idea.


Stuart

---

### Post by ibjsb4 on 2013-05-05
Yep an update && dist-upgrade may help.

Last time I had weird things (like you) happen, it was a combination of cheap disk and too high of a burn speed.

---

### Post by stuartbh on 2013-05-05
Well, I tried the "apt-get update && apt-get dist-upgrade" and it did little to help. I also did not use a CD, I just did a dd to a USB stick. I also checked the md5sum of the CD prior to using it.

I am also going to take a look at Debian maybe too. I was for quite a long time a RedHat type, but I switched to Ubuntu when I had problems with Fedora, then switched to CentOS. The CentOS forums were rather derisive to deal with so I moved to Ubuntu and have never really been dissatisfied with Ubuntu. The only thing about Ubuntu (over the long term) that I do not like is the fact they use Unity and not GNOME. But, so long as GNOME is still able to be installed after the fact I find Ubuntu usable.


Stuart

---

### Post by ibjsb4 on 2013-05-05
The classic desktop can still be found in all current releases.  If you run 12o4, you will have classic support till 2017 (its an LTS and supported till then).

---

### Post by stuartbh on 2013-05-23
In the end I simply reinstalled the OS and the issue evaporated.

---

