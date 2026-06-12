---
title: "Focal Fossa updates - unattended upgrades dialog - nothing happens"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by dessertlizard on 2020-09-18
Hi!

I've recently installed Ubuntu 20.04. The auto updates have been popping up for some time now but considering I'm in no way an expert on Linux and also considering the risk that sometimes the updates break something that's previously working fine I had been delaying applying them for some time.

However I decided to go for the install a couple minutes ago.

During the process I got a dialog about something called "unattended updates". With several options tho choose from.

>Keep the package maintaner version
>Keep local version
>Show differences side by side

And a few more.

I chose to show the differences side by side. However nothing more happened and the updates ran normally.

I've since checked the /var/history.log and apparently now I've got a bunch of "symlinks" and a couple of renamed newer files scattered around.

What the hell just happened to my system? Can someone shed some light into it? I've since Googled for an answer but the few that appear are more related to Debian Linux and aren't of much help.

I'm not very keen of having a system randomly modified when I explicitely chose for the program to show me the differences, hoping that i would then be able to chose if I wanted to apply the update or not.

I'm so not happy that I'm considering a format and a new clean install just for the sake of keeping my computer clean as it were.

Thanks in advance for any input about the subject.

---

### Post by Impavidus on 2020-09-19
Some time ago on 20.04 I had something similar. The updater had me choose between the maintainer version or the local version of some config file (I think it was unattended-upgrades), although I knew I hadn't changed the config file since installation and I hadn't upgraded from a previous release of Ubuntu. Must have been a glitch.

I always look at the list of packages that will be upgraded, but as long as the package manager doesn't report any problems (like partial upgrades), I just install all upgrades. Only once did that lead to trouble in the 14 years I've been using Ubuntu.

---

### Post by kurt18947 on 2020-09-19
unattended-upgrades has been okay for me in 20.04. It was a pain in 18.04 on one install though. Anytime I wanted to do a manual check for new software I got a message "waiting unattended-upgrades to exit" or words to that effect. It'd take 1.5 minutes or more for unattended-upgrades to complete. I uninstalled it, do a manual check at least once a week on my 18.04 install.

---

### Post by deadflowr on 2020-09-19
What symlinks?
Can you give an example.

What renamed new files did it produce?

And /var/history.log is non-existent,
did you mean /var/log/apt/history.log?

---

### Post by dessertlizard on 2020-09-19
> **deadflowr said:**
> What symlinks?
Can you give an example.

What renamed new files did it produce?

And /var/history.log is non-existent,
did you mean /var/log/apt/history.log?

Some I was able to read on the update window before disappearing had something to do with the boot folder/files.

Yes, I meaned the /var/log folder but the log there present doen't contain all the information that was displayed during the autoupdate.

Some of the renamed files as I said, are on /boot. For instance:

>System.map-5.4.0-47-generic was renamed/replaced by config-5.4.0-47-generic
>vmlinuz vmlinuz-5.4.0-47-generic was renamed/replaced by vmlinuz-5.4.0-26-generic - no error here, it was apparently downgraded
>vmlinuz.old was created

And going by what I was able to view on the update window, it happened it a couple more files through the whole system.

If this is the way Ubuntu does its updates, I'm not keen on doing them. It just litters the whole system.

---

### Post by webaake on 2020-09-19
Take control. Disable unattended upgrades. Here's how: [https://linuxconfig.org/disable-automatic-updates-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/disable-automatic-updates-on-ubuntu-20-04-focal-fossa-linux)

Someday it WILL wreck your system.

---

### Post by dessertlizard on 2020-09-19
> **webaake said:**
> Take control. Disable unattended upgrades. Here's how: [https://linuxconfig.org/disable-automatic-updates-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/disable-automatic-updates-on-ubuntu-20-04-focal-fossa-linux)

Someday it WILL wreck your system.

The autoupdates are already disabled. However when manually run that doesn't seem to prevent some sub-updates, the so called "*unattented upgrades*". Which, even though have a dialog asking the user what to do about them, apparently end up doing something completely different. At least in my case, since I chose to display the differences and it ended up doing some kind of upgrade/downgrade without being told to do so.

And apparenty not many people know why also.

---

### Post by ajgreeny on 2020-09-19
Maybe not something I would recommend to all but unattended-upgrades package is something that can easily be removed from your system with no problems arising from so doing, provided, of course, that you update the system manually very regularly.

I always remove that package and use two aliases to update and upgrade manually, probably every day.
Add these two lines to your hidden .bashrc file in your home and you can do all that's required simply by typing ***ud*** and ***ug***.
```
alias ud='sudo apt update && apt list --upgradable'
alias ug='sudo apt full-upgrade'
```

---

### Post by grahammechanical on 2020-09-19
Load Software & Updates. Go to the Updates tab. What setting do you have for Automatically Check for Updates? Change it to Never. Now look at When there are security updates. We cannot set that to Never but we can change it to Display immediately instead of Display & install automatically. As for When there are other Updates, set that to Display every fortnight. You might then get a bit of peace.

Ubuntu developers are trying to protect us from our own laziness. An infected machine on any network is a danger to all machines on the network. The Internet is a network, after all. Linux developers are quick at fixing security vulnerabilities when they become known. We would be foolish not to benefit from that kind of insurance. We might as well go back to using Windows XP.

Regards

---

### Post by Impavidus on 2020-09-20
Since then I removed unattended-upgrades. I set the system to check for updates daily. This only checks for updates, doesn't install them. And I set it to inform me of all updates immediately, but not install them automatically. Works flawlessly.

---

