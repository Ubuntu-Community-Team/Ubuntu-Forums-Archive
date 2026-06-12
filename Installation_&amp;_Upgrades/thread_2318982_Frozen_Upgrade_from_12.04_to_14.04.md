---
title: "Frozen Upgrade from 12.04 to 14.04"
date: 2016-03-31
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2016-03-31
Hi all,

I started the upgrade process from 12.04 to 14.04, but it appears that the upgrade has frozen at "Setting up apport-gtk (2.14.1-0ubuntu3.19) ..."  What can I do from here?  Will I lose any data?

---

### Post by Shadius on 2016-03-31
Ubuntu.  I can't use another distro.  I have stuff on this computer.

---

### Post by Bucky Ball on 2016-03-31
Did you leave it to do its thing? You realise that, depending on your connection speed, upgrading via the net can take at least two hours.

If it hasn't been at least that long, leave it for awhile longer. It can look as if nothing is happening but stopping an upgrade part way through can, and often does, leave you with a very broken system.

---

### Post by Shadius on 2016-03-31
Yes, I've left it to do its thing.  It's been a few hours.  Over 4.  The system is unresponsive, no mouse or keyboard inputs are being accepted.  What can I do?

---

### Post by Bucky Ball on 2016-03-31
You are doing this with an ethernet cable? Not advised to use wireless for upgrades. If you are, are you positive the wireless is still connected?

If you can, leave it doing its thing, but plug in an ethernet cable and see if it budges or shows signs of life. That might still take a little time to know.

---

### Post by Shadius on 2016-03-31
I started the upgrade since 11:17 PM yesterday night and nothing has changed.  The time hasn't even changed on the screen.  I will try the Ethernet connection.

---

### Post by Shadius on 2016-03-31
I just plugged in the Ethernet cable, but still no change.  No signs of anything on screen.  No mouse or keyboard response.  It seems to have gotten stuck at "Installed apport".

---

### Post by Bucky Ball on 2016-03-31
Well, when you posted you said the upgrade was stuck at 'Setting up apport'. Your last post says you are stuck at 'Installed apport'. That would signify something has happened. :-k

---

### Post by Impavidus on 2016-03-31
You could just stop it, get a completely broken system and do a fresh install. It's either that or wait and hope the upgrade finishes. I assume you have backups of your important files, don't you?

---

### Post by Shadius on 2016-03-31
I forgot to backup one folder.  Would I be able to retrieve that folder?

---

### Post by Bucky Ball on 2016-03-31
Yep. Boot from Ubuntu install media and 'Try Ubuntu'. When you get to the desktop, open a file manager and find the folder then drop it to a safe place.

You could stop the upgrade, reboot and see what you get. You might have a bootable system, just a confused one. Maybe sensible enough for you to back stuff up before taking further action without needing to boot from install media, though, if you're lucky.

---

### Post by Shadius on 2016-03-31
Will try that. Thanks Bucky Ball.

---

### Post by Shadius on 2016-03-31
Well, upon doing a restart, it seems that the CPU overheated according to the BIOS.  Nothing seems to be broken.  I will spend my time backing up everything now.

---

### Post by Bucky Ball on 2016-03-31
That's kinda bad and kinda good ...

---

### Post by Shadius on 2016-03-31
> **Bucky Ball said:**
> That's kinda bad and kinda good ...

Can you explain?  I know that the CPU overheating is bad.  How can I stop it from overheating?  Maybe the thermal paste needs to be replaced.

---

### Post by holycow131415 on 2016-03-31
> **Shadius said:**
> Can you explain?  I know that the CPU overheating is bad.  How can I stop it from overheating?  Maybe the thermal paste needs to be replaced.

You may just need to clean out your fans in your tower.

---

### Post by Shadius on 2016-04-01
Will try that.  Haven't had a good cleaning in a while.

---

### Post by Shadius on 2016-04-01
So while it seems that the upgrade went through, I don't think it completely upgraded.  Some things like the System Settings aren't loading.  So how do I go about fixing it?  I tried running the update manager, but it says that I am up to date.

---

### Post by Bucky Ball on 2016-04-01
Try opening a terminal and:
> 
sudo apt-get update
sudo apt-get dist-upgrade

See if that does anything. You might also try:

> sudo apt-get autoremove

That may get rid of anything left over from the dodgy upgrade. What do you get when you give this command:

> uname -a

?

---

### Post by Shadius on 2016-04-01
Here's the output of uname -a:

shadius@shadius-phantom:~$ uname -a
Linux shadius-phantom 3.13.0-83-generic #127-Ubuntu SMP Fri Mar 11 00:25:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
shadius@shadius-phantom:~$

---

### Post by Bucky Ball on 2016-04-01
okay. Run these again:

> sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

Then give us 'uname -a' again and:

> lsb_release -a

---

### Post by Shadius on 2016-04-01
> **Bucky Ball said:**
> okay. Run these again:



Then give us 'uname -a' again and:

shadius@shadius-phantom:~$ uname -a
Linux shadius-phantom 3.13.0-83-generic #127-Ubuntu SMP Fri Mar 11 00:25:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
shadius@shadius-phantom:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty
shadius@shadius-phantom:~$

---

### Post by Bucky Ball on 2016-04-01
Yep. Well, for all intents and purposes, looks like it worked. You are on 14.04 LTS. If things are working as they should, I guess this is solved. If not, probably best to post a new thread with any other support questions to increase your chances of support (rather than post 3+ pages deep here on a thread with an unrelated thread title). 

Let us know.

---

