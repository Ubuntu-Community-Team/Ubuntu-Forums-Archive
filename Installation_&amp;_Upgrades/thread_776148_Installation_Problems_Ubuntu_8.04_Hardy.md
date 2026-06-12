---
title: "Installation Problems Ubuntu 8.04 Hardy"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by slowtrain on 2008-04-30
I have a few questions about upgrading from 7.10 to 8.04 LTS that I suspect others may be wondering about as well.  When I hit the 'upgrade' button in update manager, I get the "not all updates can be installed" message.  Looking down the list of updates, I see a lot of software, like firefox, that have a not-checked and not-checkable checkbox.  I understand that in 8.04 beta, some software was held back and this was normal.  But, is this normal for a new distribution release?  Or, could I be seriously messing up my software installation by doing a partial install?  

To what extent might the problem be due to my having installed some non-standard packages via automatix or directly w/ apt-get (I installed Skypes directly)?  Should I comment out the automatix repositories in my sources.list?  

Would I be better off installing from the 8.04 ISO?  Is this faster on a slower broadband connection?  Would it not mess with my current preferences and non-standard packages?  Is there an advantage to using sudo aptitude dist-upgrade?

If it seems better to stay in 7.10 for the time being, how do I get my software update to stop bugging me about installing the 8.04 packages?  Even after a reboot, update still insists that I install all these packages.

Anyone know whether Skypes and JGR function in the 8.04 distribution?

Any comments or thoughts would be very helpful.  Thanks in advance!

---

### Post by slowtrain on 2008-04-30
Ok, I'm going to log my update experience.  I tried out the 8.04 ISO CD.  Thought I could start up from the CD and run some of the applications I was concerned about working in 8.04.  Unfortunately, this software requires other libraries that it can't find when I'm running the CD, so I couldn't test the software.

I also had hoped the CD would have an option to install on top of my current system, but it doesn't.  I might eventually decide a clean install is the way to go, but for now I'd like to see if I could preserve all my preferences and additional software installations.

Have started up the 'partial update' to 8.04 using the update manager.  Looks like the server is being heavily used.  Am guessing it will take 6-9 hours to download the updates.  Then I have to hope that I'm not actually messing up my computer.

---

### Post by slowtrain on 2008-04-30
Given how long it'll take to upload the updates and how late it is here, I wonder if I can turn off my machine and start where I left off tomorrow?  Or will it start loading the updates from the beginning?

---

### Post by slowtrain on 2008-05-01
The update manager did start from where it left off after I canceled and turned off the machine yesterday.  I wonder what it does with files that it has only partially downloaded--hopefully it detects this and replaces the file or finishes downloading it.  Should be able to start the partial install in an hour or so.  The server seems to be much freer in the morning than in the evening or at night.  Download is proceeding much faster.

---

### Post by slowtrain on 2008-05-01
Okey, Hardy installed after about 1.5 hours.  Some quirks:  When I first started the system, I got a series of error messages saying five parts of my system had crashed, including my investment applet and nautilus.  Strangely, though, none of these appeared to have been crashed.  On reboot, I did not get these crash messages.  The firefox launcher icon has been replaced with a mostly dark square.

Beyond that, however, the new system is well worth the installation time.  I've noticed some big improvements over 7.10.  These include:

*The processor seems to be working a lot less. Possibly due to the dynticks enhancement.

*I can finally hibernate or suspend my desktop.  A lot less electricity and guilt than leaving on my computer 16 hours a day!

*Still a bit flaky on utilizing my Plantronics DSP 400 headset, but at least some of the time when I reset all the Sound preferences to use the USB audio and restart an application, the application switches to the headset.  In the past, the headset was either working right after boot or wouldn't work at all--and didn't work at all at least half the time.  Also, there was no way to switch.

My non-standard software packages, particularly Skype, JGR, and jedit, all seem to be working fine.

The interface looks much snazzier.  Am hoping the Nautilus will solve some of the flakiness of the old.

One concern:  the new firefox doesn't have del.icio.us or Zotero.  I understand Zotero is not far from a build that works w/ firefox.  Strange that I have firefox installed because it was one of the packages that was grayed out when I looked.

Overall, this is great and worth the effort.

---

### Post by slowtrain on 2008-05-06
Overall, I'm still happy w/ 8.04, but there is some flakiness.  One is that Gmail on a web browser now takes up all my processing power and some pages within gmail won't open.  I've switched to Thunderbird as a front end for Gmail for now.

8.04 also has a tendency to think that there are errors where there aren't any.  I get an error msg that it wasn't able to hibernate--after i bring it out of hibernation.  It tells me programs have crashed that haven't crashed.

---

### Post by slowtrain on 2008-05-06
A couple other flakiness items:  The use of system memory is a bit odd.  For example, right now I have 583MB of RAM and 786MB of swap space being used for memory.  Given I have 1GB RAM, I'm surprised the system isn't using more of that.  Opening new documents or switching applications seems quite sluggish.  The system doesn't seem to switch over to much faster RAM when it gets a chance.  I wonder if this has anything to do w/ the hibernate function.

Google calendar won't take new entries.  Probably a Firefox 3.0 issue.

---

