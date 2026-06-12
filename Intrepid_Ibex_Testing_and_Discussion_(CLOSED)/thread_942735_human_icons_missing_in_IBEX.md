---
title: "human icons missing in IBEX"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Keen101 on 2008-10-09
I have been running Ibex since alpha on my external USB HDD. But, The Gnome Human icons are not there. At first i thought it was just a bug from alpha, that would eventually get fixed by updates. But, i have seen others post screenshots, and those systems look fine. I am mostly annoyed at the logout and shutdown icons, they seem to have reverted back to the default gnome icons. I suppose a wokaround would be to install a different icon theme, but i'd like to get this fixed.

---

### Post by Rocket2DMn on 2008-10-09
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by amano on 2008-10-09
I cannot confirm that, My human icons are all still in place...

---

### Post by swj on 2008-10-09
You may have better luck downloading the beta and installing again?

---

### Post by wgrant on 2008-10-09
> **Keen101 said:**
> I have been running Ibex since alpha on my external USB HDD. But, The Gnome Human icons are not there. At first i thought it was just a bug from alpha, that would eventually get fixed by updates. But, i have seen others post screenshots, and those systems look fine. I am mostly annoyed at the logout and shutdown icons, they seem to have reverted back to the default gnome icons. I suppose a wokaround would be to install a different icon theme, but i'd like to get this fixed.

Do you have human-icon-theme installed? Do you have it selected in System->Preferences->Appearance->Customise?

---

### Post by Keen101 on 2008-10-09
> Do you have human-icon-theme installed? Do you have it selected in System->Preferences->Appearance->Customise? 

Yes. I have human-icon-theme installed, and have it selected it appearances settings, but still the system only displays the default gnome icons. As far as I can tell this only affects my system. I'm not going to re-install, i have too much data on this drive now. Plus, it seems like it should be a simple fix.

The human-icon-theme has even gotten at least two updates since i first installed the system. I had originally thought that it was just a bug, and would be fixed by updates.

---

### Post by FuturePilot on 2008-10-09
> **Keen101 said:**
> Yes. I have human-icon-theme installed, and have it selected it appearances settings, but still the system only displays the default gnome icons. As far as I can tell this only affects my system. I'm not going to re-install, i have too much data on this drive now. Plus, it seems like it should be a simple fix.

The human-icon-theme has even gotten at least two updates since i first installed the system. I had originally thought that it was just a bug, and would be fixed by updates.

Have you tried switching to another theme and then back to the Human them so that it reloads the theme?

---

### Post by Keen101 on 2008-10-09
> Have you tried switching to another theme and then back to the Human them so that it reloads the theme?


Yep. That was the first thing i tried.


But, i am going to try and re-install the package with synaptic. I might have already tried that too... i can't remember.

---

### Post by swj on 2008-10-09
> **Keen101 said:**
> i have too much data on this drive now.

Interesting...The only reason I suggested that, is most people do not use development releases as production, otherwise I would have never suggested re-installation...in fact I reinstall at each release to test the installation as well.

---

### Post by Keen101 on 2008-10-09
> Interesting...The only reason I suggested that, is I thought people do not use development releases as production, otherwise I would have never suggested re-installation...in fact I reinstall at each release to test the installation as well.

Hmm... we'll normally i would not have. Normally I would have waited to the final release. But, i got a new computer, and when i tried booting up my external drive with ubuntu 7.04 or 7.10, it could not load the video correctly. I even tried an 8.04 live-cd, but that did not work either. I tried the 8.10 alpha, and it worked, so i used it (with caution).

I don't have so much data on it that if it were lost i'd go crazy. I really don't have that much on it... I do realize that it can be unstable at times. In fact it was one week after updates... the GDM login manager had some bad code in one the updates... I was unable to login. It sucked, but a little digging and i figured out how to edit a config file to get in, and then update again. So, If i were to loose data no big deal... just It seems like such a small problem that there should be a fix for it without re-installing.

---

### Post by Keen101 on 2008-10-09
Okay, I seem to have made progress, but not all the way fixed.

I tried re-installing the human-icons-theme with synaptic. It sems to have fixed almost all the icons. All except the two that bug me the most (the shutdown and logout icons).

here are two new screenshots.

I did a little digging in /usr/share/icons

the gnome icons folder in 24x24 had these icons named:

gnome-session-logout.png
gnome-logout.png
gnome-shutdown.png

but, when exploring /usr/share/icons/Human I find that those icons are missing!!! This must be the root of my problem somehow... but it seems really strange.

I would think that re-installing the package would fix all of the icons. But, they should not be missing at all should they? The screenshot here looks fine...

