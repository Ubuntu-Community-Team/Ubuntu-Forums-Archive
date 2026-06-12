---
title: "Edgy upgrade crashed destkop to white"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Mau on 2006-10-27
After upgrading to Edgy, my desktop is now pure white.  Everything boots up fine, but after I type in my password, I see the Ubuntu loading screen and then everything turns white with grey areas where some of the panels are suppose to be. Any idea on how to fix this?

Edit: Running my XGL profile gives me the desktop (XGL not working, but whatever).  Still, I would like my gnome profile to work.

---

### Post by Crusher on 2006-10-27
I am also experiencing this problem.

---

### Post by Mau on 2006-10-27
Anybody have any ideas on this?

---

### Post by tojge on 2006-10-27
Yeah, the (almost) exact same thing happens to me, apart from the fact my desktop is more pink-ish than white... And I get to see the top and bottom panels, and that's about it :( 

It is also true that Xgl logs in fine (well, so to speak...), but with no 3D accel. and a desktop looking like it came straight out of the mid-1994.

Any ideas would be greatly appreciated, thanks...

---

### Post by UltraMathMan on 2006-10-27
Same problem, white screen then xserver crashes, hopefully there will be some fix soon. I have a ATI Mobility X1400 256MB w/ Hypermemory in an Inspiron E1505 using the fglrx driver. I tried reconfiguring the xserver and setting the driver to vesa, but then I didn't even get to the login screen. There is also no splash displayed on boot.

---

### Post by Mau on 2006-10-28
Hey guys,
I put two and two together, and realized that if I create a new user account, I can login.  So, it seems to be a problem with our profile.  Anyone know how to reset your profile?

---

### Post by CarpKing on 2006-10-28
I'm having a similar problem, though I see some of the items on the panel for a brief second before they disappear and I'm left with the pinkish background.

---

### Post by IanVaughan on 2006-10-28
I get the same problem. (with a GNOME login, shows loading splash screen, and then blanks to white. After that returns to the login window. Also XGL login works but also in low graphics mode)

So what is the solution? Do we have to create a new login?
Or is it just a conf setting need correcting?

How can this happen with an upgrade? During the update, I replaced any upgraded conf files that the update prompted me about!

(bumping...)

---

### Post by jetthe on 2006-10-28
This might be totally unrelated, but I experienced pretty much the same thing after upgrading to Edgy from Dapper. Running the fglrx driver from the repos on my R9800 seemed to cause some problems with AIGLX.

My problem was solved by adding the following to my xorg.conf to disable AIGLX:

```

Section "Extensions"
        Option          "Composite"     "disable"
EndSection

```

---

### Post by IanVaughan on 2006-10-28
Trying both, creating a new user and adding the following on the old exiting account both worked fine.

> **jetthe said:**
> My problem was solved by adding the following to my xorg.conf to disable AIGLX:

```

Section "Extensions"
        Option          "Composite"     "disable"
EndSection

```

---

### Post by IanVaughan on 2006-10-28
Ok, I posted to soon!  I found that adding that "Extensions" in to xorg.conf did NOT do the trick, as I could still NOT login as my normal account.

BUT if I created a new account, I could login fine with that (without the "Extensions" lines in xorg.cong).

SO there must by some setting in my "profile"/home-folder?! But what???
As a bit of a noobe, I need pointing in the right direction! Anyone got any ideas??

(An alternative would be to switch over to this now working second account, but its not got sudoers rights, and the terminal is all wrong! (no auto-complete on tab, all arrows produce chars!!))

---

### Post by CarpKing on 2006-10-28
Okay, I managed to get my normal account default session to work.  Here's what I did (I have no idea which of these steps may be necessary; some may even have been harmful):

I read at [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues) that fglrx might be disabled in /etc/default/linux-restricted-modules-common, so I checked there and it was not disabled.  I then opened up /etc/X11/xorg.conf and noticed in the text at the top that it only gets upgraded if it hasn't been modified since its last upgrade.  It said you could force it to upgrade with ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
After I did that and rebooted, I got a text screen that said X failed to start.  The log it showed me said that no proper driver was found or something to that effect.  After that it spit me out into a black screen where I could type but not enter any commands; I hit Ctrl+Alt+F1 and logged in.  I made sure that xserver-xorg-driver-ati and xorg-driver-fglrx were installed (they both already were) and then did ```
sudo dpkg-reconfigure xserver-xorg
```
After going through that process (changed ati to fglrx, left the rest of the defaults), I typed startx and got a normal desktop.  I rebooted and then logged into my default session and everything seems fine except that fglrxinfo still says mesa, and my XGL session still puts me into low-graphics mode.  I'm going to try going through the process of enabling 3d again and see if that helps.  

