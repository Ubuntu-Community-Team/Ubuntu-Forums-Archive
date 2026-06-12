---
title: "[SOLVED] upgrade to intrepid beta, black screen"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rektaali on 2008-10-02
i just upgraded from 8.04 to 8.10 beta.
during package installation i got multiple errors saying that it couldnt install some files.
i cannot remember what files since for some stupid reason i wasnt really paying attention, just clicking "close"

now after the installation was complete, or so i think because the installation window was closed and the "reboot" button was on the menu bar, i clicked the reboot button and rebooted my computer.
it loaded GRUB just fine, but after that it just gives me a black screen, and nothing happens.
when i press any key on my keyboard the Num Lock light flashes for some unknown reason.

id rather not re-install kubuntu, because i have multiple files/videos in there that id like to keep.

ive searched for a solution for this but i just couldnt find anything like it. mostly probably because no one is as stupid as to try something like this when they dont know what theyre doing.

---

### Post by Rocket2DMn on 2008-10-02
Moved to Intrepid Ibex Testing and Discussion - remember that Intrepid is still a development release and is subject to more-than-normal breakage.

If it is booting, then going blank when about the time it's supposed to be loading the graphical login, you might need to reconfigure X.  Reboot into the recovery mode kernel and run
```
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Let the computer reboot normally.  You will need to re-install restricted drivers if you use them (though I'm not sure they all work in Intrepid yet...).  That is likely the initial problem - failure to remove restricted drivers before rebooting into a new kernel can mess up X.  If you don't know what I'm talking about, then you probably shouldn't be using development releases of (K)ubuntu.

---

### Post by agurk on 2008-10-02
If that doesn't work, you can boot a live CD and copy the files to a USB device.
Impressive start btw, welcome to the forums!

---

### Post by jerrylamos on 2008-10-02
> **agurk said:**
> If that doesn't work, you can boot a live CD and copy the files to a USB device.
Impressive start btw, welcome to the forums!

Today's build live CD (nearly Beta?) = black screen on this IBM Thinkpad R31 32 bit Celeron 1 gHz.

Amazingly, install worked - it's dual boot and I'm on the early Alpha 5 which works so the computer is O.K.  The CD boots on my Compaq Presario so the CD is O.K.

Closest I can get to running is to Ctrl-Alt-F1 when the brown screen & pointer appear.  That lets me stare at a command line prompt while I can hear the hard drive as Gnome Ubuntu starts up.  

When all is quiet, Ctrl-Alt-F7 to the Gnome desktop.  It appears for about 1 second, background, top & bottom lines, applets, the whole bit.  Then Wham, blackground screen and nothing works..

Xubuntu & Kubuntu Intrepid Alpha's work.  It's just Ubuntu Gnome that doesn't.  The launchpad bug @ is 277344

Jerry

---

### Post by rektaali on 2008-10-03
I´ve been asking a friend of mine to help me, and he says that it doesnt even get to loading X, which is what i was kind of suspecting. 

when i boot to recovery mode it gives me 
´VFS: Cannot open root device "UUID-59f8bd62-da2d-49ba-b38f-e1dbbf0fdce0" or unknown-block(0,0)`
`Please append a correct "root=" boot option; here are the available partitions:`
`Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)´

So the infamous Kernel panic got me.

---

### Post by Rocket2DMn on 2008-10-03
Yeah, that could be a problem.  Have you tried booting into an earlier kernel in the GRUB list?  You may want to try re-installing GRUB if that doesn't work either, I would suggest using the Super Grub Disk - I think the website is supergrubdisk.com but I can't check right now since the site is blocked here at work.  If all else fails, you will need to boot into a LiveCD, backup your files onto another hard drive, then reinstall the system.

---

### Post by xebian on 2008-10-03
Before you do anything more, I strongly suggest you boot with a live CD - puppylinux, etc, and save your files off your HD to a safe place.

---

### Post by jdong on 2008-10-03
I would recommend grabbing an Intrepid Beta Desktop CD (LiveCD) and trying that on your system to see if it boots normally. If it does, then it's an upgrade error. Otherwise, there's a bug in Intrepid that makes your system unuseable (that we'd like to know about!)

In fact I ALWAYS recommend people to do this before upgrading to a new distribution anyway, as it gives you more assurance the new version will work before you commit to it.

In any case, use any Linux LiveCD to pull your data off the hard drive before screwing around more -- the upgrade doesn't damage any of your data, even if the operating system itself is in ruins.

---

### Post by rektaali on 2008-10-05
ok i got my friend to help me, and what we did was went to the oldest kernel recovery there was in the kernel list, went to root, and typed apt-get update && apt-get dist-upgrade.

of course the original problem mightve been that my ethernet card was disabled for some reason, and we had to get that working again.
i cannot remember what we did exactly to get it to work, but it wasnt too hard considering the fact that i was getting really angry and almost gave up on the whole thing.

but thanks for all your help. 
i really appreciate it.

---

### Post by jdong on 2008-10-05
Sounds like for some reason your original upgrade was incomplete. Can you look for dist-upgrader logs in /var/log if you have some spare time? Those can help the developers figure out why that happened.

---

