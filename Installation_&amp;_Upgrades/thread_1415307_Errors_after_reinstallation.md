---
title: "Errors after reinstallation"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Giacomo23510 on 2010-02-24
I had Ubuntu 9.10 installed in a dual boot configuration with XP, each in their own partitions.  Prior to 9.10, I had also had 9.04, 8.10, 8.04, and even earlier versions installed with no issues.  As you would know, my Windows installation became corrupted and I decided to reformat and repartition the whole hard drive.

I reinstalled XP first and and it runs like new.  However, when I reinstalled Ubuntu 9.10 errors began to appear.  I first noted pop-up dialogue boxes such as messages indicating connection to the network, updates available and even the terminal appeared as blank white boxes.  I could use the terminal window, such as entering commands to edit my boot file, but no text would appear in it at all.  Then, in attempting to download the available updates via the update manager, the computer would freeze, necessitating a reboot.  After rebooting the same errors would happen.

Thinking that this was an issue with 9.10, I uninstalled it and installed 9.04, thinking an older version (which previously also worked fine prior to the reformat) might solve the problem.  No such luck, same issues.  I then uninstalled 9.04 and installed 8.10 using the same train of thought.  Same issues.

All the included application software that I tried seems to work ok as does the network connection and browser, but I cannot figure out why I am having problems that I didn't have before.

No changes have been made to the hardware.  I'm using an old Dell Optiplex G110 with a PIII 866, , 810E chipset, 512 mB memory and a 120 gB hard drive.  I know it sounds weak, but Ubuntu was working great before I reformatted and reinstalled it.  I've tested the memory and hard drive with no errors reported.

I would really appreciate any help you may be able to offer.

Thanks.

---

### Post by quixote on 2010-02-26
Strange that it's having the same issues no matter which version you install.  Probably, you're putting them in the same partition each time?  If so, is there any chance that partition somehow became corrupted?  Try booting from a liveCD, make sure the hard drive is not mounted, and run ```
sudo e2fsck -p /dev/sda2    *[COLOR="Blue"](substitute the right partition designation for your ubuntu install)[/COLOR]* 
```If you want more detail on that, let me know.

---

### Post by Giacomo23510 on 2010-03-02
Quixote,

Thanks for the tip.  I tried it, but couldn't tell what the output was as the terminal window does not show text.  As before, the window is a white box, no prompt shows, no entered text shows and any system response also is not shown.  This seems funny as Ubuntu was run off the CD with no hard drives mounted.

With the previous re-installs mentioned in my original post, I did delete and repartition the Ubuntu and swap partitions and formatted in ext3 prior to each of the re-installs.

The disk failing warning had appeared after each each re-install, but it also appeared in ubuntu prior to my initial wipe of the hard drive when ubuntu was working fine.  I had tested the disk with windows and dos tools after the wipe and no errors were reported.  The drives SMART information also showed the drive to be ok.

Out of frustration, I'm going to delete the partition again, test it again and reinstall 9.10 once again.

Please let me know if you have any other ideas

Thanks again for your help.

---

### Post by Giacomo23510 on 2010-03-02
Quixote,

I tried running the command you provided on the Ubuntu partition using Puppy Linux and had the following results:

"clean, 111009/1038352 files, 642738/4150786 blocks"

It appears that the partition is ok.

Do you have any other ideas?

---

### Post by quixote on 2010-03-02
You mentioned trying to reinstall ubuntu.  Did you try that?  At this point, that would be the only suggestion I have.  Maybe the install just didn't work right for some reason.  The fact that you got the same white-window problem off the liveCD strongly suggests that maybe the version on the CD is the problem. ??

Try reinstalling, and either use a CD that you know for sure got you a healthy install before, or download a new iso and burn it at slow speed (eg 10x or 8x).

---

### Post by Giacomo23510 on 2010-03-04
Well, I've downloaded 9.04 again (I wanted the older version of GRUB), burned it to CD and installed it after repartitioning the Ubuntu partition.  While things were slightly better this time, i.e., updates run fine, system does not lock up (even updated to 9.10), but the "white box" problem continues.  Not being able to see what is entered into or the response in the terminal window renders this install unusable.  It seems that the terminal window is the only window that I am having this issue with thus far.

In the hope that it may be a clue to the cause of my issue, something I failed to mention earlier was that when the mouse is clicked, a small square (abut the size of an icon) remains in the position where the cursor was.  If the window can be scrolled, the "square" goes away immediately, otherwise it remains until several other "squares" have occurred.  Also, when hovering the mouse over any text in the drop down menus, it colors and distorts the area surrounding the cursor for a split second.

I guess I'll just keep playing around with it until it drives me to the point of removing it from the system.  I really enjoyed using Ubuntu for that past few years to learn linux and as a decent operating system for my out-dated PC's, but with this problem, I'm not going to be using it for much longer.

Thanks for your help.

---

### Post by quixote on 2010-03-04
If this problem is only in the terminal window, I wonder if it's possible that there's an odd setting somewhere in preferences.  Open a terminal window, go to Edit > Profile Preferences, and see if perhaps the text color is set to white or something.  It's a long shot, but who knows.  

Sorry to hear you're so fed up you're ready to dump the distro.  :(

There are also other terminal programs.  xterm is kind of basic, but usually installed by default, and you could at least see whether it inherits the same weird problem.  There's also KDE's konsole which can be installed from synaptic.  The simplest way to start xterm is by typing "xterm" in a terminal.  I realize that for you that involves typing on faith, but I think it would work.  If you install konsole, it'll put a shortcut probably under Accessories.

Another thing I should have maybe mentioned is that you don't have to use grub2 with karmic.  You can use old grub just fine.

---

### Post by Giacomo23510 on 2010-03-08
As you suggested, I opened "Terminal" and guessed at where the drop down menu was for Profile Preferences.  I check them and they appeared to be in order. I even changed them to white on black, but this had no effect, I still have the blank (no header either) white window for terminal.

I did use X-Term for a few operations successfully (edited the boot menu).  For some reason, that does not have the blank window issue.

I then downloaded and installed Konsole, hoping that I could use it to replace Terminal.  Alas, I have the same issue with both Konsole and Terminal.  I would also like to add that any window that pops up  requesting the admin password (such as when running the update manager, synaptic, or installing the printer driver) also appear as a blank white box, but knowing what it is, I just type in the password and updates or downloads work fine.

I even scanned the installation with ClamAV, thinking perhaps a virus was causing this behavior.  While Clam did find two suspect files, moving them to quarantine had no effect on either Konsole or Terminal, and the issue continues.  At least with X-Term, I can use the system somewhat.

Thanks again for your help.  I'll continue to play around with it and hopefully get it working as it should, even if it takes more reinstalls.

---

### Post by Giacomo23510 on 2010-03-08
Quixote,

Well, the mystery is finally solved.  In searching on google today, I found a user that experienced a similar problem with 7.04.  To solve the issue, I went into System/Preferences/Appearance/Visual Effects and changed the setting from Normal to None.  No more blank white windows.

I realize that the computer I'm running Ubuntu on is definitely not a powerhouse, but I didn't realize this setting could have such an effect.  I still don't understand why I didn't have the problem with previous installs unless the selection was set to none in an earlier version and the subsequent upgrades via Update Manager through many interim versions did not make changes.

Thanks so much for all the time you spent with me on this.

---

