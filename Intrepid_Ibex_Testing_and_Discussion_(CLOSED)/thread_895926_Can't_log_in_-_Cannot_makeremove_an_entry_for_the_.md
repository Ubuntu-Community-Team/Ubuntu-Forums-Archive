---
title: "Can't log in - Cannot make/remove an entry for the specified session"
date: 2008-08-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by readams on 2008-08-20
Attempting to log in through gdm pops up a message "Authentication Failed"

Logging in from console prints a message "Cannot make/remove an entry for the specified session"

Looking in auth.log I see something like:
login[pid]: Cannot make/remove an entry for the specified session
gdm[pid]: pam_nologin(gdm:auth): cannot determine username

I even get this error if I use recovery mode and try to use su to switch to another user!

Any suggestions?

---

### Post by gmclachl on 2008-08-20
It sounds as if you have been hit by this
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/259867](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/259867)

---

### Post by gmclachl on 2008-08-20
If the updates haven't hit your mirror you can pick them up from here.

[https://edge.launchpad.net/ubuntu/intrepid/+source/pam/1.0.1-3ubuntu2](https://edge.launchpad.net/ubuntu/intrepid/+source/pam/1.0.1-3ubuntu2)

---

### Post by douham on 2008-08-20
I to have been hit by this. Installed updates at about 2100 UTC. Has anyone any suggestions

---

### Post by danbuter on 2008-08-20
> **douham said:**
> I to have been hit by this. Installed updates at about 2100 UTC. Has anyone any suggestions

You may want to try an older kernel.

---

### Post by phidia on 2008-08-20
Yeah count me in on this too-I guess I will try using the previous kernel when I get time and report back.

Added: No I tried two previous kernels and the only change was to drop the boot to initramfs.
Could try the chroot but that will be another day.

---

### Post by plun on 2008-08-20
Maybe a chroot is needed according to [B][U]bug report in message 2
[/U][/B]
Manual from Hardys development

[http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)


hardy > intrepid

---

### Post by phidia on 2008-08-20
From the bug report it looks like this could be the solution:
> 
To recover, you have 2 options..

1: Recovery console
2: Chroot from the liveCD (see above)

After that, it should be the normal update/upgrade process.


According to the report the pam package was the problem and has been upgraded.

---

### Post by scradock on 2008-08-20
confirming that:

1) changing kernel does NOT help;

2) use a recovery log-in (as root) and edit /etc/pam.d/common-session to remove the line ```
session requisite          pam_deny.so
```

and replace it by ```
session required          pam_permit.so
```

The "sed" file provided in the Launchpad bug report didn't get it quite right for me, but a little careful editing to line up non-comment lines in common-session seemed to help.

Then you can log in again and upgrade libpam-modules and libpam-runtime to the 1.0.3 versions.

---

### Post by phidia on 2008-08-20
Yeah scradock, I could not use recovery mode either. I chrooted from my gutsy install-did "sudo apt-get update && sudo apt-get upgrade" and I'm back in intrepid.

---

### Post by scradock on 2008-08-20
that's good!

---

### Post by ccw on 2008-08-20
> **phidia said:**
> From the bug report it looks like this could be the solution:

According to the report the pam package was the problem and has been upgraded.

Yes it was the 1.0.1-3ubuntu1 pam packages. Upgrading them to 1.0.1-3ubuntu2 in a chroot environment will get everything back into a working state.


Quite honestly: 2 skills needed to run a development ubuntu/debian machine:

1) the ability to evaluate what apt-get wants to remove or install during a dist-upgrade
2) the ability to recover via a live CD/rescue boot and chroot.

---

### Post by scradock on 2008-08-21
I used the third "essential skill" - the ability to edit a config file from another install or LiveCD environment.

The essence of the workaround that got me back up (so that I could do the upgrade to the fixed libpam packages) was to remove the line ```
session requisite      pam_deny.so
``` from the common-session file in /etc/pam.d

After the upgrade, I tried replacing that line, which is presumably there for a reason, but got the Authentification failed error in gdm once again.

I'm not sure that the problem is really fixed - could someone who didn't do any hand-editing of the common-session file post a copy I could try, to see if it works here?

Thanks in advance...

---

