---
title: "Feisty - Uhoh..."
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by mpadberg on 2007-06-10
Hi all.  Not precisely how to capture this, but I'll give a quick brief on what I've done.

Had a Dapper server (6.06LTS) that I wanted to upgrade.  Following what I've read in a few places, adjusted etc/apt/sources.list to change all instances of Dapper to Edgy, then apt-get update / apt-get dist-upgrade.  Dapper to Edgy went fine.

Did the same process from Edgy to Feisty (etc/apt/sources.list replacement, then apt-get update / apt-get dist-upgrade).  This also, went good.  completed, rebooted, up she came.

It was then that I noticed vmware had some issues.  I was due to upgrade to vmware 1.03 anyways, so why not now.  Needed a vmware patch, applied it, all good.  Reboot, all's good.  Decided to install the vmware MUI.  Install went fine, but it just won't start.  Research indicated changing the /bin/sh symlink to point to /bin/bash instead of /bin/bash helps - sure enough, the MUI would start (although still not function).  Reboot, and the startup process goes through all components, but doesn't arrive at a login prompt (I'm just using cmd line, no X on this box).  Its gotten past loading all network components, ssh, etc, so I can remotely access it via ssh, although not from the local console.

I've put back the symlink /bin/sh -> dash (as it was previously), but this hasn't made any difference.

How do I begin to diagnose/troubleshoot this one?  Mark a spot in the syslog, reboot, follow whats happening?  Any way to figure out whats going on with the console login?  

Current status: box is running, services are up, box is accessible, vmware is working, ssh, ftp, samba/nfs and other services.  Its workable, but there's still a problem...  

Any assistance is greatly appreciated!

Marlen.

---

### Post by mpadberg on 2007-06-13
I dug further into this.  Looking at /etc/inittab, I'm trying to run the server in runlevel 2 (just command line mode).  Files in /etc/rc2.d indicate S99rclocal and S99webmin.  I can watch everything else during startup - and it all starts fine.  This includes executing rc.local (I know this has executed because I inserted an echo statement in there simply stating "echo This is where rc.local is executing").  Rc.local doesn't execute anything, simply makes the statement.  The other S99 symlink is to start webmin, which is also working.

So where I'm at: the server is up, its running, all installed software is working fine, however at the completion of the startup cycle, it doesn't prompt for login.  I did also check for the nologin (there's an S??rmnologin symlink in /etc/rc2.d to remove the nologin file if it exists).  

What else would prohibit the login prompt from being displayed.  I've ruled out vmware mui and the /bin/sh symlink as being the issue (returned the original symlink for /bin/sh to point to ./dash).

Any ideas?

---

