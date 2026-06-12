---
title: "No new login screen"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ernstblaauw on 2010-03-06
Hi,

I'm running Lucid alpha on my desktop (64-bit) and laptop (32-bit). My desktop has the new login screen theme (the purple one). However, the login screen of my laptop still shows the old brown one. How do I enable the new login screen on my laptop? 

Bye bye,
Ernst

---

### Post by Atermoon on 2010-03-06
> **ernstblaauw said:**
> Hi,

I'm running Lucid alpha on my desktop (64-bit) and laptop (32-bit). My desktop has the new login screen theme (the purple one). However, the login screen of my laptop still shows the old brown one. How do I enable the new login screen on my laptop? 

Bye bye,
Ernst

You can try reinstalling gdm or ubuntu-artwork or... I'm not even sure which package is responsible for that.

Or you can use gdm2setup [https://launchpad.net/gdm2setup/](https://launchpad.net/gdm2setup/) to tweak your gdm. It has a bunch of options which the normal config doesn't, like changing the background, disabling the annoying sound or changing the gtk and icon theme.

---

### Post by Mr. Picklesworth on 2010-03-06
I have this same issue on my netbook, upgraded from Karmic (desktop version) using the upgrade tool. My suspicion is that I probably tinkered with GDM's settings at some point, so they are overriding the new defaults. Trouble is, I don't know the appropriate gconf-fu to revert that.

---

### Post by stevevai on 2010-03-06
I'm also stuck with the old login screen, no idea how to update it

---

### Post by petejk on 2010-03-06
I'm in the same boat here,

The login screen hasn't changed for me, although the new desktop themes are available.

Should the default boot splash logo have changed also?

Thanks,
Pete

---

### Post by ernstblaauw on 2010-03-06
> **Atermoon said:**
> You can try reinstalling gdm or ubuntu-artwork or... I'm not even sure which package is responsible for that.

Or you can use gdm2setup [https://launchpad.net/gdm2setup/](https://launchpad.net/gdm2setup/) to tweak your gdm. It has a bunch of options which the normal config doesn't, like changing the background, disabling the annoying sound or changing the gtk and icon theme.

gdm2setup does the trick. Thanks!

---

### Post by petejk on 2010-03-07
Both problems solved now:
gdm;
apt-get purge gdm and linked packages, then reinstall.

Got the correct purple Plymouth splash using 
sudo plymouth-set-default-theme ubuntu-logo --rebuild-initrd
and instructions from
[http://ubuntuforums.org/showpost.php?p=8919056&postcount=92](http://ubuntuforums.org/showpost.php?p=8919056&postcount=92)

Only thing is now I installed GDM2setup and changed the theme, and I cant remember which are the new Lucid defaults.
At the moment my GTK theme is Ambiance
and Icon Theme is LoginIcons.
Is anyone able to install GDM2Setup to check that those are the defaults?

Thanks,
Pete

---

### Post by MadMan2k on 2010-03-07
the settings were not updated correctly, just do:
rm -rf /var/lib/gdm

here is the bug: [https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/532659](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/532659)

---

### Post by robert shearer on 2010-03-07
> **ernstblaauw said:**
> Hi,... My desktop has the new login screen theme (the purple one). However, the login screen of my laptop still shows the old brown one. How do I enable the new login screen on my laptop?

Lucky you I say :D. I want the 'old brown one' with the black and white login box.

Wanna swap...? ;)


Seriously, anyone know how to get back to that set-up ?

---

### Post by uRock on 2010-03-07
> **robert shearer said:**
> Lucky you I say :D. I want the 'old brown one' with the black and white login box.

Wanna swap...? ;)


Seriously, anyone know how to get back to that set-up ?

Reinstall Karmic

---

### Post by Atermoon on 2010-03-07
> **robert shearer said:**
> Lucky you I say :D. I want the 'old brown one' with the black and white login box.

Wanna swap...? ;)


Seriously, anyone know how to get back to that set-up ?

Install gdm2setup and change the theme ;)

---

### Post by petejk on 2010-03-07
thanks Madman2k - that worked just fine for me.
Sorted!

Pete

---

### Post by andrewthomas on 2010-03-14
I just did a fresh install of the alpha 3 today on a new box. After two sets of updates, multiple reboots and zero configuration changes. I have the new login screen, yet I have the old wallpaper.  What is up with that?

---

### Post by Atermoon on 2010-03-14
> **andrewthomas said:**
> I just did a fresh install of the alpha 3 today on a new box. After two sets of updates, multiple reboots and zero configuration changes. I have the new login screen, yet I have the old wallpaper.  What is up with that?

Because alpha 3 still had the old artwork. Change the wallpaper to something else and then again to warty-final and you'll see it updated. As you can see it's the new one on the thumbnail.

---

### Post by andrewthomas on 2010-03-14
> **Atermoon said:**
> Because alpha 3 still had the old artwork. Change the wallpaper to something else and then again to warty-final and you'll see it updated. As you can see it's the new one on the thumbnail.
Yeah, that worked.  Thanks.  It is weird that this didn't happen on any of my other installs.  On the others the wallpaper would just change itself while the updates were being applied.

---

### Post by Atermoon on 2010-03-14
> **andrewthomas said:**
> Yeah, that worked.  Thanks.  It is weird that this didn't happen on any of my other installs.  On the others the wallpaper would just change itself while the updates were being applied.

No idea, 2 of my installs + my girlfriend's laptop were stuck with the old one after the update and had to "refresh" it (change to another and change back) to see the new one. My other 2 had different wallpapers so I assumed it was normal behavior.

---

### Post by mwolfe on 2010-03-22
I just upgraded 9.10 to 10.04 the other day and I'm getting the brown login screen, everything else seems good though.
I upgraded both my desktop and my laptop (I have a second partition with 9.10 on it if anything should go wrong).
Anyways, I want to warn people not to just blindly delete everything in /var/lib/gdm with the command:
 rm -rf /var/lib/gdm
The reason is that there are some other applications the user may have installed which have configuration files living in that directory. I figured they would handle it gracefully, however I got several warnings after deleting the directory, and i get the warnings everytime I boot up. (The warning was something about .ICEauthority file being missing). Anyways, this was just on my laptop which I don't use very often, I ended up deleting that install, and installing a clean version of lucid beta 1 instead and now everything is working good (more or less).

Thus, i'd recommend not blowing out the full directory, but instead I'd recommend deleting /var/lib/gdm/.gconf as someone mentioned in the comment for the bug report here:
[https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/532659/comments/10](https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/532659/comments/10)
If you do decide to delete the directory, do yourself a favor and back the files up first in case you get errors after.

---

