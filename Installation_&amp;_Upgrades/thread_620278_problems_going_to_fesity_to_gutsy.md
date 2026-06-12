---
title: "problems going to fesity to gutsy"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by dueling boot on 2007-11-22
I updated everything in 7.04 and tried to update to 7.10 when I got the following error messages:

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could 
not resolve 'wine.lowvoice.nl'
Failed to fetch 
[http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) 
Could not resolve 'wine.lowvoice.nl'
Failed to fetch 
[http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could 
not resolve 'wine.lowvoice.nl'
Failed to fetch 
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 
404 Not Found
Failed to fetch 
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 
404 Not Found
Failed to fetch 
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 
Not Found
Failed to fetch 
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 
404 Not Found

I'm assuming that it's looking at some config file and the locations of certain remote directories has changed, and therefore the upgrade "chokes". I'm pretty sure that the files are WINE and (maybe?) some proprietory codecs?? WINE confuses me, since I decided I wouldn't be needing it, and removed the program. The codecs I still have (PLEASE don't start with holier-than-thou "why would you EVER use non GPL stuff?", OK? (IF it's codecs, I think those are controlled by AUTOMATIX?)

So, I'm assuming there's something like the old DOS config text file that I need to edit to remove (or at least comment out) the offending lines? RIGHT?

So, what file(s) are they? Do I have to use a text editor? or is there a way in the GUI to just point and click away?

Thanks in advance for any assistance you could provide.

---

### Post by dueling boot on 2007-11-22
OK, followup --- by doing some searches, I was directed to comment out (with a # in front) of the lines concerning wine and mediubuntu in sources.list file -- and I found that file in /etc/apt directory

AND I found the offending lines -- BUT, I can't seem to find a way to edit it out! SIGH!!

when I used the commands that somebody suggested in a terminal:

gksudo gkedit /etc/apt/sources.list

nothing happens -- I just get the same command line with no way to edit

when I right-click on the file in the file manager, it DOES open up, but READ ONLY, with no option to save any changes (putting the # in front of the wine and mediubuntu lines -- ARGH!!

I don't see any option to open in a mode where I can edit out the lines and then save the file. What AM I doing wrong?

---

### Post by rsambuca on 2007-11-22
> **dueling boot said:**
> OK, followup --- by doing some searches, I was directed to comment out (with a # in front) of the lines concerning wine and mediubuntu in sources.list file -- and I found that file in /etc/apt directory

AND I found the offending lines -- BUT, I can't seem to find a way to edit it out! SIGH!!

when I used the commands that somebody suggested in a terminal:

gksudo gkedit /etc/apt/sources.list

nothing happens -- I just get the same command line with no way to edit

when I right-click on the file in the file manager, it DOES open up, but READ ONLY, with no option to save any changes (putting the # in front of the wine and mediubuntu lines -- ARGH!!

I don't see any option to open in a mode where I can edit out the lines and then save the file. What AM I doing wrong?

There is a typo in your command.  Try copy and pasting this into a terminal.```
gksudo gedit /etc/apt/sources.list
```

As an alternative, you can go to "System -> Administration -> Software Sources".  Go to the "Third Party Software" tab and deselect the outside repos.

---

### Post by dueling boot on 2007-11-22
OK -- since this is a dual-booting machine, and I have the ability to view the Linux partition from the XP side of things -- AND can open the sources.list file THERE in a simple text editor (not just VIEW, but open for editing), would it be safe to edit the sources.list file under XP and save it with the offending lines #-ed out?

---

### Post by rsambuca on 2007-11-22
I already gave you two different methods of doing what you want.  One via the command line, and one via a GUI.  Have you tried either of those?

---

### Post by dueling boot on 2007-11-22
hmmmm -- well thanks for pointing out the typo -- ARGH!! (once upon a time, I could edit config.sys and autoexec.bat with the best of 'em -- now, can't even do a single line without a mistake? ARGH!!)

that being said, I like the alternative about using the System --> Admin --> Sources better (hard to screw up point and click, ehh?) -- and I guess it's also better than editing the file under XP (that IS "kosher" to do?)

---

### Post by rsambuca on 2007-11-22
I think you can also edit text files using Windows notepad or wordpad.  There I gave you 4 options!

Good luck!

---

### Post by dueling boot on 2007-11-22
our posts kind of crossed each other -- I'll be trying the GUI method first, to avoid anymore typo possibilities & then try the Feisty-->Gutsy upgrade again -- I'll let you know -- THANX
(I'd wish you a happy Thanksgiving, but you had YOURS about a month ago!  ;^)  )

---

### Post by dueling boot on 2007-11-22
looks promising with the GUI option -- gotten further into the process than before -- it actually finished the download (tho' it unloaded some now-unsupported-by-Canonical-programs -- probably no big deal) and is now supposedly doing the actual installation

I'll give a final status report later today or early tomorrow

---

