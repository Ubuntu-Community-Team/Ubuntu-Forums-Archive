---
title: "Jaunty KDE Upgrade Went Bad, cannot reinstall install anything K"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by convert_mrta on 2010-03-17
Hello,

I attempted to upgrade my Korganizer for some improved features, and attempted to use a KDE backport repository for Karmic.  The progress window showed upgrading, but when it was done all things KDE were gone from my menues and system.  Korganizer, Dolphin, etc cannot be called from command prompt.  They're just gone.

I removed the backport repository from Synaptic, and attempted to reinstall the canonical authorized version of KDE, but when I do, I get the error messages below.

It would seem that required packages got broken in the upgrade progress.  And apt refuses to install or re-install missing/broken dependencies.  I don't know how to get KDE, any version back on my system.  

Am I missing a required repository?  I've run apt-get upgrade repeatedly. 

/etc/apt/sources.list us attached.

I've searched these forums and countless other placed on the web to find a solution....I'm baffled.  Would appreciate any help getting KDE, prefereably latest version, but even Canonical offical verison back on my Jaunty system.

Thank you, thank you to anyone who can help.


$ sudo apt-get install korganizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  korganizer: Depends: kaddressbook but it is not going to be installed
              Depends: kdebase-runtime (>= 4:4.2.4) but it is not going to be installed
              Depends: kdelibs5 (>= 4:4.2.4) but it is not going to be installed
              Depends: kdepim-kresources but it is not going to be installed
              Depends: kdepimlibs5 (>= 4:4.2.4) but it is not going to be installed
              Depends: libkdepim4 (= 4:4.2.4-0ubuntu1~jaunty2) but it is not going to be installed
              Depends: libkholidays4 (= 4:4.2.4-0ubuntu1~jaunty2) but it is not going to be installed
              Depends: libqt4-network (>= 4.5.0~+rc1) but it is not going to be installed
              Depends: libqt4-qt3support (>= 4.5.0~+rc1) but it is not going to be installed
              Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
E: Broken packages

