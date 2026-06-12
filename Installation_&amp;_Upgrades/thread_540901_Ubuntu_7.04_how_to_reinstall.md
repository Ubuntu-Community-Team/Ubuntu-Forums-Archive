---
title: "Ubuntu 7.04 how to reinstall ?"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by suj2007 on 2007-09-02
Friends,  ubuntu 7.04 is installed in my system along with Win XP as duel booting system. Recently  ubuntu os is creating problem frequently, such as sometimes the terminal not open and if open it hangs up other applications behave like this. Than I have not alternative to shut  down the  system. Some times I cannot shut down also and then I have to direct power off.

Therefore I wish to reinstall  ubuntu 7.04 without uninstall/unformating the existing installation. Is there any way to do the same. If I format the existing ubuntu installation I will lose all the updated done via net as well as other configuration.

Please any alternative.
thanks

---

### Post by forestpixie on 2007-09-02
I know that you can use apton cd to save and reuse applications that you've downloaded but I'm not sure about updates - I suspect you'd need to get them again

Saying that a search found [this]("http://ubuntuforums.org/showthread.php?t=377202") thread - in which I found this

> **Motoxrdude said:**
> I think if you do a manual partition editing you can reuse your current "/" partition and mount that as "/" in your new install without formatting it. Not sure how it will work, but i think it will.

But I couldn't be really sure if it'll work or not - if it doesn't using aptoncd would at least keep the application downloads you'd done

---

### Post by logos34 on 2007-09-02
there's also gnome-reset to backup your desktop settings/preferences

$ apt-cache show gnome-reset
Package: gnome-reset
Priority: optional
Section: universe/gnome
Installed-Size: 200
Maintainer: Daniel Holbach <daniel.holbach@ubuntu.com>
Architecture: all
Version: 0.1.2+cvs2006.02.03-0ubuntu2
Depends: python (>= 2.5), python (<< 2.6)
Filename: pool/universe/g/gnome-reset/gnome-reset_0.1.2+cvs2006.02.03-0ubuntu2_all.deb
Size: 13652
MD5sum: 10a111f35411b2f1b4a741e7c99763eb
SHA1: bd2003562e03a9bd81b3e29907b2a5a332250f67
SHA256: a8c09e29194854c01c07981989a452fa924c82573cfc3ca643eacbc25e67320f
Description: backup and reset tool for GNOME
 gnome-reset creates a backup of a bunch of settings and then resets
 them.  A domain is a particular set of settings.  Some current
 examples are nautilus and gnome-panel.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by suj2007 on 2007-09-02
I tried to reinstall ubuntu. During reinstalling some where it ask for names and password for the existing user in windows as well as ubuntu and prompts me for 6 users from Win Xp and ubuntu 7.04. I cannot decide what to do and cancelled the installation. 

I shall be glad to know what shall I have to do for this step?
thanks

---

### Post by merlinus on 2007-09-02
Choose: Do Not Import Anything, other than maybe your previous ubuntu username.

If you do not import that either, then you will be prompted for a new username and password later on in the install process.

-merlin

---

### Post by suj2007 on 2007-09-02
Thanks for your reply.

---

