---
title: "Trouble installing VMware on Gutsy"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by scrawford on 2007-12-01
Does anyone have a procedure for installing VMware server on Gutsy.

I'm a relative Linux noob.....

I tried following the instructions for a prior version of Ubuntu (not sure which, it's getting late at night here) and got to the point where I used the command: sudo vmware-install.pl from within the directory where this file resided, only to receive a "command not found" error.

??????

Any help would be appreciated.

---

### Post by sethvath on 2007-12-01
It should be sudo ./vmware-install.pl

Do read the howto file for installing vmware

---

### Post by scrawford on 2007-12-01
Thanks sethvath that did the trick.

Where do I find the howto file for installing vmware?

---

### Post by siouzi on 2007-12-01
Just a quick tip. Before you can begin using the vmware you have to configure it (sudo ./vmware-configure.pl) and it will probably need to build things. All that are needed for the building process can be installed with sudo apt-get install build-essential.

---

### Post by sanitycheck on 2007-12-01
There is an easier way now:  VMWare Server is available for Gutsy in the partner repositories as of last night (at least that's when it looked like it appeared).  I checked earlier in the week but I did not see it there under Gutsy.

Just add the partner repository under Adept or edit /etc/apt/sources.list directly.

   *deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner*

If using a stock kernel, you have the option to download and install the correct kernel module as well.

I installed it last night on a fresh Gutsy Server i386 system (converted to KDE) and it worked great.  Note that you have to agree to the VMWare terms by checking a box at the end of the agreement.  You also have to obtain a serial number from VMWare from their website (I already had one).  You do NOT have to run the usual VMWare installation script to get it to work - you just hit the icon and it starts right up.

The only strange thing is Adept continually indicates that vmware-server has an update.  The proposed version is the same, and installing it didn't turn off the notification icon.  I'm not sure what is going on there.  I may post a question if it doesn't go away soon.

---

### Post by flamacue on 2007-12-02
> **sanitycheck said:**
> The only strange thing is Adept continually indicates that vmware-server has an update.  The proposed version is the same, and installing it didn't turn off the notification icon.  I'm not sure what is going on there.  I may post a question if it doesn't go away soon.

I am having the same issue.  I'm running Feisty, and the Update Manager says that there is an update to vmware-server available, both from and to version 1.0.4-1feisty3.  I have tried installing the update a few times, and the installation seems to go fine, but afterwards the notification for the update remains.  

I've been having this issue for at least a few weeks now, so I would be interested to know the answer, too.

(For the record, I do plan to upgrade to Gutsy when I have a chance, just haven't had time yet.  Even so, it sounds like that doesn't solve this issue.)

EDIT:  This bug has been reported [[COLOR="Blue"]_here_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/160683")...though reading through the comments, it turns out that the actual cause is [[COLOR="Blue"]_this bug_[/COLOR]]("https://bugs.edge.launchpad.net/soyuz/+bug/172275").

---

### Post by feld on 2007-12-02
same here on gutsy ^^

---

### Post by flamacue on 2007-12-15
I am no longer having this problem on Feisty.  Perhaps they fixed the bug(s)?

To the OP:  if the issue is resolved for you as well, perhaps you should mark this thread "[SOLVED]".

---

