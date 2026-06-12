---
title: "kubuntu 7.10 toshiba blackscreen after booting !!!"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by StevenRoose3 on 2008-02-15
hi,

after installing kubuntu 7.10 with LiveCD, everything went fine, when rebooting i get blank screen. I am searching fr this bug fr a rather long time, but never found a working fix.
i can just boot recovery mode and type kdm, but that's stupid, isn't it?
(the boot screen is nice)
i rally think it has to be fixed before, i saw many threads about it, but i couldn't found i fixed one.

regards,
Steven

---

### Post by Rocket2DMn on 2008-02-15
This happens fairly often, it just doesn't like your video card (yet).  You can reconfigure X following this little guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you have questions/problems post back with your video card make/model

---

### Post by StevenRoose3 on 2008-02-16
i just saw that when i boot (normally, when i have blackscreen) nd i wait very long, the kde login windows really opens, but with a veryy long wait, is it the same problem then?

---

### Post by StevenRoose3 on 2008-02-16
when i boot normally, it takes 2 minutes longer than recovery mode (+ kdm command) (: 2min43secs)...

plz help.

Steven

---

### Post by Rocket2DMn on 2008-02-16
Is that just from start to finish, or does it hang?  If it's just start to finish, you can follow this lovely guide to help speed up your boot process.  It basically just memorizes where stuff is in your hard drive so the next it boots it know exactly where to look instead of search around for every little thing.  It's a really cool feature - [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by StevenRoose3 on 2008-02-16
done, both aspects, nothing helped.

i'll mention that i just don't see any loading screen, just 3 minutes black screen before the login comes up.

i can't find any other topic with this bugs.

Steven

---

### Post by Rocket2DMn on 2008-02-16
It might just take that long to boot your computer, but the problem is your not getting the splash screen.  If you want to see what's happening you can remove the "quiet" and "splash" arguments from your menu.lst file for grub (always make a backup first) for the kernel you are booting from:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
Then you can reboot and should see a bunch of white text scroll down your screen as different parts of the OS are loaded.  You can see where it hangs up or just takes awhile to load.

If you search the forums for something like "no splash at boot", you will get tons of hits.  Some will show you what I just said (how to NOT have a splash) and some will have the same problem you have.  Sometimes it has to do with the splash being at the wrong resolution I think - it's not an uncommon problem.

---

### Post by StevenRoose3 on 2008-02-17
it's going faster now, i think by the profile...

but do i hide the boot codes by retyping the --quit and/or the --splash is menu.lst?

and, i still don't see the loader screen

---

