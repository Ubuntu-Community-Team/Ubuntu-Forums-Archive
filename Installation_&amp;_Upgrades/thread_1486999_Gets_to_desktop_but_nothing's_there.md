---
title: "Gets to desktop but nothing's there"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by StephenG on 2010-05-18
Been using 9.10 without incident.  Did the package manager update to 10.04 and now it boots as far as the desktop but there's nothing there.  Oh, yeah, the wallpaper is still there but no icons, no links in the bottom bar, no way to get to command line.  I can't tell if there is 'net connectivity.  Tried to boot into safe mode and after a long list of text I can finally get to a command line but of course I can't get any updated anything since there's no connectivity to the 'net.  I list about 6 or 8 choices at the GRUB screen, but none of them (recovery mode or regular) gets me anywhere.  All grub choices are 10.04 variants.  I can't seem to find any way to even get back to a 9.10 installation.  Fortunately I have the laptop (that I didn't "update" yet) so I have connectivity if I need to download something, though I'm not certain the system will find the CD drive or thumbdrive, so that's still a future experiment.  Any thoughts, anyone?
Home-built: Gigabyte board, AMD Athlon X2, nVidia GeForce 6100, nVidia nForce 430.  Nothing special really -- no gaming stuff, just a schoolwork computer for my kids.  All 9.10 updates were done prior to upgrading to 10.04.

---

### Post by maybeway36 on 2010-05-18
I suppose you could boot the computer from a live CD, back everything up onto USB, then reinstall. It might be a bit of work, but it's one sure way to fix it.

---

### Post by mathias j sagartz on 2010-05-18
Lots of people have had problems having their desktop come up without
panels.  If you can get the applications menu to appear by pressing
alt-F1 and can open a little run application window by pressing alt-F2,
this may work for you.  What needs to happen is to execute a script 
containing the following 3 lines of code. (I have no clue exactly what
they do, they came from a guy named Holeyfield) 

```

gconftool-2 --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

``` 

If you can open the applications menu you can use gedit to create this
script file and you can open a terminal to make sure the file permissions 
are set to make it executable.  Then when you boot and are faced with the
blank desktop press alt-F2.  In the little window that appears enter the
path name of the file you just created and saved.  Press the run button
and in a few seconds the panels should appear.

Hope this helps.

---

### Post by Catharsis on 2010-05-18
That's a really cool fix. Thanks for posting it.

You actually don't have to make it a script. Just do Alt+F2, check the "Run in terminal" box, and then enter the three commands one at a time.

Best of luck.

---

### Post by StephenG on 2010-05-18
I'll try these tonight -- after the kids are in bed.  Thanks.

Nope, no reaction to either Alt-F1 or F2.  I get the logon screen and after entering the pw I get the regular desktop (with the regular wallpaper still intact) but that's all there is.  No responses to any other commands that I can decipher.  Mouse works fine and so does keyboard (which I found out while in one of the dozens of recovery mode screens I've wandered around).  I can get to the root shell prompt, but not the choice with networking.  Well, actually I can get to that one, but no wireless connectivity can be established, so it's a useless drill.

If I try to run in failsafe graphic mode, I get a menu that offers to let me reconfigure graphics or troubleshoot the error, but there's no getting past any of those options successfully.

Wait minute !!!  I ran the three commands from the root shell and rebooted and lo, adn behold, I got a desktop up.  Trying to update now and see what I end up with.

---

### Post by sccar_support on 2010-05-18
I'm seeing the exact same behavior.  Tried the fix described above and all three commands ran but still no desktop icons.  I also cannot run things like the ubuntu software center or right-click options on the desktop.  It tries to open but never does.  When I run it command line, I get:

(11) [~] > /usr/bin/software-center

GLib-ERROR **: /build/buildd/glib2.0-2.22.3/glib/gmem.c:156: failed to allocate 3855203796 bytes
aborting...
Abort

I see plenty of posts about this problem but no workable fixes yet

I'm running 9.10 (32 bit).

---

### Post by StephenG on 2010-05-19
My issue is fixed!  Woohoo.  Now, if I were only capable of helping the newest member of our "non-working-desktop family," I'd be happy to.  I wish you the best of luck. May I suggest you search out whoever "Holeyfield" is, perhaps he or she has an aswer for you.  For now, I should mark my original thread solved, eh?

Sccar -- did you try running the commands from the root shell, going throught the recovery mode boot menu, or through the desktop link to the terminal?

Mathias, where did you find the Holeyfield post?  I just did a search by that user name, to thank them for the answer, but cannot find anyone in this forum using the name.  Can you direct me there, for a proper thank-you?

---

### Post by mathias j sagartz on 2010-05-19
After a little searching I found the original thread, "All my panels have
gone away" posted on 2/11 by perevera.  The fix came from the third reply
by Howefield.  Sorry I butchered the spelling of his name.

My loss of panels was a strange thing.  After I installed Lucid I rebooted 
once and everything was fine.  But on all reboots after that I got the same
blank desktop that you did.

---

### Post by Arnie Tchelakian on 2010-05-19
Using 10.04 also. What can one do if unable to get a Alt-F1 or Alt-F2 response?

I Boot up, and like normal it asks me for Wifi password; enter that and everything normal -straight to the Desktop but without Panel, Icons, or anyway to open terminal or start any Apps. 

I know my files are still intact; used an old install CD to give me a temporary Desktop to play around with. That's how I'm able to be writing this.

The only thing I can seem to do is Lock the Desktop, and then go to the Switch User screen, but I only have 1 user.

Any ideas? I'm a little new at this. I don't get any mouse pointer; however Alt-Ctrl-Del gives me the Shut Down box, and I can scroll around aimlessly until one of the selections lights up. Keyboard seems to respond, but no Alt-F2 box will come up, even thou it normally would. Very sad about that.

I hit some strange combination at some point and it gave me command line full screen, and of course I was lost as soon as I saw that. Ended up typing bad words into it hoping it would understand that I was angry.
No avail. But at least that's how I knew the keyboard worked.

Anyone ?? Anyone...
Thanks.

---

### Post by StephenG on 2010-05-19
Arnie T -- see posts 3 and 4 for the cure that worked for me.  Instead of letting it boot all the way to my useless desktop, I cut it short with the ESC key at the prompt to interrupt the GRUB boot loader.  Once there, I chose the Recovery Mode option and that took me to a menu giving me an option for Root Shell.  Once there, I executed the three lines of code (one at a time) that are in post #3.  Rebooted and all worked.  I did have to tweak some of the desktop settings, but at least I didn't have to reinstall and I didn't lose any data as afar as I can tell.

---

### Post by mathias j sagartz on 2010-05-19
Stephen, do you have to use this procedure every time you boot up or
was this a once and for all fix?

---

### Post by StephenG on 2010-05-19
So far, I used it only once.  I've rebooted, for the express purpose of finding the answer to that question, about a dozen times and things are still working perfectly.  I'm not ready to declare it a Once And For All Fix, but it is for now.  Perhaps since I executed the commands from the root shell instead of from a terminal from within the desktop, it got it fixed a a lower level.  I don't know and that is sheer speculation.  I am not at all well-versed in Linux.  But reflecting on Windows and the way it sits within a DOS system, if you make changes to the config.sys file, for instance, they take effect prior to the Windows shell opening and so the theory makes some sense to me.  It's only a guess and I'm sure someone is fixing to "spark" me about the comparison.  So be it.

---

