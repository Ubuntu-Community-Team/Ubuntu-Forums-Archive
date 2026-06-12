---
title: "Ubuntu 9.10 Update Manager + Synaptic problem"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by PTOPedro on 2010-01-04
Hey everyone!

I'm currently having a problem with both Update Manager and Synaptic.

Synaptic won't even remotely open for some reason and I can't seem to update via the Update Manager. It gets the updates but doesn't want to install them. No password asked just the usual brief window of reading package information and that's it. Nothing has been done.

Any thoughts?

---

### Post by PTOPedro on 2010-01-08
Also just as a nice side note. It used to update before and everything, but i can't seem to do it since i changed my permissions. If that helps at all let me know. Please!

---

### Post by kellemes on 2010-01-08
> **PTOPedro said:**
> (..) but i can't seem to do it since i changed my permissions.

What permissions you changed? How?

Anyway, open a terminal-window and try this..
```
sudo apt-get update
```
Any error messages?

---

### Post by PTOPedro on 2010-01-09
an error does appears saying 

```
sudo: must be setuid root
```[IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=QUOTE")[IMG]http://www.babylon.com/favicon.ico[/IMG][IMG]http://www.qtl.co.il/img/copy.png[/IMG][[IMG]http://www.google.com/favicon.ico[/IMG]]("http://www.google.com/search?q=QUOTE")[IMG]http://www.babylon.com/favicon.ico[/IMG]

---

### Post by sarahlizz3 on 2010-01-09
I'm having the same problem.  I have not changed anything on this computer - I just got it today from System76.

When I initally logged into the computer, the update manager popped up with updates.  When I tried to start the updates, it went grey and nothing happened.  Did not ask me for my password or anything.
I am able to run the updates through the terminal.

When I try to open Synaptic, a button on the bottom panel (task bar) pops up saying "Starting Administrative Application" and then it just disappears and nothing opens.  
I am also able to open synaptic through the terminal, without a problem.

I tried to install a new program downloaded off the internet (a .deb package), when I clicked on the download to start the gui does not automatically open - nothing happens at all.

This sounds like a similar problem as PTOPedro is having, but I thought I'd include all of my issues in case that provides more information to someone.  Going through the forums, I found similar issues, but they either were not resolved (from years ago) or the fix didn't work.  I tried:
[http://ubuntuforums.org/showtread.php?t=800157](http://ubuntuforums.org/showtread.php?t=800157)
[http://ubuntuforums.org/showtread.php?t=324424](http://ubuntuforums.org/showtread.php?t=324424)

Any help would be very much appreciated.

---

### Post by PTOPedro on 2010-01-15
bump

---

### Post by Murr on 2010-01-18
Same problem here.. apt-get not working either. Probably not a client bug?

edit : earlier in the day synaptic was working, I was installing a whole lot of stuff and when it stopped working I immediately checked for the update manager.

---

### Post by Murr on 2010-01-18
Synaptic now working partially. Some servers are down I reckon?

---

### Post by Murr on 2010-01-19
everything works today. Problem solved

---

### Post by djparker on 2010-01-19
I installed Ubuntu 9.10 yesterday on my Toshiba Laptop. Everything went fine. I set the network access and told the update manager to look for updates. It found 128 MB worth of files and installed them. This morning when I signed in, I went to update manager and told it to search for updates. I am now getting the following errors: 

W: GPG error: [http://www.bashterritory.com](http://www.bashterritory.com)  Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://pakages.medibuntu.org/dists/karmic/Release.gpg](http://pakages.medibuntu.org/dists/karmic/Release.gpg)  Could not resolve 'pakages.medibuntu.org'

W: Failed to fetch [http://pakages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2](http://pakages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2)  Could not resolve 'pakages.medibuntu.org'

W: Failed to fetch [http://pakages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2](http://pakages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'pakages.medibuntu.org'

W: Failed to fetch [http://www.bashterritory.com/pytube/releases/Packages.bz2](http://www.bashterritory.com/pytube/releases/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.

What gives? Any ideas? Can this be easily fixed or will I have to reinstall 9.10? 

Regards,
djparker

---

### Post by PTOPedro on 2010-01-20
yeah...apparently my permissions are screwed up and i don't know how to fix them....great....i can't install anything from the ubuntu software center, still updates won't update synaptic wont open....help!

---

