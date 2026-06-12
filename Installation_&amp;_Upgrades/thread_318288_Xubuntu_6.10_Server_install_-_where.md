---
title: "Xubuntu 6.10 Server install - where?"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by FakeOutdoorsman on 2006-12-13
I want to install Xubuntu with IceWM on a Panasonic CF-71 Toughbook Pentium II with 128 mb ram.  I have the Xubuntu 6.10 Edgy alternate disk and tried to follow the [directions]("https://help.ubuntu.com/community/InstallingXubuntu") on the Ubuntu Wiki. It says, "at the Ubuntu boot screen, type: *server*".  The wiki also has a link to a screenshot, but it is unavailable.

I was planning on using the server option to install a very basic system and then add what I want later.  There is no place for me to type *server*.  Has it been removed from 6.10?  Here are my options:  Install in text mode, Install in OEM mode, Install a command-line system, Install an LTSP server.  Maybe command line is equivalent to the old server install.

---

### Post by NT4usB on 2006-12-13
Read the fine print when you run the CD. There's a Func key that will display more options... F4 or F6 or something. Start with F1 (help).
A command line like box shows up but it's not clear if you tack on 'server' to the end or overwrite the entire line with just 'server'. I did find removing some of the switches allowed me to see the install process instead of just a graphic. Alt+F2 (or F3 or F4) toggles between a command line and the install progress...
I went around and around with Xubuntu one night, trying to put it on a PIII 550 with 768 MB of PC100.
When I finally got it installed, I wasn't real impressed with the (lack of) speed...
Might have even been pokier than when I had NT4 on it. Hard to say as it had been a while since I ran it that way.

---

### Post by confused57 on 2006-12-13
> **FakeOutdoorsman said:**
> I want to install Xubuntu with IceWM on a Panasonic CF-71 Toughbook Pentium II with 128 mb ram.  I have the Xubuntu 6.10 Edgy alternate disk and tried to follow the [directions]("https://help.ubuntu.com/community/InstallingXubuntu") on the Ubuntu Wiki. It says, "at the Ubuntu boot screen, type: *server*".  The wiki also has a link to a screenshot, but it is unavailable.

I was planning on using the server option to install a very basic system and then add what I want later.  There is no place for me to type *server*.  Has it been removed from 6.10?  Here are my options:  Install in text mode, Install in OEM mode, Install a command-line system, Install an LTSP server.  Maybe command line is equivalent to the old server install.
You might want to look into Ubuntu Lite:
[http://www.ubuntuforums.org/showthread.php?t=98233&highlight=Ubuntu+Lite](http://www.ubuntuforums.org/showthread.php?t=98233&highlight=Ubuntu+Lite)

Install a command line system is the same as the install a server on previous alternate Ubuntu versions.

---

### Post by FakeOutdoorsman on 2006-12-14
I got everything working using Install a command-line system and adding IceWM.  More responsive than Xfce but not as good looking.  I'll try out the [icebuntu]("http://freshmeat.net/projects/icebuntu") theme and see if it slows it down too much.  Helpful pages:
[URL="https://help.ubuntu.com/community/Installation/LowMemorySystems"]
Installation / Low Memory Systems[/URL]
[IceWM]("https://help.ubuntu.com/community/IceWM") - Ubuntu Wiki
[My IceWM Setup]("http://xubuntu.wordpress.com/2006/07/20/my-icewm-setup") - Xubuntu Blog
[HOWTO: Setup Icewm with Rox-Filer]("http://www.ubuntuforums.org/showthread.php?t=171203")

---

### Post by K.Mandla on 2006-12-14
You're right: That wiki page is a bit outdated. For anyone else who runs into this problem, a server install is called a *command-line system* on the Edgy alternate CD. :-?

Edit: I've tried to update it a little, with links at the top that point to the Xubuntu download pages and a mention of command-line systems in the body, but it's still a bit sketchy.

---

