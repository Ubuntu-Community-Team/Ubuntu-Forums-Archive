---
title: "There's Truly No Place Like Home"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-01-01
The last three days have been really interesting.  If you bother to search on my user name, you can see I've had this war going on as to which is better, Ubung.tu 9.04 or Ubuntu 9.10.  I've experienced so many problems in getting 9.10 installed and working, that I pretty much just went back to 9.04 for the time being.  Others have said the same thing.

Have you been counting?  Install 9.04, and there re 264 patches waiting to be downloaded and installed.  With 9.10, there are only 164 at present.

In order to protect my valued email which is being handled by IncrediMail under Windows (no Linux version), and that means running Windows as a client under VirtualBox.  A pretty good arrangement.  But reinstalling Ubuntu as many times as I am given to do, I have to preserve that VDI of Windows, download and set up VirtualBox again, and resume my use of Windows as a client.

So what I've been doing is not a reformat of the root partition, but a delete of everything except the /home folder and what's in it, which is the user accounts.  But I did not realize something until a had a bit more experience in doing this.

What is was is that every user account is really set apart, and every user can customize the Desktop, screen resolution, and whatever to suit himself or herself without effecting any other user.  Windows pretends to do this, but much of Windows is shared among users, only you may not realize it.  Anything different between users has to be set up and supported by configuration information or actual programs installed just in certain user accounts.  That might seem a bit obvious, but it has some carry over effects.

For instance, the other day the touchpad on this notebook was no longer recognized.  The mouse pointer also shrank in size.  No known reason for it, it just happened.  Each time I reinstalled 9.04, I had the same problem.  All I was leaving on the driveeach time was the lost&found folder and home.  So I backed up home to an external drive, and went through a full format as part of the reinstall.  I got the touchpad back, but I also suddenly found I could see nearby access points on my wireless as well.  I even connected on my host's hnetwork, which is unsecured.  What happened?  I shut down my notebook to resolve some problems my host any my wire's cousin were having with their computers, but when I turned my notebook back on, the screen resolution had gone to pot again.  What was happening here?  I shut down so we could enjoy dinner and watch a movie together, then took it up again when I got home.

Screen resolution had now dropped to a maximum of 640x480.  No higher setting was offered.  I looked at /etc/X11/xorg.conf, but there were just a few statements in there concerning video, so what happended to the ones about the keyboard and mouse?  And there were no statements about resolution, and it would not accept any.  In fact the documentation on xorg.conf is some of the poorest on record, with no real good examples.  Let's see how the 9.10 side looks.  Much better. Resolution is good, choices there, touchpad is working, just can't tell about the wireless adapter.  But there is no /etc/X11/xorg.conf file either!  What is going on here, and how can 9.10 know all the screen resolutin settings if there is no file to tell it these things?  Tackle it tomorrow, as it is already late.

It came to me overnight.  If I leave everything intact under /home, then I must also be leaving the existing configuration settings for each user in place.  If those settings are either right or wrong and left behing, then they could effect the outcome of the next install for that same user.
But what was causing these settings to change?  The one thing I really don't like about the Toshiba L355-S7915 is its keyboard.  It is essentaily flat, and the touchpad is in the way when you try to type.  The spacebar is small and set too far up among the other keys, so there is no good way to rest a thumb on it or strike it when a space is needed.  I often strike wrong keys when trying to type, and the cursor keys are too near my right hand, so I am bouncing about on the page, often out of position when I strike the next key.  Maybe some of the unruly key combos are inducing settings changes and I just don't realize it at the time.  Could that be it?  I don't know.

Anyway, I attempted another reinstall of 9.04, but this time it came back and complained that there was a parsing error on line 33 of the config file.  Followwing the steps outlined, I was taken to the config file, which turned out to be /etc/X11/xorg.conf.  And not just any version of this file, but the one I had worked with earlier to see if I could induce the allowed screen resolutions for this notebook, which range up to 1440x900.  But even following the manual, nothing was accepted here.  I tried to comment out the line, but that did not take.  Then I just deleted the line, but I still got the error.  And it would only let me continue booting in low resolution mode.

So maybe in a normal boot process, something like this happens, and you don't see a message about it, it just continues to boot up in low resolution mode.  That might account for the reason that once I encounter a problem, it just persists, normally.  If it comes and goes, then maybe  I just have a problem with reading some files correctly from the hard drive during the boot process.  If so, then it suggests that perhaps Ubuntu, or Linux in general, does little to screen for incorrect file readings as the boot process continues.  If this were the case, then one solution might be to have additional safeguards where system and configuration files are involved.  One method here might be to keep a better check on file checksums, and perhaps a backup copy of critical files that can be used when the primaries are found to be inadequate.

Meanwhile, to accomodate my desire to have it both ways, I will back up my /home/[username]/.VirtualBox directory and contents.  Do a full reinstall after reformatting, then copy this directory and condtnes back to the same place.  You may have to change ownership or access rights when you do this, just so that the user can make use of it, otherwise you may may not have sufficient priveleges.  Alternatively, you could just copy or move this to another place, say /home, and then delete your entire user account.  But this would create immediate problems as your user, user settings, and such were erradicated.  Best quit the GUI mode, log out, and log back in as someone else, say root or superuser.  You may not be able to, but there are way it can be managed.  You could even start up from a LiveCD and enter the Terminal mode to do what has to be done first, before then going right to Install.

Normally I have little to say in fvor of Windows over Linus, but there are some notable exceptions, like these:

