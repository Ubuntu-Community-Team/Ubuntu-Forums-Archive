---
title: "Upgrade wants to remove nautilus, xorg etcetc"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-10-10
Just a heads up, synaptic currently wants to remove essential packages like nautilus, xorg and so on. Dont do it :) Wait for the updates to fix it.

---

### Post by plun on 2008-10-10
Yup... its a major breakage for the moment.

---

### Post by philinux on 2008-10-10
Strange, not happening here. Just one package kept back.  libxi6

---

### Post by Efros on 2008-10-10
Borked my system, get "No exec line in the session file: gnome", oh well welcome to beta land!

---

### Post by Nullack on 2008-10-10
Fellow testers who succumb to this can eventually get over it by updating from the command line :

sudo apt-get update
sudo apt-get upgrade

Once the repos are sorted :)

---

### Post by wgrant on 2008-10-10
> **philinux said:**
> Strange, not happening here. Just one package kept back.  libxi6

That's due to the set of uploads we've done over the past few hours to hopefully fix some input property and thus touchpad problems. A few more pieces to fall into place until it's fixed, however.

---

### Post by plun on 2008-10-10
Well... apt is still a supported "noble art" and some users perhaps
prefer this knowledge...:-\"

aptitude also....:)

[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)


Broken nevertheless....  just a normal condition for a test version.

---

### Post by philinux on 2008-10-10
Make that 2. LOL libxi6 xinput

I was offered a partial upgrade which i always cancel. Debconf just got updated though.

---

### Post by ronacc on 2008-10-10
thanks for the heads up. I'm looking at about 20 "held back" packages here I was going to sort through them to try to prune the list but now I'll just wait awhile longer .

---

### Post by plun on 2008-10-10
Its probably this package...  "brown bag"..

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008361.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008361.html)

EDIT
> 
The following packages are BROKEN:
  libxi6 


---

### Post by jfernyhough on 2008-10-10
Crap. I just did a "mark all upgrades" in Synaptic and applied it. Then I noticed I had residual config for nautilus and gnome-session... not good, I thought.

---

### Post by philinux on 2008-10-10
Ah I see what synaptic wants to do. I'll pass on that. :)

---

### Post by plun on 2008-10-10
Yup this is the challenge

> **libxi6**: Breaks: gnome-control-center (<= 1:2.24.0.1-0ubuntu3) but 1:2.24.0.1-0ubuntu3 is to be installed.
          Breaks: gnome-settings-daemon (<= 2.24.0-0ubuntu1) but 2.24.0-0ubuntu1 is to be installed.

Broken...

---

### Post by philinux on 2008-10-10
> **jfernyhough said:**
> Crap. I just did a "mark all upgrades" in Synaptic and applied it. Then I noticed I had residual config for nautilus and gnome-session... not good, I thought.

Just dont logout or reboot. Just keep updating via the terminal.

sudo apt-get update && sudo apt-get upgrade

---

### Post by wgrant on 2008-10-10
> **plun said:**
> Its probably this package...  "brown bag"..

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008361.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008361.html)


That is related, but it's not the cause. It would have just meant we would have had to retry it manually, rather than having Launchpad automatically retry when the new libxi-dev came along.

---

### Post by wgrant on 2008-10-10
> **plun said:**
> Yup this is the challenge

Broken...

gnome-settings-daemon will be installable from archive.ubuntu.com in a few minutes, and gnome-control-center in a little over an hour. I think that should just about fix everything.

---

### Post by dro0g on 2008-10-10
I got hit by this and am patiently waiting at an xterm failsafe session for the update :)

---

### Post by plun on 2008-10-10
Well, I am still at a GUI....:)


> The following packages are BROKEN:
  xserver-xorg-core 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2470kB of archives. After unpacking 4096B will be used.
The following packages have unmet dependencies:
  xserver-xorg-core: Breaks: xserver-xorg-input-evdev (<= 1:2.0.99+git20080912-0ubuntu2) but 1:2.0.99+git20080912-0ubuntu2 is installed.
                     Breaks: xserver-xorg-input-synaptics (<= 0.15.2-0ubuntu3) but 0.15.2-0ubuntu3 is installed.
The following actions will resolve these dependencies:
Remove the following packages:
xserver-xorg-input-all
xserver-xorg-input-evdev
xserver-xorg-input-synaptics


Just to wait...

---

### Post by darrenm on 2008-10-10
I've just forced xserver-xorg-input-evdev in because my keyboard and mouse wouldn't work in X.

I'm back in X now in KDE4 but I can't run the display config to set up my screen correctly. Waiting for the packages...

---

### Post by dro0g on 2008-10-10
OK, just got an update and it's back up! I had to run 'sudo apt-get install ubuntu-desktop' to get everything back.

---

### Post by bash on 2008-10-10
Hmm ... still borked for me. Installed the update in good faith ;)

Now I just can't restart the PC 'till a fixed ubuntu-desktop is available again. Oh well could be worse.

---

### Post by jstalin on 2008-10-10
Same here, still no keyboard or mouse.

---

