---
title: "No autologin after update 11.04 + Gnome-shell"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Davo_80 on 2011-05-01
Hi,

I upgraded to Ubuntu 11.04 and installed Gnome 3 (gnome-shell) instead of the Unity environment. 

Since I installed Gnome, Autologin doesn't work any more, even if I set it up to do so, or even manually in the custom.conf file of GDM...

I don't know where to look next...

Thanks for your help.

Dave

---

### Post by cbowman57 on 2011-05-02
I'm looking for a solution to this too.

---

### Post by rezonatix3 on 2011-05-04
I can't get it to work either. I gather that the login settings are stored in [/etc/gdm/custom.conf](http://projects.gnome.org/gdm/docs/2.14/configuration.html?pagewanted=all), but I can't get GDM to automatically login to my main account.

**Edit:** Still no solution, but I did a fresh install of Ubuntu 11.04 and set my user to autologin during the install. This is the custom.conf file created by the installer:

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=user
TimedLoginEnable=true
TimedLogin=user
TimedLoginDelay=10

```
This successfully autologins into Unity. Autologin is disabled by changing the first line, AutomaticLoginEnable:

```

[daemon]
AutomaticLoginEnable=false
AutomaticLogin=user
TimedLoginEnable=true
TimedLogin=user
TimedLoginDelay=10

```
However, once I install Gnome 3 (with the commands below), the AutomaticLoginEnable line doesn't work anymore.

```

sudo apt-add-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
sudo apt-get install gnome-session

```
So custom.conf works perfectly under Unity, but not under Gnome 3 ...

---

### Post by Deadboy420 on 2011-05-04
Would also appreciate and answer to this problem. Auto-login works with Gnome 3 in Fedora 15.

---

### Post by cbowman57 on 2011-05-04
> **Deadboy420 said:**
> .... Auto-login works with Gnome 3 in Fedora 15.

Suse has no problem with it either.

---

### Post by rezonatix3 on 2011-05-07
So what are the differences between Ubuntu and Fedora/SuSE? What does /etc/gdm/custom.conf look like on the latter systems?

---

### Post by cbowman57 on 2011-05-07
> **rezonatix3 said:**
> So what are the differences between Ubuntu and Fedora/SuSE? What does /etc/gdm/custom.conf look like on the latter systems?

Good question, 

custom.conf from natty

```
[daemon]
TimedLoginEnable=False
AutomaticLoginEnable=False
TimedLogin=username
AutomaticLogin=username
TimedLoginDelay=5
DefaultSession=gnome-shell
```

from suse

```
# GDM configuration storage
#
# Note: settings from /etc/sysconfig/displaymanager have a higher priority
#

[daemon]

[security]

[xdmcp]

[greeter]

[chooser]

[debug]

```

What do you think?

---

### Post by Gabriel_Marie on 2011-05-07
Fedora 15 beta's /etc/gdm/custom.conf 


```
# GDM configuration storage

[daemon]

AutomaticLoginEnable=True
AutomaticLogin=*username*

[security]

[xdmcp]

[greeter]

[chooser]

[debug]

```

username = actual user's name

---

### Post by cbowman57 on 2011-05-08
> **Gabriel_Marie said:**
> Fedora 15 beta's /etc/gdm/custom.conf 


```
# GDM configuration storage

[daemon]

AutomaticLoginEnable=True
AutomaticLogin=*username*


