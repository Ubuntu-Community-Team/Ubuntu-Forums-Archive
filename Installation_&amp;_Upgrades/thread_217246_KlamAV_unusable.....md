---
title: "KlamAV unusable...."
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by kenweill on 2006-07-16
I installed KlamAV from Synaptic but it seems that its unusable.
I cant scan. I cant update. 

Is this a dependency problem?

When i try to scan, a "Database Initialization error" comes.
When I update, "Config file error occurs" comes.

What else should I install to make this work? 
I thought all things should work if i install via Synaptic...

---

### Post by orb9220 on 2006-07-16
Why are you bothering with antivirus programs? They are not needed.

Quotes from other threads:

"Why are you running an antivirus program on Linux? Unless you are running a mail server that relays mail to Windows machines, it is totally unneeded. (And then it is only needed to protect the Windows boxes.)"

"have done a search on this forum regarding anti virus and firewall/ spyware software, and most people say:

Anti virus = not needed
Firewall = not sure on this one
Spyware = not needed"

"You don't have to worry about an anti-virus program (at least not yet), but like others have said - a firewall is recommended."

This may apply to you 

"Some might say that you should install antivirus software in case you are sent an email containing a virus designed for a windows PC, it wouldn't infect your machine. But if you were to forward that email (possibly to a windows PC), it will be caught. And you will have the satisfaction knowing that you have done your bit to help prevent the spread of infection."

but if you don't have xp then I wouldn't worry about.

But if you just do a forum search you will see posts about problems with KlamAv if you still want antivirius

Sorry I couldn't be more help.

---

### Post by kenweill on 2006-07-16
I have windows xp. I want to prevent the spread of infection.

KlamAV is included in Synaptic, it should work. Or, is it just added in the repository without being tested to work?

Viruses in linux are rare. Rare doesnt mean nothing. Its just rare. Only a few. What if i get infected with one of those few viruses in linux? I want to be protected by those rare viruses in linux.

---

### Post by T700 on 2006-07-16
> **kenweill said:**
> I have windows xp. I want to prevent the spread of infection.

KlamAV is included in Synaptic, it should work. Or, is it just added in the repository without being tested to work?

Viruses in linux are rare. Rare doesnt mean nothing. Its just rare. Only a few. What if i get infected with one of those few viruses in linux? I want to be protected by those rare viruses in linux.

The current version of clam works quite nicely.  That said, I'll echo the earlier sentiment--it simply is not needed for the desktop.  The only time I will run it on Linux is if the machine is a mailserver.  In that case, it is useful to strip out viruses from email before relaying them to a Windows box.

Regarding those rare Linux viruses, they really don't do anything in the wild.  Unless you run 24/7 in root or have the habit of unquestioningly offering up root access to strange programs, there is really nothing to worry about.  If it makes you sleep better to run an anti-virus, go ahead, but the lack of that kind of nonsense is one of the true pleasures I found in the Linux world.

Paul

---

### Post by DigitalDuality on 2006-09-15
What's wrong with people wanting extra security?  I don't see why you would be arrogant like a bunch of mac users and pretend to be invincible.

---

### Post by jonrkc on 2007-02-22
> **DigitalDuality said:**
> What's wrong with people wanting extra security?  I don't see why you would be arrogant like a bunch of mac users and pretend to be invincible.

Amen!  Linux is not invincible, it has been targeted, it is being targeted more all the time, and there is nothing wrong with wanting all the security you can have.  

Klamav worked for me last night (freshly downloaded from the repositories).  It would not work today; it did not retain my settings from yesterday; could not update itself; could not upgrade, etc.

I guess I'll go back to BitDefender Console, which works without any problems, if I can find where to get it again.  Had to uninstall it, unfortunately, in order to use apparently worthless Klamav.  Tried GTK frontend also, and apart from being put off by its ugly appearance and misspellings, it wouldn't cooperate either.  So...

Not spending all my life trying to get things to work from the repositories when they're out of date (as Klamav reported itself and Clamav both to be) and dicey in operation.

---

### Post by julian67 on 2007-04-01
It's not just useful for mailservers. Anyone using Linux who might connect to Windows users' usb drives (external hdd, flash drive, camera memory cards, personal music player etc etc etc) or who connects their own USB devices to different PCs and who doesn't wish to *host* Win malware that will then be passed onto the next connected device can benefit from using an AV tool. Of course the Win malware won't impact on your non-MS system but it's not nice to be spreading problems to people who *will* be affected. I don't run AV routinely but if I've had to connect my usb flash drive to a public or untrusted PC I'll scan it either with klamav or from bootable read only media. There's no shortage of nasty stuff that instantly writes itself to any Win filesystem it can find.

edit: I was using KlamAV on openSuse with no problems but haven't been able to get it working on Ubuntu Edgy, same problem as OP. But I've tried f-prot and this works very well if you don't need GUI. Unfortunately while it's no-cost for home users with Linux it isn't Free.

---