### Post by Macius_Pl on 2008-10-10
:lolflag: I write from livecd 8.04 , in intrepid no keyboard and mouse in log screen . :lolflag::lolflag::lolflag:

---

### Post by plun on 2008-10-10
> **bash said:**
> Hmm ... still borked for me. Installed the update in good faith ;)

Now I just can't restart the PC 'till a fixed ubuntu-desktop is available again. Oh well could be worse.

Ok from "Main"   :)


So its clear for all:


Kubuntu

```
sudo apt-get install kubuntu-desktop
```

Ubuntu

```
sudo apt-get install ubuntu-desktop
```

---

### Post by zoomy942 on 2008-10-10
but how do i get to that screen?  i mean, i get to the login and cant do anything.  how do i get it so i can update?

EDIT : cancel that.  Alt F1 worked, but i type in the sudo apt-get install ubuntu-desktop and i get error about natalius depencies and gnome panel and gnome session...

what can i do?

---

### Post by jstalin on 2008-10-10
> 
Ubuntu

```
sudo apt-get install ubuntu-desktop
```



Did that, didn't work.

---

### Post by jfernyhough on 2008-10-10
I think I'm back to normal...

Try sudo aptitude reinstall ubuntu-desktop

Otherwise check synaptic under sections, residual config, and reinstall the missing stuff.

---

### Post by bash on 2008-10-10
> **plun said:**
> Ok from "Main"   :)


So its clear for all:


Kubuntu

```
sudo apt-get install kubuntu-desktop
```

Ubuntu

```
sudo apt-get install ubuntu-desktop
```

I know that. It just still reports broken packages for me. Maybe the CH mirror is not updated yet.

---

### Post by darrenm on 2008-10-10
A apt-get dist-upgrade should be enough as there is an update to xserver-xorg-input-evdev 

Try apt-get update ; apt-get -f install first if it doesn't work.

---

### Post by plun on 2008-10-10
Well its seems to be some trouble with mirrors

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)


sources.list can be edited but it can also cause more trouble....  :-k

---

### Post by plun on 2008-10-10
Also important...

```
sudo apt-get update

```
```
sudo apt-get upgrade
```


then

```
sudo apt-get install ubuntu-desktop

```

---

### Post by bash on 2008-10-10
CH mirror is finally updated. Everything seems to be fine again. Updating now.

---

### Post by iponeverything on 2008-10-10
I got bit this, but is fairly easy to back out with what I had in /var/cache/apt/archives

first install the libxi6_2%3a1.1.3-1ubuntu2_i386.deb and 
xinput_1.3.0-1ubuntu2_i386.deb and then it will let you reinstall the others with:

dpkg -i ubuntu-desktop_1.119_i386.deb fast-user-switch-applet_2.24.0-0ubuntu2_i386.deb gnome-applets_2.24.0.1-0ubuntu1_i386.deb gnome-applets-data_2.24.0.1-0ubuntu1_all.deb gnome-panel gnome-control-center_1%3a2.24.0.1-0ubuntu3_i386.deb gnome-session_2.24.0-0ubuntu1_i386.deb nautilus_1%3a2.24.0-0ubuntu2_i386.deb nautilus-cd-burner_2.24.0-0ubuntu1_i386.deb gnome-panel_1%3a2.24.0-0ubuntu1_i386.deb gnome-panel-data_1%3a2.24.0-0ubuntu1_all.deb gnome-settings-daemon_2.24.0-0ubuntu1_i386.deb

I didn't have network, so I had to come up with another idea..

---

### Post by jstalin on 2008-10-10
Updates ran, installed ubuntu-desktop, still no mouse or keyboard.

---

### Post by iponeverything on 2008-10-10
> **jstalin said:**
> Updates ran, installed ubuntu-desktop, still no mouse or keyboard.

can you log into your machine remotely?  if so try:

apt-get update
apt-get upgrade
and just for fun:
apt-get install xinput

also restart x with ctl-alt-bksp

---

### Post by jstalin on 2008-10-10
> **iponeverything said:**
> can you log into your machine remotely?  if so try:

apt-get update
apt-get install xinput

also restart x with ctl-alt-bksp


Yes, it says that xinput is already the newest version. I believe that updated with my apt-get update a fwe minutes ago.

---

### Post by Stingr on 2008-10-10
I had set my keyboard layout to Evdev-managed keyboard yesterday to troubleshoot a problem with freenx.  Taking a cue from darrenm above I ran:

```
sudo apt-get --reinstall install xserver-xorg-input-evdev
```

from a console and then restarted GDM by doing:

```
sudo /etc/init.d/gdm restart
```

That fixed it for me (Thanks darrenm).  If it works for you don't forget to switch back to your console and logout.

Hope this helps.

---

### Post by jstalin on 2008-10-10
Stingr - that did it, thanks so much!

---

### Post by zoomy942 on 2008-10-10
> **Stingr said:**
> I had set my keyboard layout to Evdev-managed keyboard yesterday to troubleshoot a problem with freenx.  Taking a cue from darrenm above I ran:

```
sudo apt-get --reinstall install xserver-xorg-input-evdev
```

from a console and then restarted GDM by doing:

