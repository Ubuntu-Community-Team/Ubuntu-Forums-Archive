---
title: "Strange ubuntu X11 error while upgrading to 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by honeybl on 2010-10-11
I've tried running the regular package upgrade as well as the alternate cd (i386) upgrade from 10.04 to 10.10. This is the error I keep getting no matter how I try to upgrade: 

Error during commit
'E:Couldn't configure pre-depend x11-common for x11-xkb-utils, probably a dependency cycle.'
Restoring original system state

any ideas?

---

### Post by Erudhalion on 2010-10-11
I have exactly the same problem while upgrading from Kubuntu 10.04.

In my case the computer was accidentally disconnected from the Internet while it was upgrading, but I'm almost certain that it had finished downloading the new packages.

The error comes up at the beginning of the "Installing the new packages" phase.

I'm running an HP Pavilion dv6.

Can anyone help?

---

### Post by gquant on 2010-10-11
Got the same problem on a Dell server.  The message I get is:

Exception during pm.DoInstall():  E:Couldn't configure pre-depend x11-common for x11-xkb-utils, probably a dependency cycle.

.

---

### Post by suebi on 2010-10-11
same here

---

### Post by Erudhalion on 2010-10-11
It seems it is a known bug.

I've found three possible solutions, I'll try them out later, but they seem to have worked for other users. Here they are:

1) From console, remove x11-xkb-utils and all its dependencies, then install xorg.

or

2) Run the following:
         dpkg --force-depends --remove x11-xkb-utils
         dpkg --force-depends --remove x11-common

or

3) Install x11-common.

then upgrade.

I think I'll try 3) out first, then 2), then 1), as I don't particularly fancy removing all the dependencies as well.

---

### Post by Erudhalion on 2010-10-11
Right, i tried the solutions i posted.

1) and 2) don't work.

I tried 3) and it upgraded everything, but on reeboot, something has gone seriously wrong somewhere, because after the login screen everything goes black, no icons, backgroud etc, except for the cursor.

I'm trying to work out what has gone wrong.

Any ideas?

---

### Post by RheaHS on 2010-10-11
3) didn't work here. X-11 was already installed.

---

### Post by suebi on 2010-10-11
option 3) didn't work for me but 2) worked fine

---

### Post by boostaldo on 2010-10-12
I have done ;

"dpkg --force-depends --remove x11-xkb-utils
dpkg --force-depends --remove x11-common"

Then I _only_ have updated  from 10.10 with Synaptic.

The error has disappeared.

---

### Post by yclian on 2010-10-13
It happened to me too. I had to remove x11-common and x11-kb-utils.

Thanks for highlighting this here.

---

### Post by gwitt on 2010-10-30
My solution was the following, and it worked:

1) add the following new software source to your software manager (e.g. Synaptic):
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) maverick main 


2) update your software manager
terminal code#  sudo apt-get update

3) update your installation of x11-common:
terminal code#  sudo apt-get install x11-common


have success

---

