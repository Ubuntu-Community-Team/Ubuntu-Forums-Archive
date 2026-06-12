---
title: "Upgrade Bug: Upgrade from 10.04 LTS to 12.04 LTS did not end gracefully"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by Krallus on 2013-04-21
Hello.  I used the software update manager in 10.04 LTS to upgrade to 12.04 LTS.  It seemed to be going fine until it got to the clean-up phase.  Either just before or just after the clean-up phase (I couldn't tell if it reached completion), the upgrade status window disappeared and was replaced by an unreadable prompt.  The prompt had a red X graphic in it on the upper left, and a button on the lower right.  All the text and labels were unreadable: just square blocks.  I took a chance and clicked the button which caused the prompt to disappear but nothing else happened.  The shutdown menu was in the "reboot required" state so I rebooted.  Everything seems okay at the moment, but I've only just started to check things out.  I'm a little concern about the way the upgrade ended as it appeared to abort during clean-up so I don't know if it reached a point where it should have started auto-configuring.  Any suggestions?  In any case, this is a bug that should be fixed.

As an aside, I'm not sure I like the new interface but I'm willing to give it a try - my immediate first impression is: great, look at all those icons, but what happened to the convenient menu to pull down my list of favourite places, the menu for all the programs, and what!?: no bar at the bottom to manage a list of open windows?!

---

### Post by ibjsb4 on 2013-04-21
You can try an update, see if it kicks anything back at ya.

As for the new desktop, thats Unity.  You can install gnome-classic, thats like your old 10.04 desktop.

```
sudo apt-get install gnome-session-fallback
```

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by kostkon on 2013-04-21
Clean-up just removes uneeded packages, empties the cache, etc.

You can do it yourself, it's 100% safe and it will free up space:
```
sudo apt-get autoremove
```
then
```
sudo apt-get clean
```

---

