---
title: "Problems after Install of 14.04 flashback"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by merlinus on 2014-09-05
Did a fresh install of 14.04 64-bit, and using gnome compiz flashback.   I have no min-max-close buttons on any windows, and cannot change the window focus when clicking on another one -- the current window remains active no matter what.

Also, I do not have any of the usual right-hand applets in the top panel.  All I have is date and time.

Assistance greatly appreciated!

---

### Post by egeezer on 2014-09-05
With compiz, sometimes you need to install dconf-tools (if it isn't there already) and run dconf-editor.  Navigate to org > gnome > desktop > wm > preferences.  There you need the Greybird theme, not the default Adwaita.

Worked for me once when I was stuck, hope it works for you!

---

### Post by merlinus on 2014-09-05
Thanks for the tip, but it seems the problems are much more extensive.  For example, clicking on menus in Firefox and Thunderbird does nothing, nor does right-click work in Tbird.

I reinstalled, but although I can see the usual panel icons at the login screen, when I log in it takes me to a screen which has only the default wallpaper -- no panels, menus, not even the unity taskbar -- and if I use keyboard shortcuts to run Nautilus or Terminal, still no close, max or min buttons, and same mouse issues.

There may be some setting in /home that is screwing things up, so having backed up all the /home files, will tell the installer to format that partition as well as /root, and see if that helps.

I of course tested the install disc for errors, even though I used it yesterday for a perfect install on my laptop.

FWIW, 12.04 has worked perfectly on this machine for over two years now, but I knew that sooner or later I would need to install a newer LTS version.

---

### Post by kansasnoob on 2014-09-05
Just as a matter of troubleshooting try booting into a Flashback w/Metacity session and see what things look like, then report back :)

---

### Post by merlinus on 2014-09-05
Flashback is gone with the reinstall, but when I do a guest login, things look as they should (e.g. unity launcher, right-hand top panel icons).

So it would appear that something in /home is creating problems.

---

### Post by kansasnoob on 2014-09-05
> **merlinus said:**
> Flashback is gone with the reinstall, but when I do a guest login, things look as they should (e.g. unity launcher, right-hand top panel icons).

So it would appear that something in /home is creating problems.

So you reinstalled using the same /home partition? Just curious.

I have also encountered a lot of issues with the *hidden dot* configuration files in /home, both with upgrades from Precise -> Trusty, and with reinstallations.

That's number one in my *Challenges and Known Issues* [here]("http://ubuntuforums.org/showthread.php?t=2220264") :(

---

### Post by merlinus on 2014-09-06
Yes, I used the same /home partition, and chose to not format it during installl.  Looks like a fresh install is in order, this time formatting the existing /home.  I can then use my backups to restore Firefox, Opera, and Thunderbird prefs and such, as it would seem highly unlikely that they are the culprits.

---

### Post by kansasnoob on 2014-09-06
> **merlinus said:**
> Yes, I used the same /home partition, and chose to not format it during installl.  Looks like a fresh install is in order, this time formatting the existing /home.  I can then use my backups to restore Firefox, Opera, and Thunderbird prefs and such, as it would seem highly unlikely that they are the culprits.

I've had some luck just renaming certain hidden dots, which causes new ones to be created when you reboot. I start by running "ls -a":

```
lance@lance-desktop:~$ ls -a
.                    .config           .gnome2_private  Music
..                   .dbus             .gphoto          Pictures
.adobe               deja-dup          .gstreamer-0.10  .profile
.apport-ignore.xml   Desktop           .hardinfo        Public
Backups              .dmrc             .hplip           Templates
.bash_history        Documents         .ICEauthority    .thunderbird
.bash_logout         Downloads         .local           Videos
.bashrc              examples.desktop  .macromedia      .Xauthority
brasero-session.log  .gconf            .mozilla         .xsession-errors
.cache               .gksu.lock        .mozilla_BK      .xsession-errors.old
.compiz              .gnome2           .mozilla_OLD

```

Here's an example where I helped someone:

[http://ubuntuforums.org/showthread.php?t=2239208&page=4&p=13106215#post13106215](http://ubuntuforums.org/showthread.php?t=2239208&page=4&p=13106215#post13106215)

You'll have to scroll ahead through several posts, and ignore the stuff about that /etc/fstab - that was a different issue - no idea how that happened.

I'd try to be of more help but I already have too may irons in the fire.

---

### Post by merlinus on 2014-09-06
I think it would be easier to reinstall and format /home, and then copy back the dot files for firefox, opera, thunderbird, bluefish, virtualbox, thunar, and such from my backup on a usb drive, even before installing flashback and other apps.

Thanks for your assistance and insights!

---

### Post by merlinus on 2014-09-06
Update:  I re-installed and formatted /home, then copied back all of the dot files.  Works perfectly!  All my bookmarks, email accounts, email, and virtualbox machine.

Thanks for the assistance!

---

