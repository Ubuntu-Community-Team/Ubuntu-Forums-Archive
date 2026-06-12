---
title: "debconf: unable to initialize frontend: Gnome"
date: 2015-09-08
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2015-09-08
debconf: falling back to frontend: Dialog
debconf: unable to initialize frontend: Gnome
debconf: (Can't locate Gtk2.pm in @INC (you may need to install the Gtk2 module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 91.)

This is the message I suddenly began to get when I used sudo "apt-get update; sudo apt-get upgrade" in a terminal window this morning.  And this occurred again when I tried it later on my 64-bit install of Ubuntu 14.04 (the first attempt was on my 32-bit install of 14.04 on a different partition).

It's sudden, its on two different installs, it involves using apt-get, and it is debconf and Gtk2 related.  How am the heck am I suppose to tell Launchpad all this in filing a bug report?  It wants me to narrow it down to a specific package.  I don't know.  Maybe debconf.  I mean, it's doing all the complaining.  And how am I suppose to know how to install Gtk2?  It's not something that Ubuntu Sodtware Center deals with.  I tried using "sudo apt-get install Gtk2", and apt-get did not know what to make of my request.  I ended up just scrambling my 32-bit install, so I have to start all over with it.

While I'm at it. let me tell you a user's perspective of Lauchpad:  "IT S**KS!!!".  I've got problems on my end too, you know, and this is beyond a user's understanding when it comes to just giving you our perspective of the matter.  I don't know it from your end, and I don't want to take time to master enough of what-I-don't know JUST TO REPORT A D**M PROBLEM!

Alright.  There's a problem.   Now you know as much as I know.  Please handle it.

By the way, apt-get does NOT handle image updates.  Everything else, if there is a PPA registered or an entry in /etc/apt/sources.list.  But  for images, you have to use "sudo /usr/bin/update-manager" to get them (you see this as "Software Updater" in the GUI).

And why do I have to specify "sudo apt-get autoremove" just to delete packages that "sudo apt-get remove" took out of commission?  And what gets rid of old images?  The ones that just keep piling up in Grub2 Advance settings?

---

### Post by MAFoElffen on 2015-09-08
first try
```

sudo apt-get update
[COLOR=#333333][FONT=monospace]sudo apt-get install libgtk2-perl[/FONT][/COLOR]

```
Then do
```

sudo apt-get install -f
sudo apt-get dist-upgrade

```

---

### Post by oldefoxx on 2015-09-09
I believe that did it.  I ran the commands and this is what I saw on the screen:

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  apport apport-gtk dkms gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons
  gvfs-fuse gvfs-libs irqbalance python3-apport python3-problem-report sudo
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Notice that previously apt-get was not upgrading 14 packages, and I never knew why.  I'm not sure what sudo apt-get install -f does, but it suggest a force option, and not having any packages specified suggest any and all upgrades that had not been upgraded for whatever reasons.

Anyway, I did a sudo apt-get update; sudo apt-get upgrade after that, and everything is fine.  I will work with it as-is now for a few days before I change the status to Solved.  But it looks good.

I recognize, from other recent study, that the libGtk2-perl means a library was required.  I thought it was a request for a package named Gtk2.  I don't know how to anticipate one thing or the other.  

Feels good to get a quick, easy, and effective response.  I wonder why it suddenly showed up, for both the 32- and 64-bit versions.  I've seen several failures to upgrade reported by apt-get for a good while, but it never said which ones or why they didn't make the cut, so I didn't know anything to do about it.  Software Updater didn't do anything about it either.

Your help in this matter is much appreciated.  Way faster than doing a bug report.  More available to others as well, because here it can be searched for.  I tried that, but found no matches, so started my own thread.

Oops!  I got it wrong.  It was sudo apt-get dist-upgrade that got the good results.  I did a man apt-get, and found -f does a fix-broken packages.  I would never have thought of tying that to install though.  The man pages are sort of weak on working examples, so must be lots of trial and error to get it right.

---

### Post by MAFoElffen on 2015-09-09
You're welcome...

> **oldefoxx said:**
> I believe that did it.
The package I had you install was the dependent package that was missing. Your machine was affected by a known bug and that was a work-around. Unfortunately, with that bug, just doing a dist-upgrade would not have resolved that problem for that current bug and it had to be added manually.

You previously used
```

sudo apt-get update

```
which updates packages, but goes by the rule of
> 
...Under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed.

Whereas 
```

sudo apt-get dist-upgrade

```
...Has a little more intelligent, smart kind of conflict resolution system that it tries to use to resolve conflicts with new package dependencies. It will remove an older package (or packages, if it needs to, to resolve a dependency conflict. So the dist-upgrade resolved the new package dependencies removing a conflicting package  that was preventing the first upgrade to proceed... (Personally, I always use the dist-upgrade option.) So basically, it then looked at the installed and packages that it might need to add and rewired those dependencies.

Please use the "Thread Tools" link at the top right, at the start of this thread, to mark this thread as "SOLVED". 

Also, if you would, please help the community by subscribing to the launchpad bug #1389582, so that they can figure out which combination of packages causes this bug:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1389582](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1389582)

---

