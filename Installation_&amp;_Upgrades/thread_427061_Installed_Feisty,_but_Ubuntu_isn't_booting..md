---
title: "Installed Feisty, but Ubuntu isn't booting."
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by MSTK on 2007-04-29
I've been using Edgy Eft for a while now as my main operating system.  I was thrilled when the update came.

However, for the longest time I couldn't upgrade to Feisty because it kept on showing an error that certain repositories couldn't be accessed (having to do with Beryl).  I thought it was a network problem on my part, but then someone told me that those repositories were ones that I added myself, and that I should just comment them out with # on sources.list (which, now that I have read the forums, might not have been a good idea).
So after I got rid of the unverified repositories, the installation worked.  I put it in the background and continued to work.

Earlier that day I had decided to begin my journey towards becoming familiar with the terminal and command line, so I went back to tinkering with things.  Soon, though, some things started slowing down and the GUI for browsing folders even crashed once.  Then Firefox crashed (which it does often on my computer anyway, for some reason).

I set those all aside as either (1) being interfered by my familiarization of the terminal and command line or (2) being interfered by the distribution upgrade that was going on.

The upgrade was still running in the background when the terminal froze and the computer vehemently died.

Had the upgrade finished and reboot started?  Or was it a "regular" system crash from a problem in the terminal? (I had loaded gaim-text right at the time of the crash to see if it worked.  It seemed a bit unstable before the crash)  I don't know, because I didn't catch a glimpse of the progress bar.  I had last seen it about 10-20 minutes ago, and it read "20 minutes" then.

The computer started booting up again, and a light blue screen showed up (Bypassing GRUB).  A log-on prompt appeared.  I thought to myself, "This must be what the Feisty login screen looks like."  I checked the "About" dialog, and it said that the  version was indeed Feisty.  I entered my username and password as normal, and the desktop began to load.
Except...it did not.  The screen stayed completely blank, with a light blue background.  After a while, I typed CTRL+ALT+DELETE, which brought up a session manager.  However, beyond that, I found no interactivity.

I tried CTRL+ALT+F1.  I'm not sure what I did there, but it ended up with a resounding sudo shudown -r now.  I forgot whether or not the shutdown actually went through or whether I had to manually do a hard power-down.  I just knew that things weren't going smoothly.

GRUB loaded up upon reboot.  Nothing was different.  I selected Ubuntu, and the loading bar appeared.  It was the same loading bar as Edgy Eft, if that could indicate anything.
Only, the loading bar froze.  It didn't move.

I waited a while, and then did a hard power-down.  I knew that I should never do that, but I believed that I didn't have a choice.

GRUB loaded up again, and I thought that maybe the problem was resolved.  But once again, the loading bar had froze.  I decided to wait this time.

After about three minutes it quit out into a condensed command line called "BusyBoxv1.1.3".  "Built-in shell (ash)".  I thought, "Wow, this must be a good time for me to put my newly acquired command line skills to the test."
However, much to my chagrin, BusyBox could not access the hard drive.  In fact, it couldn't do anything.  It only had a few built-in commands.  There was a limited file hierarchy, but it was mostly empty.
I typed "reboot", and the computer rebooted.  Back to GRUB.

My Windows still booted.  "Ubuntu (Recovery Mode)" I could make no sense of, and wasn't much more useful than BusyBox.

So now, my Ubuntu isn't booting.  That's my problem.  Can anyone help?  It feels like a part of me has died.

EDIT: This seems to be similar (if not identical) to the "/bin/sh: can't access tty; job control turned off" bug, except off of an update manager upgrade instead of a liveCD.  So it might be my hardware.

---

### Post by hal8000 on 2007-04-29
> **MSTK said:**
> I've been using Edgy Eft for a while now as my main operating system.  I was thrilled when the update came.

Earlier that day I had decided to begin my journey towards becoming familiar with the terminal and command line, so I went back to tinkering with things.  Soon, though, some things started slowing down and the GUI for browsing folders even crashed once.  Then Firefox crashed (which it does often on my computer anyway, for some reason).
--snip--


I think the above paragraph is your problem. What commands did you type and what exactly did you do?? By making multiple changes you have corrupted something.

Boot with the live Feisty CD, plug in a USB pendrive, mount your old /home partition and recover your personal data.
Unless you can give specifics, or a different answer your best option is a clean install, sorry.

---

### Post by MSTK on 2007-04-29
> **hal8000 said:**
> I think the above paragraph is your problem. What commands did you type and what exactly did you do?? By making multiple changes you have corrupted something.

Boot with the live Feisty CD, plug in a USB pendrive, mount your old /home partition and recover your personal data.
Unless you can give specifics, or a different answer your best option is a clean install, sorry.

It wasn't anything too damaging.  I'm not a complete newcomer to command lines.  I was mainly tinkering with VIM, browsing with links2, etc.  I didn't modify any system folders.  Nothing that would damage the system, or so I'd believe.

I don't take Firefox crashing to be a significant event, because Firefox seems to always crash on my computer for some reason.

The last thing I was doing on the terminal was loading gaim-text.  It either froze up, or I didn't know how to interact with it.  I'm guessing it's probably the latter, because I pressed TAB and it seemed to respond to that with no latency.  Yet, I couldn't find any other keys that could control it so for all purposes I believed that it was unresponsive.

---

### Post by bulldog on 2007-04-29
You can try from the recovery console ```
sudo aptitude update && sudo aptitude dist-upgrade
```
With a little luck it upgrades your install to a workable situation.

---

### Post by MSTK on 2007-04-29
> **bulldog said:**
> You can try from the recovery console ```
sudo aptitude update && sudo aptitude dist-upgrade
```
With a little luck it upgrades your install to a workable situation.

I'm sorry, but recovery mode isn't even responding for some reason.

---

### Post by bulldog on 2007-04-29
Can you get to a console at all?
If you can try it there to see if it's responding.

---

### Post by MSTK on 2007-04-30
I can enter a console by booting the LiveCD and using it from there.  The drive mounts fine, and I can chroot without a problem.

I'm going to browse some answers to the "/bin/sh: can't access tty; job control turned off" bug.

Fortunately, now that I can actually boot into some form of Ubuntu, I can back up my home folder.  I'll probably end up doing a full reinstall and copying my home folder back on.

---

