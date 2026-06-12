---
title: "Strange Upgrade Problem"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Josh The Stampede on 2008-05-01
Yesterday I upgraded from Gutsy to Hardy using the uprgrade manager. I backed up my xorg.conf file beforehand, and lo and behold, after upgrade my monitor was a mess, so I used my old xorg and everything seems ok. Except there's one issue.

After a reboot or power-up, if I log directly into gnome, I get a hard-freeze with no mouse, either before the desktop appears or less than a minute after. However, if I log into gnome failsafe, everything works perfectly.Then, from there, I can log out, and back into gnome regular, and it still works just fine. Sound, video, network, everything works. It's only the first login after a shutdown/reboot that needs to be failsafe or the machine locks up immediately after login.

I know it's a strange and esoteric problem, but does anyone have a clue what this might be? I've already tried replacing/renaming/deleting my .gnome, .gnome2/sessions, and .gconf files. This fixes the problem for one login, but then again after a reboot it hangs. My sound and video both work fine after the workaround, so I dont think it could be those drivers, which are usually the culprit.

---

### Post by Thingymebob on 2008-05-01
Can't help but I'm also having problems with the first login although slightly different. On first login the X session immediately restarts and bumps me back to the login screen after that all following logins work perfectly. Not a massive problem for me just a little annoying. 

By the way my Hardy install is also Dist upgrade from Gutsy where everything worked a treat

I've attached my xsession.errors file for anyone that may be able to help.

---

### Post by Thingymebob on 2008-05-09
This solved my problem, not sure if it will help you or not


I think the issue may be with xserver-xgl,
Looking through my own logs I decided to remove xserver xgl, and the problem has gone away. Had to remove Option AIGLX OFF from xorg.conf to keep Compiz working.

I think installing XGL and adding the AIGLX option to xorg.conf was a common workaround to get compiz working with ATI cards back in fiesty.

---

