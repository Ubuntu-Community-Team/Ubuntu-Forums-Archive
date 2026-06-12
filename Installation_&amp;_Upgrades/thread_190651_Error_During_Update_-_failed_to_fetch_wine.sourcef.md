---
title: "Error During Update - failed to fetch wine.sourceforge.net..."
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by jeff-- on 2006-06-06
When trying to update to Dapper, using the gksudo "update-manager" command, I get the following:

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.sourceforge.net/apt/binary/Packages.gz](http://wine.sourceforge.net/apt/binary/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://wine.sourceforge.net/apt/binary/Packages.gz](http://wine.sourceforge.net/apt/binary/Packages.gz) Sub-process gzip returned an error code (1)

That is the exact error I got during my upgrade to 6.06.  I was wondering if there's anything I can do to fix this.  I currently run Breezy, and my specs are:

Pentium 4 2.4 ghz
nvidia TI 4200
512mb ram
15" lcd monitor

Though I don't know that any of that matters.  Obviously wine is a problem but I don't know what to do to fix this error.  Any help is appreciated :)

---

### Post by philipgm on 2006-06-06
I often get errors upgrading wine packages but these are all due to the server being slow. In the past I have had to run the update manager several times to get a new wine release to install, simply because it times out on the server. 

I suspect that that is your problem, and you may have to upgrade everything else and then re-run the update manager until it works.

HTH

Phil

---

### Post by jeff-- on 2006-06-06
I've done a sudo apt-get update like 5 times and I saw that same "failed to fetch wine.sourceforge" thing in it every time.  And then I tried the update manager again to upgrade and I got the same error.

Should I just get rid of wine?  I actually don't currently use it for anything so I won't be at any loss.

---

### Post by philipgm on 2006-06-06
If you're not using it yes, get rid of it. You can always install it later, possibly when the servers are less busy. My experience has been that wine updates are most difficult when the update is first released so do the upgrade and then go for a wine install later.

Regards

Phil

---

### Post by jeff-- on 2006-06-06
Well I did a sudo apt-get remove wine, it said it was removed, and I am getting the same error as I was in my first post.  Any suggestions?

---

### Post by InsaneSith on 2006-06-06
[QUOTE=jeff--]Well I did a sudo apt-get remove wine, it said it was removed, and I am getting the same error as I was in my first post.  Any suggestions?[/QUOTE]
Did you try seeing if it was removed from your sources list?

---

### Post by jeff-- on 2006-06-06
That was indeed the problem, got it working :)

---

### Post by YokoZar on 2006-06-07
The sourceforge repository is obsolete, out of date, and frequently broken like this.

There's a new repo, instructions here:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

