---
title: "Kubuntu-Desktop Install Moved My Ubuntu Install?!"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by tracyandskye on 2010-03-07
I installed Kubuntu-Desktop on Ubuntu & now my Ubuntu installation is on the 2nd (data)partition!  It's hard to believe but I'm looking at it from a live cd and that's what looks like happened.

For right now, my main goal is to get Ubuntu back.  Should I make the 2nd partition bootable so I have a dual-boot option at startup?  Should I make the 2nd partition bootable & not the first?  Can I uninstall Kubuntu somehow & have things return to how they were?  What a nightmare!  I thought I was just loading an alternative sassion to Gnome.  I thought that the only thing I said yes to was to use the KDE boot manager (or whatever).  Big mistake...

---

### Post by tracyandskye on 2010-03-07
Looking closer, all of the system files like the /etc folder & things are still on the first partition.  It seems like it just moved my user files over to the other partition, so obviously it's not a dual-boot situation.  

There is nothing in the home folder on the first partition (which is at least one reason I couldn't login).  So I'm going to copy my user file from the 2nd partition to the first & try logging in again.

---

### Post by tom4everitt on 2010-03-07
Exactly how did you install kubuntu-desktop? Did you install it from a (bootable) cd or did you install it from within your running ubuntu?

---

### Post by tom4everitt on 2010-03-07
Usually if you log out from kde (not shutting down the computer, just signing out) you will have an option at the bottom of the screen which desktop environment to use. 

There you should be able to choose between gnome and kde.

---

### Post by tom4everitt on 2010-03-07
> **tracyandskye said:**
> Looking closer, all of the system files like the /etc folder & things are still on the first partition.  It seems like it just moved my user files over to the other partition, so obviously it's not a dual-boot situation.  

There is nothing in the home folder on the first partition (which is at least one reason I couldn't login).  So I'm going to copy my user file from the 2nd partition to the first & try logging in again.


Its a quite common setup to have the user data on a separate partition. It sounds quite unlikely that installing kde would have changed that.

---

### Post by tracyandskye on 2010-03-07
That's true.  I probably set the 2nd partition to mount at /home.  It probably doesn't show that in Nautilus so I thought they were all on the 1st partition.  So now I just need to know how to get Kubuntu to see it.  I can't login because the user is not recognized (I think) from the Kubuntu login menu.

---

### Post by tom4everitt on 2010-03-07
But the mount of /home is set in the file /etc/fstab which is unaffected of whether you login with gnome or kde. Are you sure there's no option to log in with gnome in the bottom the login window?

---

### Post by tracyandskye on 2010-03-07
There is an option under a button in the kde login window, but it's still the same.  Somehow the user account got disappeared I guess.

OK now I feel like even more of an idiot than usual when messing with Linux.  I didn't have the case right on one of the letters in the username!  I thought I tried all the possibilities earlier but apparently not.

It works fine.

---

### Post by tom4everitt on 2010-03-08
Ok, great! :)

---

