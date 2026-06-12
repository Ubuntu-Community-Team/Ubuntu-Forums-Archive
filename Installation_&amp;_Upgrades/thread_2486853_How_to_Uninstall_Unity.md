---
title: "How to Uninstall Unity"
date: 2023-05-14
forum: Installation &amp; Upgrades
---

### Post by cforput on 2023-05-14
I wanted to install Unity the app development package but instead installed the Unity environment on my 22.10 Ubuntu. Not my touchpad gets input from the palms of my hands when I type. This is horrible behavior. I've tried going as far as completely deactivating the touchpad in Settings, Tweaks and looking around in dconf editor for settings. None of them have ANY affect on the touchpad. Even if I turn them it completely it it still works. What program is used with Unity that actually changes the touchpad? Or better yet, how do I get rid of Unity now that I've installed it accidentally? There are other things that don't work either. IMO it's horrible and I don't want it. I've tried searching on how to uninstall it but all that comes up is results from back when ver 17 was around. Even just typing this question, conciously trying to hold my hands up off the touchpad it still accepted input several times. Thank you

---

### Post by TheFu on 2023-05-14
The easy answer is to require from the backup you made before installing 25+ packages.  You do have backups, right?

Otherwise, use the same package name you installed in the remove command.  Then remove any orphaned dependencies.  If you did a 
```
sudo apt install unity

```Then make a know-you-can-restore backup first, then do a 
```
sudo apt remove --purge unity
sudo apt autoremove
```

Backups are necessary, since we could do bad things, unintentionally.

What DE were you running before?  That DE might have a different login manager.  That might need to be reinstalled.

And lastly, create a new userid with a new directory and profile.  Login using that.
If you know what you are doing, already have a backup from last night, and run the commands, this should take around 3 minutes to complete, not counting the time required for reboots.  You'll probably need to reboot twice at different stages.

---

