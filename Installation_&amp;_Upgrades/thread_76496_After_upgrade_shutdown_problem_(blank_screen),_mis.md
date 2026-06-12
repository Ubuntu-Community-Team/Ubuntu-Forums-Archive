---
title: "After upgrade: shutdown problem (blank screen), missing program (kvim), + experience."
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by bkasterm on 2005-10-15
First my problem, then I'll give a general description of my experience upgrading.

The problem is that when I shutdown I get told that kdm is being shut down, and then the screen goes blank.  No more info on what is happening is shown.  Any suggestions on where to look for a solution to this?  I don't know what is involved in showing the usual information.  However the startup info is now (after the install) shown graphically (with Kubuntu logo).  The computer still shuts down, but I really want to see the info.

My computer is a Sony VAIO laptop with AMD processor.

**************

Now for the full experience:

First I did the upgrade at this time because I had some problems with parts of KDE craching on me (kicker mostly I believe).  I would not have done the upgrade now without this reason.  I had ubuntu installed with later KDE and some other window managers added.

I started using apt-get as at the time of install the info on using synaptec was not yet available on the update note page.  There were some problems, but following the suggestions given, I made it through.

After rebooting (at which time the start up info was still shown as text) X didn't work.  Again by following the suggestions given in error messages and status checking output of apt-get I got it all to work.

Now since I usually use synaptec, I fired up synaptic to see what it had to say about current status of my packages.  It suggested a huge amount of them to be updated.  There were some minor errors in doing this that were easy to overcome (by just starting the update again), until I came to a library used by gnucash.  This problem was only overcome by removing gnucash (which I don't use anyway).  After this I got everything working.

I did for some reason have to reboot a couple (three) times to get startup to work well (it started up fine, but the graphical interface showing the startup messages died on me.  I rebooted see if it always did at the same time, but it turned out that it automatically "fixed itself".  The shutdown still doesn't work.

So far two things are notheworthy.  I lost the setting for my desktop icon sizes in KDE and kvim is no longer present (also no package to install).

Off course very unpleasant during install was that at some point I couldn't start xine or any other media player to watch a movie I wanted to watch. :-)  By waiting for it to finish with some libraries it was installing this was fixed.  Fortunately my backup (using rsync) in the background kept running without problems (and yes I know, backing up only during installation might be considered a tat bit late [but previous backup was only a couple of days ago]).

Now all but the shutdown seems to be working well (and I hope my little problem with KDE is now gone, only time will tell; it wasn't something that happened very regularly).  I am really happy and impressed that whenever there were problems the suggestions given worked well (except for the problem with gnucash).

Best,
Bart

(later found)
1) rhythmbox no longer plays my music files.  Starting it on a file it just runs through all putting an exclamatoin mark in front of all of them.
2) JuK is no longer present.
I can still play music through NoAtun and Mplayer, but I don't like their interfaces.  I am going to try reinstall JuK.

---

### Post by bkasterm on 2005-10-15
Probably the first step in solving:
I found that the program involved in showing bootup graphically is called usplash.  And that should take care of shutdown too.  Now I can google more effectively for possible solutions.

---

### Post by ecentinela on 2006-05-04
Have you discover something?
I have the same problem... black screen on shutdown. How to solve it?

Thanks

---

### Post by bkasterm on 2006-05-10
I have not really worked on this.  The only thing I have is a workaround:
switch to another virtual console (I think 8), there the usual messages
are shown.

Best,
Bart

---

### Post by true_friend on 2006-12-02
i have also the same problem.
using edgy and cannot shutdown after blank screen. i have to power off manually.
any ideas?????????
Regards
True_Friend

---