/Control Panel/Add/Remove Hardware  (when it works)
/Control Panel/Add/Remove Programs  (Until they took it away)
/Control Panel/Administrative Tools/Computer Management/Disk Management
/Control Panel/System/Device Management
/Control Panel/Internet Options
/Central Panel/Network and Dialup Connections
/Central Panel/Mouse (change more aspects of mouse)

I mention this in passing, because it's easier to control things when part of a corporation, whereas each package manager sets a different profile for configuring his package for use.  Even if decent documentation then comes forth, There is just more to deal with, look for articles on, read, and learn.

---

### Post by oldefoxx on 2010-01-01
Aside from the problems described above and how I have tentatively associated them with persistency in some traits due to having left behind config files when a new install is taking place, there is the question of why Ubuntu seems to have a bigger problem when installed on some PCs.  It's as if its efforts to correctly identify the hardware involved suffers somehow.

What can I possibly mean by this?  Well, many Toshiba notebooks support the same wireless card across different models, and the install seems to fail with them quite often, so much so that some users have bought a different plug-in or external card rather than deal with the frustrations of trying to make the internal one work.  Some that have gotten the internal card to work have not been pleased with the results, citing weak signal strength, slow performance, and a tendency for a connection to be lost.  So call that one possible example.

But maybe here is a better one.  In all my installs and reinstalls of either Ubuntu 9.04 or 9,10, I've always reached the final stage where it said that the install was completed, and a restart was needed for the process to be finished.  And I've always noted the same three things:

(1)  The screen was at high resolution automatically
(2)  It is able to connect to the internet on its own
(3)  The keyboard and mouse/touchpad are working with no problems.

Now this is what the installer pretty much did on its own to identify and work with the hardware at hand,  But if you reboot the PC and wait for it to come up, something can have changed among these three,  Now what is it that the installer discovered and used to its advantage that does not carry over into what gets installed?  Why aren't the discovery methods used by the installer incorporated into the boot process when it is set up on your hard drive?  I think that is a real good question,  Another might be, how can we relate to the configuration information being handled by the installer and improve the resulting boot process ourselves?

And let me add one more:  I've complemented Linux for its ability to get you up and running to some extent, whereas Windows just dives into its BSOD mode and leaves you hanging,
but what's with the Recovery Mode features promoted, like on the Alternate CD images for Ubuntu?  I've tried them, with no net gain, and there are no instructions on what to do to help yourself.  I'd just as soon start over with a new install than fumble around with a recovery process that isn't getting anything done.  At least the Install process knows what it is there for and gets the job done.

---

### Post by oldefoxx on 2010-01-02
To test the idea of user-based config files, I added another user named newuser, then transferred my initial account's folders and files over.  When I logged out, then back in as newuser, I had the default settings for the screen and the mouse, not the ones I had configured for my initial account.  So that falls through.  I then spent some time looking through the folders and files on both accounts, but there wasn't much to go on.  A folder called .config, and some .xml files that might be relatede, but nothing really evident.

Did note something else as all this was going on.  I have an external hard drive that gets mounted automatically on boot up, but when I log out of one account and into the other, it isn't mounted any more, and a mount -a will not mount it either.  But I log out of that account and back into the one that I logged into when it first booted up, and there it is, still mounted.  Whichever account I first log into after booting up will have have access to the external drive.  Rather strange behavior.  If it was always the same account that had access, that might fit with an effort to exercise some degree of security in this matter.  But the first to log in has posession?  That is something quite different.

---

### Post by oldefoxx on 2010-01-03
Something seems clearer now.  First, as I have found, there are no config settings in the user accounts for their preferences for things like screen resolution and brightness, or mouse behavior.  But they are being tracked somewhere, because you set up a new account and it defaults to whatever the default settings are, and if you change them, they are remembered for that individual into the future.

Second, there are aspects of having and using a Toshiba Satellite notebook that effect everything from the way I type, sit, and can even expect my installs to come out.  Not that there is anything really bad about this notebook, but it has presented me with a few challenges.

Third, that on a review of some of the things I have encountered this far, I felt compelled to put in a couple of bug reports.  Not that each is really a bug, but perhaps there is a feature that seems to be missing in the present Ubuntu build.  One more comes to mind right now.  There is a setting under Power Management that lets me control screen brightness, but there is no corresponding setting that does anything about contrast.  Some of the color choices for text are so light, that trying to read what is written against a light or white background is almost impossible, for me at least.

You may have it the other way around, because I think we have all visited a site or two with a dark background on which they might use blue for the text.  Unreadable, right?  But I know of several tricks to deal with things like that, such as:

Highlight the text by selecting it with the mouse.  That might be enough in and of itselt to make the text readable.  If not, copy and paste it into something handy, like OpenOffice's Writer.  If too small to read, just pick a font of your choice and change the size as well.  That often works.

And one other choice I think worthwhile.  Go under View in FireFox and under Page Style, pick No Style.  That throws out a lot of the gobbledy-goop spread over the web page and lets you just read the text portions.  As to the problem with color mixing that makes it so hard to see?  Under Edit/Preferences, you can select Font, size, and color, which takes precidence over whatever was embedded in the web page.

Oh, something too small to read?  FireFox deals with that easily.  Hold down the control key and press the +/= key to enlarge it, repeating until it is at a size you want.  To go back, use the control key and press _/- until at the size you now want.  This only applies to the current page, meaning other pages will display at their normal sizes.  This is a feature you will often wish that other programs shared.

---

