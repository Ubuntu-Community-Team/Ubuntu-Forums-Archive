---
title: "URGENT: Feisty suddenly degraded...can no longer boot normally"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Old *ix Geek on 2007-06-23
I have NO IDEA what happened, but last night I suddenly was unable to do various things.  First, when trying to "Open in File Manager" my home directory, an error modal came up saying...something.  (I didn't write it down.  Sorry.  It never occurred to me that things would rapidly degrade.)  I could access everything just fine from a command line, but not graphically.  I tried to run Konqueror, but after long attempts at loading it would just disappear silently.

I decided to reboot.  (It's a laptop, and it gets rebooted frequently anyway.)  That's when everything just fell apart.  :(

Attempting to boot normally (from GRUB's choices) yielded a blank screen instead of KDE.  Just blank...no mouse pointer...no prompt...nothing.  To get out of it I had to power down.

Next I booted in recovery mode as root, then manually executed kdm.  It LOOKED like it was going to load--there was a spinning mouse pointer--but that's as far as it got.  Again, I had to power down.

Now, I can log in as root (CLI only, in recovery mode), and navigate through all directories, run commands, etc. (good thing I started back when *nix was CLI only!), BUT anything I attempt to do that takes more than a few seconds to execute ends up hanging.  For example, I've tried multiple times to ftp files to my web server, and it'll be cranking away...and then just hang.  I tried recursively zipping a directory, and after cranking away for a while...it hung.

As I said, I literally have no idea what's happened.  And I have to say that I'm STUNNED to be faced with a *nix system that suddenly, inexplicably degraded so that even root can't function properly.  If this had happened at the companies whose *nix systems I administered...I'd have been jobless.  :(

Does anyone have any ideas?  Anything I can look at that may give some insight into what happened?  Anything I can try to fix things?  I finally had this laptop running JUST like I wanted.  I've highly customized it and gotten things working smoothly that in the past I've had problems with (i.e., wine PERFECTLY running Roller Coaster Tycoon 2 and other games, my Broadcom wireless running at high speed, etc.).  I REALLY, really don't want to lose all of this...and I don't like thinking that the only way to solve a problem is by the infamous windows method: Reinstall the OS! ](*,)

---

### Post by merlinus on 2007-06-23
A few thoughts come to mind:

Can you try to re-seat your video card?  Are all the cables, etc. securely plugged in?

Is your hard disk heading to the south pole to visit with the penguins?

Can you boot from a live cd?  If so, you can probably save your data.

Good luck!

-merlin

---

### Post by checho on 2007-06-23
That happended to me once while trying to install compiz in a computer which it´s video card could not handdle it I think that simply your graphic interface archive is corrupted. I know is a big issue but is just one problem and not a total lost of the OS, like seems to be. 
In fact what you can do is replace the configuration file in the /etc directory. Just google in console (ctrl+alt+F1). You can use the command lynx and the webpage address (lynx [www.google.com](www.google.com)). This command is not installed by default so you first may do and "apt-get install lynx". Now in the web search for a configuration file and replaced. I can't give you more advice in what is the exactly name of the file or give you the configuration file because i use gnome. Anyway try this page [http://www.antipope.org/charlie/linux/wibble/kde_themes.html](http://www.antipope.org/charlie/linux/wibble/kde_themes.html). There gives a good explanation about the kde file system. I tried to find a functioning configuration file in the web for you but couldn't find it. Maybe you may have better luck, or get an installation cd and copy it (file or files or even the entire kde folder) or maybe someone reading this post and using kde may post it for you

---

### Post by Old *ix Geek on 2007-06-23
Thanks for the quick replies.  Just to clarify: The laptop itself is working perfectly--I'm using it right now...but from "the dark side" (windows).  So it CANNOT be a hard drive issue, graphics card being loose, etc.

The graphics configuration file sounds promising, so I'll explore that a bit.  Meanwhile, any other ideas are greatly appreciated!

---

### Post by Old *ix Geek on 2007-06-23
I've spent hours crawling through logs and looking for files that changed around the time things screwed up last night...and right now--don't ask me how!--I'm posting this from the Linux side of the screwed up laptop.  So at least I'm making progress.  I do NOT want to wipe out all of my very customized settings/tweakings, so I'm going to avoid a clean reinstall like the plague.  (Note that I'm logged in as root on Gnome, neither of which I normally use.)

In my daemon.log there are a bunch of entries of this form:

Jun 23 19:30:00  HPLaptop ccsd[4306] : Unable to connect to cluster infrastructure after 300 seconds
Jun 23 19:30:30  HPLaptop ccsd[4306] : Unable to connect to cluster infrastructure after 330 seconds

and so on.

Okay, first of all, I really don't know what a "cluster infrastructure" is, nor do I know anything about **ccsd**. But once I saw those ever-increasing entries in daemon.log, I killed off **ccsd** to make them stop. :)  So my first question is, what the heck does this mean?

In other logs, I'm seeing a lot of references to **gconfd**, but--again--I have no idea what this is, and neither **apropos** nor **man** turned up anything.

If there's something I can post (log contents, command output, etc.), please let me know and I'll post it.  I really need to get this sorted out.

If it comes down to it and I need to reinstall Feisty, will doing so wipe out my data and/or customizations? (I think the answer is yes, but I don't understand why there wouldn't be a nondestructive option.)  And, no, I do NOT have a separate /home or /data partition.

---

### Post by merlinus on 2007-06-23
You can install the ext2 ifs driver and back-up your home directory and data from windows.

IIRC, gconfd is a gnome configuration file.

-merlin

---

### Post by Old *ix Geek on 2007-06-24
Well, I SOMEHOW got back up and running (I couldn't begin to recount everything I did...but it worked!).  But since I still don't have a clue WHAT went wrong, I'm a bit nervous now that it'll happen again.

Anyway, for right now at least, the problem is solved.

---

