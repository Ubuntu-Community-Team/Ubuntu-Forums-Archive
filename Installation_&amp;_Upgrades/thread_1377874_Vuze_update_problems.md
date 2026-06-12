---
title: "Vuze update problems"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by Bill D on 2010-01-10
I've been trying to update Vuze to the latest version 4.3 on Karmic. I've tried the .deb install to no avail. I have the .tar.bz2 package downloaded but I have yet to find any instructions that break down the install process into steps that can be understood and followed by a new user like myself. Thanks in advance for any help you can provide!

---

### Post by Enigmapond on 2010-01-10
Search the forum before making a request..90% of what you need is already out..:) Cheers

[http://ubuntuforums.org/showthread.php?t=530017](http://ubuntuforums.org/showthread.php?t=530017)

---

### Post by Bill D on 2010-01-10
I tried searching the forums before posting. The .deb file from getdeb installed the version that I already had and am trying to upgrade. Compiling the tarball did the same thing. I removed the previous version before trying to install the updates.

---

### Post by Kanna2412 on 2010-04-15
Hi Guys,

I love Vuze. I installed Vuze on Ubuntu 9.10 from repositories. When I opened it, it was asking me to upgrade. I clicked on the upgrade button, it went to Vuze website. Again I downloaded Vuze software and installed manually. Again I encountered the same problem.

My friend installed Vuze for windows XP on his laptop. The version has more features than I got and it is not asking for upgrade.

Please help me fix this.


Indian.

---

### Post by rifter on 2010-04-21
> **Enigmapond said:**
> Search the forum before making a request..90% of what you need is already out..:) Cheers

[http://ubuntuforums.org/showthread.php?t=530017](http://ubuntuforums.org/showthread.php?t=530017)

That thread has nothing to do with Vuze or how to update it.  Read posts before replying ;).

---

### Post by rifter on 2010-04-22
> **Bill D said:**
> I tried searching the forums before posting. The .deb file from getdeb installed the version that I already had and am trying to upgrade. Compiling the tarball did the same thing. I removed the previous version before trying to install the updates.

I had the same thing happen.  I tried adding the getdeb repos and indeed it did make vuze show up in synaptic as having an upgrade available.  I upgraded, according to synaptic, from vuze 4.2.0.8-3ubuntu1 to vuze_4.3.0.4-1~getdeb1_all but when I started Vuze the about box still says 4.2.0.8.

I will do some more research and see if I can find an answer.

---

### Post by rifter on 2010-04-22
I finally got Vuze fixed thanks to _[color=blue][this howto](forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)[/color]_.  The procedure there also fixes permissions so that you can update Vuze with Vuze itself.  I found that via _[color=blue][thread=995327]this thread[/thread][/color]_ the major difference in that thread's version of events is that you create a vuze user to run vuze under.  I might change that later because it is more secure and should still allow for updating.
Anyway I thought that would help you.

---

### Post by rifter on 2010-04-22
Well, for some reason when I installed the new Vuze according to that howto it forgot that I had chosen the old ui in the ui chooser and started eating cpu like a fiend (this is using the latest 64 bit version of vuze).  There's probably something else going on here.
But what I noticed was that when I deleted that version and reinstalled the getdeb version it upgraded me to 4.3 properly. (the version that is currently available from sourceforge is 4.4).  The menu option was gone, which actually had not been removed during the remove step, and I had deleted manually ...
I switched the ui and then went back through the process of manual install for the 64 bit version and it remembered the UI setting this time, but still eats cpu.  That's a problem for another day.
Anyway what might be helpful for others is that when you upgrade vuze from getdeb it seems the replace does not really work.  The step of doing apt-get remove on the old package seems to be key here.  Getdeb's version is still behind the latest, though, which is why that howto is helpful.

---

### Post by rifter on 2010-04-22
I figured out what was causing the cpu thrashing in the manually installed Vuze. The script (/opt/vuze/azureus) that came with it had the following line in it:

JAVA_ARGS="-Xmx128m"

which makes Vuze have a max of 128MB to work with.  On my system it needs a lot more than that. Unfortunately I couldn't just set it to a space or null for some reason; the later lines would parse wrong and the class path would never get specified on the command line (reading the script, I honestly can't see why, but I am sure it will dawn on me later when I am less tired).

So I had to get rid of every instance of "${JAVA_ARGS}" in the script as well.  Then it worked fine.  Now unless you also set SCRIPT_NOT_CHANGED to 1 at the top the script might get changed in updates, so be forewarned.

---

### Post by CTolley on 2010-05-10
Thank you rifter for linking the howto and thanks to Forlong for writing it.  My Vuze is working like a champ now.

-Tolley

---