```

username = actual user's name

Yeah, I tried it that way too but it was a no-go. :(

---

### Post by Gabriel_Marie on 2011-05-08
As much as I've enjoyed Ubuntu over the past few releases, the decision to use Unity as the default caused me to move to Fedora 15--at least until 11.10 is released. In Fedora 15, Gnome 3 is full-featured, looks great, and "it just works."  I'm confident that, in time, Ubuntu and it's users will slowly iron out all the kinks in Gnome 3, but as of now it's just too unstable and lacking functionality for me.

---

### Post by Davo_80 on 2011-05-11
Hello all,

Thank you for the plentiful replies. Apparently, many people have the same problems as I do: 
- Unity doesn't fullfill needs, 
- Gnome 3 doens't autologin after the switch from Unity
- General usability has gone down... compared to Gnome 2 which I used for many many years

I switched to Ubunty 10 after Mandriva got a bit disorganized on the company level; unfortunately Ubunty 11 is a let-down too.

I'm awaiting the Fedora 15 release in about 14 days...

Kind regards.

---

### Post by Quackers on 2011-05-11
This was a known problem several weeks ago. You must appreciate that gnome3/gnome-shell is still experimental in Ubuntu. Depending on which ppa you used, if you visit that ppa you will see that there aren't that many people working on it at the moment. 
Things take time.

On a different note, I have tried Fedora and openSUSE with gnome-shell and I agree they work just fine.
There is no reason to suspect that this will not be the case in Ubuntu in time.

---

### Post by cbowman57 on 2011-05-11
Well I'm sure not going to bail on Ubuntu because of autologin problems.
In the time it would take me to achieve the familiarity with another Distro that I have with Ubuntu the bugs will be worked out.

And from what I've seen, Gnome 3.0 on Fedora, Suse & Arch have no more functionality than my Gnome 3.0 on Ubuntu.

---

### Post by Quackers on 2011-05-11
> **cbowman57 said:**
> Well I'm sure not going to bail on Ubuntu because of autologin problems.
In the time it would take me to achieve the familiarity with another Distro that I have with Ubuntu the bugs will be worked out.

And from what I've seen, Gnome 3.0 on Fedora, Suse & Arch have no more functionality than my Gnome 3.0 on Ubuntu.

Can't argue with common sense :-)
I agree 100%. The only problems I'm having at the moment (after initially getting it running) is not being able to start the Unity or Classic desktops and the lack of autologin - which isn't a problem for me.
It's working just fine apart from those minor matters :-)

---

### Post by cbowman57 on 2011-05-11
> **Quackers said:**
> Can't argue with common sense :-)
I agree 100%. The only problems I'm having at the moment (after initially getting it running) is not being able to start the Unity or Classic desktops and the lack of autologin - which isn't a problem for me.
It's working just fine apart from those minor matters :-)

Really?  Other than the persistent autologin bug I'm not having that problem.  I just popped out and snapped this pic to verify.

---

### Post by Quackers on 2011-05-11
You're just bragging now :wink:
How did you upgrade? Which ppa, please?

---

### Post by cbowman57 on 2011-05-11
> **Quackers said:**
> You're just bragging now :wink:
How did you upgrade? Which ppa, please?

A little bit. :)

I actually made a custom iso (not what I consider a distro), a link is in my signature.  But here are the sources I use on this particular installation (might be a tad bit different than what's on the iso):


```
deb http://archive.ubuntu.com/ubuntu natty main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ natty-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu natty-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu natty-proposed universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu natty-backports universe main multiverse restricted
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu natty main #Ubuntu Chromium - Daily Builds PPA
deb http://ppa.launchpad.net/n-muench/firefox-daily/ubuntu natty main #Firefox Daily Builds
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu natty main #Awn Testing Team PPA
deb http://ppa.launchpad.net/dockbar-main/ppa/ubuntu natty main #Dockbar Main Group PPA
deb http://ppa.launchpad.net/flozz/flozz/ubuntu natty main #FLOZz's PPA
deb http://ppa.launchpad.net/ricotz/testing/ubuntu natty main #GNOME Shell Testing PPA
deb http://ppa.launchpad.net/synapse-core/ppa/ubuntu natty main #Synapse Core PPA
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu natty main #xorg-edgers fresh X crack
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu natty main #X Updates
deb http://ppa.launchpad.net/transmissionbt/beta/ubuntu natty main #Transmission Beta builds
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu natty main #Telepathy PPA
deb http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu natty main #TahuTEK.net PPA Repository
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu natty main #WebUpd8
deb http://ppa.launchpad.net/zeitgeist/ppa/ubuntu natty main #Zeitgeist
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu natty main #Grub Customizer PPA
deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu natty main #Conky Hardcore PPA
deb http://ppa.launchpad.net/banshee-team/banshee-unstable/ubuntu natty main #Banshee unstable builds
# deb http://ppa.launchpad.net/byobu/ppa/ubuntu natty main #byobu PPA
# deb http://ppa.launchpad.net/unity/ppa/ubuntu natty main #Unity packages
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu natty main
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu natty main
deb http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu natty main
# deb-src http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu natty main
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu natty main
# deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu natty main
deb http://ppa.launchpad.net/sikon/steadyflow/ubuntu natty main
# deb-src http://ppa.launchpad.net/sikon/steadyflow/ubuntu natty main
deb http://ppa.launchpad.net/nikount/orta-desktop/ubuntu natty main
# deb-src http://ppa.launchpad.net/nikount/orta-desktop/ubuntu natty main
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu natty main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu natty main
deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu natty main
# deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu natty main
```

---

### Post by Quackers on 2011-05-11
Interesting, thanks :-)
I'm sure I'll break mine at some time in the near future, so I've bookmarked this for future use :-)

---

### Post by cbowman57 on 2011-05-11
> **Quackers said:**
> You're just bragging now :wink:
How did you upgrade? Which ppa, please?

Just noticed that I don't have the UGR ppa on this installation, though at one time I might have.  This one is what I based the 64-bit iso on.  Pretty sure the 32-bit version uses the UGR ppa but it's fully functional as well, and includes a light installation of LXDE that was pulled in with lxdm, which I used to bypass gdm for the live 32-bit iso.

---

### Post by cbowman57 on 2011-05-11
> **Quackers said:**
> Interesting, thanks :-)
I'm sure I'll break mine at some time in the near future, so I've bookmarked this for future use :-)

Clonezilla & alt-f2 gnome-shell --replace are our friends. :D

---

### Post by Quackers on 2011-05-11
Oh yes, or just Alt+F2 and r :-)

---

### Post by cbowman57 on 2011-06-04
> **Davo_80 said:**
> Hi,

I upgraded to Ubuntu 11.04 and installed Gnome 3 (gnome-shell) instead of the Unity environment. 

Since I installed Gnome, Autologin doesn't work any more, even if I set it up to do so, or even manually in the custom.conf file of GDM...

I don't know where to look next...

Thanks for your help.

Dave

I know this thread is a month old but I finally found the autologin solution.  Force downgrade to gdm 2.32, works like a charm, just toggle it on through system settings >> user account.

---

### Post by webbsd on 2011-07-04
Downgrading to 2.32 didn't work for me :(

I did notice an error in /var/log/gdm/:0-slave.log about not being a member of group nopasswdlogin. However, even when added to this group gdm won't autologin.

Steve.

---

### Post by cbowman57 on 2011-07-05
> **webbsd said:**
> Downgrading to 2.32 didn't work for me :(

I did notice an error in /var/log/gdm/:0-slave.log about not being a member of group nopasswdlogin. However, even when added to this group gdm won't autologin.

Steve.

What happens if you activate it via Login Screen Setting?

[ATTACH]196828[/ATTACH]

---

### Post by nafik on 2011-07-06
I have same issue. Fresh install of 11.04 with Gnome 3 and GDM v3.0.4 (ubuntu gnome remix ppa). I can set auto login (enable it) for my account in settings window, however when I close this window and reopen it I can see old settings (disabled auto login).
Is there in gnome 3 something like gconf-tool in gnome2? That might be way...

---

### Post by nafik on 2011-07-06
I tried to start gnome-control-center in gnome-terminal and set autologin.
I got this error in console:
(gnome-control-center:2367): user-accounts-cc-panel-WARNING **: SetAutomaticLogin call failed: failed to change automatic login: No such file or directory

So I tried to create /etc/gdm/custom.conf and add there
[I][daemon]
AutomaticLoginEnable=true
AutomaticLogin=user[/I]
. Then I see no error in console after setting autologin and it holds "enable status". However after rebooting system GDM won't start and I get to console, not to X.

---

### Post by lzap on 2011-07-18
You are missing one line from your config file. It should be:

```
[daemon]
TimedLoginEnable=true
TimedLogin=students
TimedLoginDelay=0
```

---

### Post by stefan.hattrell on 2011-10-02
Thanks lzap. That's a good interim solution for now, using the TimedLogin directive. The AutoLogin directive doesn't seem to work.

It now logs in fine and I can shadow the session with NX too which is what I was trying to figure out!

---

### Post by stefan.hattrell on 2011-10-02
Dave can you test this solution and mark the thread as SOLVED if it works?

---

### Post by ZooDirt on 2011-10-13
This solution worked for me. Thanks, Fellas!   My /etc/gdm/custom.conf file was missing so I created one.   Contents are below:

```

[daemon]
TimedLoginEnable=True
TimedLogin=ZooDirt
TimedLoginDelay=0
DefaultSession=gnome-shell

```

---