Hopefully some part of this will help some of you.

---

### Post by CarpKing on 2006-10-28
Okay, well, following the steps for Edgy on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), fglrxinfo now displays my card's name.  XGL session still puts me into low-graphics mode though, so no Beryl. ;_;

I think the next step will be to uninstall Beryl and XGL, then reinstall them using instructions for Edgy (forgot to mention that last night one of the things I did was reinstall fglrx, though I don't know if this specifically had any effect on my later success).

---

### Post by tojge on 2006-10-28
> **CarpKing said:**
> ...(forgot to mention that last night one of the things I did was reinstall fglrx, though I don't know if this specifically had any effect on my later success).Well, I think it did, because that's pretty much all I did (logged into Xgl session, of course, since GNOME was not usable), and what do you know, after a reboot, there was my good ol' GNOME desktop. Now, of course, I am not able to get Beryl to work, Xgl loads fine, but Beryl keeps complaining about "no composite extension", but that's an entirely different and unrelated story...

And yeah, before you ask, I completely removed Beryl and all related packages first, and then reinstalled and reconfigured them, but still no luck... Oh, well... At least it reminded me of how faster GNOME is :-)

---

### Post by UltraMathMan on 2006-10-28
EDIT: followed the instructions here and now I have GNOME again:mrgreen: 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
----------------------------
ORIGINAL POST
ok, I went through and did ```
aptitude reinstall xserver-xorg-video-ati
aptitude reinstall xorg-driver-fglrx
dpkg-reconfigure -phigh xserver-xorg
``` from the recovery console and then ran ```
startx
``` and GNOME started without any problems. I reboot and try to log in to GNOME and the xserver crashes...

---

### Post by IanVaughan on 2006-10-29
> **UltraMathMan said:**
> and GNOME started without any problems. I reboot and try to log in to GNOME and the xserver crashes...
Do you mean to say that the problem still exists?

As I have still to resolve it myself. Having following the reinstalls you posted, rebooted and my existing working login still doesn't load, it just shows the splash screen after login and then logs off again!

The new account I created after having these problems however does work, so this indicates that it is NOT a xorg.cong problem! But I do not know enough to find out what it could be?!

---

### Post by UltraMathMan on 2006-10-29
No, my regular GNOME session is working again (though I haven't checked XGL) the following details what I did to get it working:

Boot into recovery console of newest kernel

```
aptitude upgrade
aptitude dist-upgrade
aptitude reinstall xserver-xorg-video-ati
aptitude reinstall xorg-driver-fglrx
aptitude install fglrx-control
depmod -a
aticonfig --intitial
aticonfig --overlay-type=Xv

nano /etc/X11/xorg.conf

```
and added the following to the end of the file
```
Section "Extensions"
        Option      "Composite" "0"
EndSection
```
then I did ```
dpkg-reconfigure -phigh xserver-xorg
``` and then tested it with ```
startx
``` which booted me into a working GNOME recovery session. I then rebooted and logged into my normal GNOME session which loaded without going white or crashing.

---

### Post by BungaMan on 2006-11-09
I've experienced the same issue after upgrading from dapper to edgy.  After rebooting and typing in login and password I got a white screen with a bit of gray area's at the top right.  This is only for the login which performed the upgrade.  Other logins work fine and new ones as well.  I suspected it had something to do with the user rather than xorg not being configured correctly so I renamed a few of the .gnome .gconf directories and it changed the problem to having the default background color (pinkish?) and my desktop icons showing up but no panels and all gnome programs that load automatically caused CORBA errors complaining about not able to add client to server list etc...  After some googling I found a few tips.  I undid all the renaming of directories and performed the following actions to finally fix the story.

first, in a console cd to the home dir of the user which has this problem.

$ cd /home/<username>

Next remove all files with a lock related to gconf (this can be one of the causes)

$ rm -rf .gconf*/*lock*

and then cd into .gconfd

$ cd .gconfd

and remove any saved states (the next plausible cause).

$ rm saved_state*

and that's it.  if you now start up with the troubled user account the problems hopefully vanished.

---