```
sudo /etc/init.d/gdm restart
```

That fixed it for me (Thanks darrenm).  If it works for you don't forget to switch back to your console and logout.

Hope this helps.


that did it for me!  thanks!

---

### Post by cokelly72 on 2008-10-10
> **Stingr said:**
> I had set my keyboard layout to Evdev-managed keyboard yesterday to troubleshoot a problem with freenx.  Taking a cue from darrenm above I ran:

```
sudo apt-get --reinstall install xserver-xorg-input-evdev
```

from a console and then restarted GDM by doing:

```
sudo /etc/init.d/gdm restart
```

That fixed it for me (Thanks darrenm).  If it works for you don't forget to switch back to your console and logout.

Hope this helps.

Thanks for this - it got my keyboard working again. No mousepad though... I'll keep trying.

---

### Post by punischdude on 2008-10-10
Downgrading to

```
/var/cache/apt/archives/xserver-xorg-core_2%3a1.5.1-1ubuntu2_amd64.deb

/var/cache/apt/archives/xserver-xorg-input-synaptics_0.15.2-0ubuntu3_amd64.deb

/var/cache/apt/archives/xserver-xorg-input-evdev_1%3a2.0.99+git20080912-0ubuntu2_amd64.deb
```

worked around for me.

---

### Post by cokelly72 on 2008-10-10
Ah - I had uninstalled the synaptics driver at some stage. Silly me. Thanks to previous posters for all the help.

---

### Post by Ewzzy on 2008-10-10
> **Stingr said:**
> I had set my keyboard layout to Evdev-managed...

Thanks, you saved my ***.

---

### Post by jackgu1988 on 2008-10-10
> **Stingr said:**
> I had set my keyboard layout to Evdev-managed keyboard yesterday to troubleshoot a problem with freenx.  Taking a cue from darrenm above I ran:

```
sudo apt-get --reinstall install xserver-xorg-input-evdev
```

from a console and then restarted GDM by doing:

```
sudo /etc/init.d/gdm restart
```

That fixed it for me (Thanks darrenm).  If it works for you don't forget to switch back to your console and logout.

Hope this helps.that made my keyboard work! but not the mouse! what should i do now? thanks

---

### Post by plun on 2008-10-10
This is the packages which was removed

> Remove the following packages:
xserver-xorg-input-all
xserver-xorg-input-evdev
xserver-xorg-input-synaptics 


I think  :)...so reinstall those packages and see if it works.

---

### Post by Efros on 2008-10-10
Multiple updates from command line eventually realized that Gnome wasn't on the session list so installed gnome and got back to a working system. What fun we are having!!!:)

---

### Post by linomac on 2008-10-10
The same issue happened to me twice too.
aptitude and adept were proposing me to remove basic system packages like kubuntu desktop, xorg etc. 
I did not accept. i waited 15 minutes and kept updating and asking for upgrading till the moment that it did not ask me to remove any of the basic software.
I support it has to do with multiple file uploading to the repositories. it is normal to happen with so many updates per date.
I update manually every 10 minutes. every hour there is something to update.
around 100 per day updates.

what i could propose if possibly to be a mechanism in aptitude/apt-get/synaptic/adept that would block removing basic packages

---

### Post by nanog on 2008-10-10
> what i could propose if possibly to be a mechanism in aptitude/apt-get/synaptic/adept that would block removing basic packages

```
sudo apt-get update; sudo apt-get upgrade
```

There really needs to be a sticky about this.

---

### Post by wgrant on 2008-10-10
If you are running Intrepid, you are expected to be intelligent enough to notice when something is removing lots of packages that don't look obsolete.

---

### Post by mobrien118 on 2008-10-12
> **wgrant said:**
> If you are running Intrepid, you are expected to be intelligent enough to notice when something is removing lots of packages that don't look obsolete.

"**Intelligence is no substitute for information**; enthusiasm is no substitute for ability; willingness is no substitute for experience; and a meeting is no substitute for progress."
--Patrick Lencioni, 'Death by Meeting'

Anyway, thanks all for the fix. reinstalling xserver-xorg-input-evdev worked for me too.

---

### Post by wgrant on 2008-10-12
> **mobrien118 said:**
> "**Intelligence is no substitute for information**; enthusiasm is no substitute for ability; willingness is no substitute for experience; and a meeting is no substitute for progress."
--Patrick Lencioni, 'Death by Meeting'

Anyway, thanks all for the fix. reinstalling xserver-xorg-input-evdev worked for me too.

We can't prevent people from removing these packages, because people are likely to legitimately want to remove them. They're useless on servers, for example.

---

### Post by philinux on 2008-10-12
> **wgrant said:**
> if you are running intrepid, you are expected to be intelligent enough to notice when something is removing lots of packages that don't look obsolete.

+1 

You're also not supposed to run Intrepid on your main machine. Rule number 1.

---

### Post by quazi on 2008-10-12
> **wgrant said:**
> We can't prevent people from removing these packages, because people are likely to legitimately want to remove them. They're useless on servers, for example.

On the other hand, Synaptic certainly shouldn't be advocating their removal.

---