$ sudo apt-get install kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core (>= 5:48ubuntu1) but it is not going to be installed
       Depends: kdeedu (>= 4:4.1.1) but it is not going to be installed
       Depends: kdegames (>= 4:4.1.1) but it is not going to be installed
       Depends: kdetoys (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeaccessibility (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeadmin (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeartwork (>= 4:4.1.1) but it is not going to be installed
       Depends: kdegraphics (>= 4:4.1.1) but it is not going to be installed
       Depends: kdemultimedia (>= 4:4.1.1) but it is not going to be installed
       Depends: kdenetwork (>= 4:4.1.1) but it is not going to be installed
       Depends: kdepim (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeutils (>= 4:4.1.1) but it is not going to be installed
       Depends: kdewebdev-kde4 (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeplasma-addons (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

---

### Post by convert_mrta on 2010-03-19
Holy Cow! No ideas from the forum on how to repair a trashed KDE?

I must be in a bad situation.  Really?

Thanks for any help.

---

### Post by Ozymandias_117 on 2010-03-19
One thing you might try, is ```
sudo apt-get install kubuntu-dekstop
``` it will prob install things you won't want, but it should fix the dependency issues.

---

### Post by convert_mrta on 2010-03-19
Thanks for the help, Ozy.  I've tried that before. See attached for results of sudo apt-get install kubuntu-desktop

This message at the top of apt-get install kubunto-desktop is probably significant, but I don't know how to act on the information:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
[COLOR="Red"]or been moved out of Incoming.[/COLOR]
The following information may help to resolve the situation:

<Then the output from install kubuntu-deskop (too long to paste omtp post, so attached)>

Also, at the bottom of the install after the last "Recommends" was this line:  

E: Broken packages

Doesn't *which[I]* packages are broken :)  But *something's* broken.



BTW, I did sudo apt-get update first.  No errors from that.  Everything was Hit, except for some Ign, (means Ignore?) which I've piped to attached Ign.txt

---

### Post by Ozymandias_117 on 2010-03-19
From what all I see the problem is with the sources.list... 

My only idea would be to boot to your live cd, go to software sources, enable the ones you use, but I wouldn't enable backports (at least for now).

Then mount your drive, make a backup of your current /etc/apt/sources.list on your hard drive (somewhere like in your home directory), then copy /etc/apt/sources.list from the running liveCD to /etc/apt on your hard drive. Reboot to your hard drive then try:
```
sudo apt-get update
sudo apt-get install kubuntu-desktop

```

That may fix it. (There may be easier ways to accomplish this... but I don't know of them)

---

### Post by convert_mrta on 2010-03-19
Sounds like a plan.  I'll give it a try!

---

### Post by convert_mrta on 2010-03-20
Tried it out -- no luck.

booted from live CD, copied the default /etc/apt/sources.list to into my production /etc/apt/ directory, and rebooted.

Did sudo apt-get update, then sudo apt-get install korganizer  (Korganizer is the critical Calendar app I need) :  


The following packages have unmet dependencies:
  korganizer: Depends: kaddressbook but it is not going to be installed
              Depends: kdebase-runtime (>= 4:4.2.1) but it is not going to be installed
              Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
              Depends: kdepim-kresources but it is not going to be installed
              Depends: kdepimlibs5 (>= 4:4.2.2) but it is not going to be installed
              Depends: libkdepim4 (= 4:4.2.2-0ubuntu1.1) but it is not going to be installed
              Depends: libkholidays4 (= 4:4.2.2-0ubuntu1.1) but it is not going to be installed
              Depends: libqt4-network (>= 4.5.0~+rc1) but it is not going to be installed
              Depends: libqt4-qt3support (>= 4.5.0~+rc1) but it is not going to be installed
              Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
E: Broken packages

Interesting new tid-bit.  I tried to install Korganizer with **Applications Add/Remove.**  I Get 

"Cannot install 'korganizer'  This application conflicts with other installed software. To install 'korganizer' the conflicting software must be removed first.   Switch to 'synaptic' package manager to resolve this conflict.

So I did.  I took a look at kubuntu-desktop, korganizer and some other K applications.  Highlighting any application , then looking at the Depenencies tab, at the bottom of each, after all of the Depends is:

Conflicts: <application name>
Replaces: <application name>

i.e.

Conflicts: kubuntu-kde4-desktop
Replaces: kubuntu-kde4-desktop

Conflicts korganizer-kde4
Replaces: korganizer-kde4

How, do I eliminate this conflict?

---

### Post by convert_mrta on 2010-04-01
Well it would appear that KDE / K-apps are hopelessly lost.

Guess I'll just wait until 10.04 comes out and do a clean install on my system.  Maybe that will resolve it.

---

### Post by convert_mrta on 2010-04-02
:biggrin:

[COLOR="RoyalBlue"]SOLVED, baby!  Using the detail that apt provides.  Yee-haaaa!

After reading the APT primer article on linux-mag.com, I tried ONE more time.  Got this trying to install korganizer[/COLOR]

Depends:  (>= 4.5.0~+rc1) but it is not going to be installed
E: Broken packages


[COLOR="RoyalBlue"]So I decided to try to install JUST libqt4-svg and got this:[/COLOR]


greg@greg-laptop:~$ sudo apt-get install libqt4-svg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-svg: Depends: libqtcore4 (= 4.5.0-0ubuntu4.3) but 4:4.6.2-0ubuntu1~karmic1~ppa2 is to be installed
              Depends: libqtgui4 (= 4.5.0-0ubuntu4.3) but 4:4.6.2-0ubuntu1~karmic1~ppa2 is to be installed

VERY interesting detail....looks like a library conflict -- the "impossible situation"  So I removed both libqtcore4 and libqtgui4

Then did a apt-get clean
Then removed a lock file that was sitting there in /var/cache/apt/archives

Then I reinstalled libqt4-svg.....it was a success!  No error!

:popcorn:  Cooking with gas now??

apt-get install korganizer    SUCCESS!   And its running and all of my calendar data is there.

Thinking my other K- applications will go back on, too.

---