[http://lifehacker.com/5058730/first-look-at-ubuntu-810-intrepid-ibex-beta](http://lifehacker.com/5058730/first-look-at-ubuntu-810-intrepid-ibex-beta)

and

[http://news.softpedia.com/news/Ubuntu-8-10-Beta-Screenshot-Tour-94796.shtml](http://news.softpedia.com/news/Ubuntu-8-10-Beta-Screenshot-Tour-94796.shtml)

---

### Post by Keen101 on 2008-10-09
whoops. forgot **MY** screenshots...

---

### Post by swj on 2008-10-09
> **Keen101 said:**
> whoops. forgot **MY** screenshots...

I think I understand now...yes, I have the same icons as you.  However, for some reason the human (red) shutdown button has been added to the 'switch users' panel 'item'...in any case, I see the same thing.

---

### Post by Keen101 on 2008-10-09
> **swj said:**
> I think I understand now...yes, I have the same icons as you.  However, for some reason the human (red) shutdown button has been added to the 'switch users' panel 'item'...in any case, I see the same thing.

Wow. Your right. I don't use the user switcher as i am the only user on this machine, but i added it back to see what you are talking about.

So, this is a bug that affects more than just my system?

---

### Post by swj on 2008-10-10
> **Keen101 said:**
> Wow. Your right. I don't use the user switcher as i am the only user on this machine, but i added it back to see what you are talking about.

So, this is a bug that affects more than just my system?

Apparently so...although, I would not be surprised if some new artwork was thrown in before the release...I hope so.  You may want to search for (or file) a bug on this.

---

### Post by Keen101 on 2008-10-10
I have reported it as a bug on launchpad, referencing this thread.

I have also noticed something else. After re-installing the human-icons-theme in synaptic package manager almost all of the icons were fixed. But, now after rebooting they are back reverting to the default gnome icons.

It's not a deal breaker, but certainly annoying for me.

---

### Post by Keen101 on 2008-10-17
this is still a problem. It seems after every restart, they revert back to the default gnome icon theme.

---

### Post by lswest on 2008-10-17
there's a fix posted [here]("http://ubuntuforums.org/showpost.php?p=5964458&postcount=544")

It reads:
> **perfectska04@hotmail.com said:**
> I think that as long as inode-directory icons are installed, there will be many regressions with any icon set (since everything will eventually inherit from gnome). I already submitted a bug to Ubuntu and commented on the bugzilla version, but no one has done anything about it. Anyway, here's a slightly more complete workaround than the one Ub1476 posted:

#This part removes the problem (useless) icons.
sudo rm -f /usr/share/icons/gnome/scalable/places/inode-directory.svg
sudo rm -f /usr/share/icons/gnome/32x32/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/24x24/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/22x22/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/16x16/places/inode-directory.png

#Log out. If for some reason the icons appear as blank after logging out, rebuild gnome-icon-theme's icon cache:
sudo rm -f /usr/share/icons/gnome/icon-theme.cache
sudo gtk-update-icon-cache -qf /usr/share/icons/gnome

---

### Post by shafin on 2008-10-17
It fixed the directory icons for me, but still no fix for the shutdown panel icon. Anyone know how to fix that?

---

### Post by Keen101 on 2008-10-20
We'll I just did updates today. And good news, almost everything is fixed. 

The red shutdown icon is now on the logout button next to the system clock. But, the ugly grey gnome logout icon is still in >System >Shutdown.

while digging around in /usr/share/icons i found some things out. 

1. the grey gnome logout logo refers to **/usr/share/icons/Gnome/24x24/actions/gnome-shutdown.png**

It actually is in all the sizes, not just the 24x24 folder.

2.the **/usr/share/icons/Human/24x24/actions** had a link to the red icon called system-log-out.png. In addition to that we need another link called gnome-shutdown.png in every /actions folder.

**3.** while manually adding links to all my /actions folders i found that in **/usr/share/icons/Human/scalable/actions** that the link "system-log-out.png" was broken. I renamed it "system-log-out.svg" , and manually copied that link and renamed it "gnome-shutdown.svg", but since there seems to be no scalable red shutdown icon neither will work.

also found this bug report on launchpad. [https://bugs.launchpad.net/ubuntu/+source/human-icon-theme/+bug/285832](https://bugs.launchpad.net/ubuntu/+source/human-icon-theme/+bug/285832)

**while i was attempting to manually add all the missing shutdown icon links, i just realized that once this is fixed it will be a little wierd in the >System tab. there will soon be two RED shutdown icons. I think that the logout icon should instead be something like a green arrow pointing downward.**

---

