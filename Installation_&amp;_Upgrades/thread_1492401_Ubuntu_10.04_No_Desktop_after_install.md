---
title: "Ubuntu 10.04: No Desktop after install?"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by jacobstevens on 2010-05-24
Hi, I saw other "no desktop" threads but they seemed to be a different issue.

I've successfully installed a fresh instance of Lucid Lynx, but when I boot it up, it looks like all I get is a terminal, no desktop environment at all.  

I'm new to Ubuntu, but the Gnome package 10.04 looked beautiful and I'm happy to keep that, if I can just get it to load.

Might be relevant: I had install problems using the ISO (Errno 5) so I tried the alternate text-only intaller.  This errored when attempting to install software, no reason given, so I skipped over it.  Finally got a successful install, happy there, but as I said, I'm new, and I'd like to try Gnome before KDE or others -- one step at a time :)  

Anyway, what command to install the desktop?

---

### Post by darkod on 2010-05-24
From the top of my head, it was as simple as:

sudo apt-get install ubuntu-desktop

but I might be wrong. :)

---

### Post by jacobstevens on 2010-05-24
> **darkod said:**
> From the top of my head, it was as simple as:

sudo apt-get install ubuntu-desktop

but I might be wrong. :)
Thanks -- I expected it would be simple!

That command appeared to unpack some things, then I was asked for my installer disc.  So I did, and then: 

"Failed to fetch cdrom:" for lots and lots of files, not being found.

"E: Unable to fetch some archives, maybe just run apt-get update or try with --fix-missing?"  And I've tried both, and it quickly appears successful.  What next?

---

### Post by darkod on 2010-05-24
> **jacobstevens said:**
> Thanks -- I expected it would be simple!

That command appeared to unpack some things, then I was asked for my installer disc.  So I did, and then: 

"Failed to fetch cdrom:" for lots and lots of files, not being found.

"E: Unable to fetch some archives, maybe just run apt-get update or try with --fix-missing?"  And I've tried both, and it quickly appears successful.  What next?

Hmmm... I don't know. :)

Reboot or if still in command mode, try:

startx

or:

sudo startx

I have never installed in text mode, I have no clue. :)

---

### Post by jacobstevens on 2010-05-24
> **darkod said:**
> Hmmm... I don't know. :)

Reboot or if still in command mode, try:

startx

or:

sudo startx

I have never installed in text mode, I have no clue. :)
Hmm, you got me thinking, now....

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

My impression was this was a non-graphical installer that ultimately installed the same thing as here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Perhaps that's not the case!  I may have to go back to troubleshooting errno_5:

"The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment."

I've burned 4 discs, at lowest possible speed.  It's a lenovo 3000 N100, has been treated nicely, and I'm in a server room, I don't think I can get any cooler.  Win7 installed OK and I can certainly run Lucid well enough from the disc so I don't think it's a lens cleaning issue.  

Should I try to put the desktop on top of this text-only instance of Lucid (if it indeed is only text based) or go back to trying to install the "normal" version and troubleshooting errno_5?

---

### Post by darkod on 2010-05-24
I thought you already knew that and wanted to try to add the desktop package manually.
Yes, the alternate installer should install basically the same system, only the actual installer is text based. Because of the error during install you are missing packages.

---

### Post by darkod on 2010-05-24
Can it be that it's working fine in live mode, but has issues copying some packages? Maybe ISO corrupted during download?
Burning 4 CDs won't help in that case. Just guessing here...

---

### Post by jacobstevens on 2010-05-24
> **darkod said:**
> Can it be that it's working fine in live mode, but has issues copying some packages? Maybe ISO corrupted during download?
Burning 4 CDs won't help in that case. Just guessing here...
You know, I thought I had downloaded a couple instances of the ISO, but now that I look again, I had first downloaded the 32-bit version, and then the 64-bit version, which must have only been downloaded once.  So I'm downloading it again, thanks for your thorough thoughtfulness.  We'll see if that works.

---

### Post by jacobstevens on 2010-05-26
Well, on a different system, I downloaded the ISO again, and got the same issue.  If the issue is truly caused by anything listed in Errno_5, it sure seems sensitive, but anyway, I tried installing 10.04 server, which worked, and then installed the desktop on top of that, which also worked.  

So now I've worked around the issue, although the issue doesn't seem to be resolved, it still seems like a legitimate issue, possibly a bug in 10.04, possibly a driver or hardware compat issue, but I don't have the means to investigate it.  Anyway, thanks for your help!

---

