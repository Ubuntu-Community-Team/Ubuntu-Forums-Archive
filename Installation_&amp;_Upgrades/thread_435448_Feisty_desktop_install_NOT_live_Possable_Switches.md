---
title: "Feisty desktop install NOT live? Possable? Switches?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by kaze on 2007-05-06
[SIZE="2"]Is a Feisty desktop install NOT going through the live CD Possable? Are there some switches for the boot: prompt to do this? Just want to be able to take an old box with low ram, slow optical, etc., and do an install, instead of waiting for like an hour on the optical spinning up and seeking...[/SIZE]

---

### Post by haargerman on 2007-05-06
Alternate CD with Text installer perhaps?

---

### Post by aysiu on 2007-05-06
I don't think it's possible right now, but [it could happen in the next Ubuntu release](http://ubuntuforums.org/showthread.php?t=409925).

---

### Post by kaze on 2007-05-06
> **haargerman said:**
> Alternate CD with Text installer perhaps?
Gonna download and try the alternate tomorrow.

---

### Post by aysiu on 2007-05-06
If you really have "an old box with low ram, slow optical, etc," I'd use this guide:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by kaze on 2007-05-06
RE: "I don't think it's possible right now, but it could happen in the next Ubuntu release."

Just read the linked thread. Exactly. The thread seemed to get stuck on the technical, sort of missed the idea. And what about linking to the alternate installer - still difficult to find. I have to almost start a download, then past the earl in and back off by one directory, basically browsing the mirror to actually find the alt iso.

The floppy based install howto <https://help.ubuntu.com/community/Installation/WithFloppies> is, IMHO, lame...

---

### Post by kaze on 2007-05-06
> **aysiu said:**
> If you really have "an old box with low ram, slow optical, etc," I'd use this guide:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Awesome link - thanks. Used to use a Lord Such (**sp!**) mini-iso like that for Debian. This one looks like the Debain installer - just points at Ubuntu instead? If the whole thing in only 10MB - why not use this as the added menu option?! And since at that point the user already has 700MB on CD - just point that "Minimal CD" code to the CD as primary, then the web as secondary... *Not perfect, but would definately reduce fustration.*

Now is the <[http://www.psychocats.net/ubuntu/minimal#barebones]("http://www.psychocats.net/ubuntu/minimal#barebones")> and <[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")> caveat free and up to speed for 7.x?

---

### Post by aysiu on 2007-05-06
What caveat?

---

### Post by kaze on 2007-05-07
> **aysiu said:**
> What caveat?

I mean, are there any [caveat]("http://www.google.com/search?hl=en&safe=off&rls=GGLC%2CGGLC%3A1969-53%2CGGLC%3Aen&q=define%3Acaveat") or known missing pieces of the psychocat's barebones Ubuntu install?

Got the mini-iso and am going through the install right now. Last night the installer from inside the live feisty first failed to format my swap and then my root; then after I did it manually via TRBFloppy it was unable to mount 'em.

I actually like this pseudo-text Debian installer better.

---

### Post by aysiu on 2007-05-07
No caveats. If you feel the barebones is *too* bare, just ask the forum members what package you need in order to do _____, and someone will probably give you a good suggestion.

---

### Post by kaze on 2007-05-08
Thanks ubuntuforums.org and aysiu!
Learned some stuff and got the machine up!

So now I'm runing icewm - I like it, but have some initial questions:
*  Is there a GUI file manager?
*  How do I view the CDROM? - all the directories named CDROM are empty and mount doesn't list it
*  How do I open up SSH into the box?

I will figure the above out - just glad I got the install done :-)

---

### Post by aysiu on 2007-05-08
You can install a GUI file manager. Even though Rox-Filer is pretty light, I'd recommend installing Thunar and its volume manager--that takes care of two things at once: CD-ROM mounting and a GUI file manager.

I don't know much about SSH, but I believe you'd want to install OpenSSH.

```
sudo apt-get update && sudo apt-get install thunar thunar-volman-plugin openssh-server
```

---

### Post by kaze on 2007-05-08
D'oh, was about to install Thunar, wanted to paste from Firefox into the terminal window, doesn't seem to be a paste option, then X crashed...

Gives an opportunity to post the one error I get, "...error loading the theme Human" "...Human.xml"

---

### Post by kaze on 2007-05-09
Hey, another thing, from the <psychocats.net/ubuntu/minimal> I didn't uncomment the ubuntu feisty universe lines from /etc/apt/sources.list - everything else seems to have worked.

---

### Post by kaze on 2007-05-09
> **aysiu said:**
> <snip>```
sudo apt-get update && sudo apt-get install thunar thunar-volman-plugin openssh-server
```

Okay - installed. Now _where_ does it show up?

Thanks for all the continued help too!

---

### Post by aysiu on 2007-05-09
Well, I don't know much about how to use OpenSSH Server--I just know that's the software you'd need.

But Thunar should show up in your menus if you've installed *menu* and *menu-xdg*. If you haven't installed those packages, maybe you should.

I'd also recommend copying over a few IceWM configuration files from either /usr/share/icewm or /etc/X11/icewm. The ones you need are

preferences
keys
toolbar

They should be copied to ~/.icewm or /home/kaze/.icewm

In preferences, you can specify whether to show programs in the menu or not. 1 means "yes," and 0 means "no."

A little trick--if you press the Windows key and space bar together, you get a kind of *Run* dialogue in the toolbar. You can then type ```
thunar
``` to launch Thunar. You can also manually edit the ~/.icewm/toolbar file to make a launcher for Thunar.

IceWM also has some GUI tools for configuration. I've found them to be a bit more confusing than the text files, but you may want to give them a try: *iceme* and *iceconf*.

Read more [here](http://ubuntuforums.org/showthread.php?t=263710).

---

### Post by kaze on 2007-05-09
Awesome!

SSH is working. Client was there, just has to install the server piece.

*menu *was installed but I had to add *menu-xdg*.

I'll try to configure IceWM tonight. Then I suppose there's a way to autocreate or copy these files for new users? Obviously the IceWM GUI is not a "heavy" as the standard install's, I didn't find the GUI referenced here <[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add.2Fedit.2Fdelete_system_users]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add.2Fedit.2Fdelete_system_users")> so used *mkdir adduser usermod chown* and *chgrp*, which was a bit tedious.

Now does IceWM have one of those shiny autoupdate buttons like the "heavier" desktops?

Overall quite happy. Next will be SAMBA and CUPS and a lightweight word processor!

---

### Post by aysiu on 2007-05-09
Well, the add user GUI I think is in *gnome-system-tools* or *gnome-utils*. 

For updates, you need *update-manager* and *update-notifier*.

Just keep in mind that the more you keep adding those types of things... the heavier IceWM will be.

---

### Post by kaze on 2007-05-09
> **aysiu said:**
> Well, the add user GUI I think is in *gnome-system-tools* or *gnome-utils*. 

For updates, you need *update-manager* and *update-notifier*.

I guess I'm just figuring out the difference btwn OS / desktop / windows manager / theme

So something like *update-manager* and/or *update-notifier* is a Linux program that is tightly integrated with the Ubuntu distro and 'net based source repositories. It would run nicely on Ubuntu regardless of the "desktop." So what windows manager do Gnome or KDE use? Or are they the windows manager? Is the fact that I'm running IceWM the reason why I can't copy from FireFox and paste into XTERM?

> **aysiu said:**
> Just keep in mind that the more you keep adding those types of things... the heavier IceWM will be.

Understood. Yeah, I'll prob just use the CLI for user creation - but want the autoupdate. That's another thing - [FONT="Courier New"]apt-get update[/FONT] does not update existing stuff - just what [FONT="Courier New"]apt [/FONT]knows about; this understanding makes a difference! That said, there must be away then within aptitude or those other package managers to update all the installed packages whose builds have incremented - I'll have to read up on that.

---

### Post by aysiu on 2007-05-09
I think *update-manager* and *update-notifier* could probably run fine in any environment that has a system tray or notification area (and IceWM does have a system tray).

Gnome's default window manager is Metacity. KDE's default window manager is Kwin.

You can paste into xterm... just not in the traditional way (right-click). There's probably a keyboard shortcut for it (Does Shift-Insert work? I can't remember), but I know middle-click (or left and right mouse buttons clicked simultaneously) will paste into xterm. It has nothing to do with IceWM--it's xterm. If you want a different terminal, you can try something heavier like eTerm, Gnome Terminal, or Konsole.

And you can update installed programs with ```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

