---
title: "Going back to hardy, I think..."
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Luke has no name on 2008-09-27
Firefox and flash have really been broken on Intrepid, and one of the most critical bugs in the distro wasn't (hasn't yet been) fixed (the ACPI / laptop hard drive killing bug).

The only things I wanted out of Intrepid was a new network manager, better suspend, and a few other things. I don't know what I'm going to do, but this web browser is getting SOOOOO bogged down, it's ridiculous. Wireless N support isn't in hardy, and suspend doesn't work well either, but I don't know if that functionality is enough to keep me on Ibex when I can't get sound out of flash, or browse facebook without the browser crapping out.

Oh, and the gnome-logout screen wasn't fixed on time, so the shutdown menu is not clean and concise as it was in hardy.

---

### Post by Slug71 on 2008-09-27
Have you tried doing a fresh install? I had tons of probs with FF too on AMD 64 and now its running fine. No sounds probs either. I even went back to Vista because of FF but now the only the only prob i have is that FF runs a little slow and doesnt like Java applets or script. Script still runs but slow. Cant get applets to load though.

Its still only an Alpha though so hopefully the BETA or RC will be better.

---

### Post by ThrobbingBrain66 on 2008-09-27
> **Luke has no name said:**
> Firefox and flash have really been broken on Intrepid, and one of the most critical bugs in the distro wasn't (hasn't yet been) fixed (the ACPI / laptop hard drive killing bug).

I think its been said many times that the "bug" is distro agnostic.  It's caused by over-aggressive power management in the firmware.

> The only things I wanted out of Intrepid was a new network manager, better suspend, and a few other things. I don't know what I'm going to do, but this web browser is getting SOOOOO bogged down, it's ridiculous. Wireless N support isn't in hardy, and suspend doesn't work well either, but I don't know if that functionality is enough to keep me on Ibex when I can't get sound out of flash, or browse facebook without the browser crapping out.

Ibex is still in testing at the moment and shouldn't be used on production machines.  You should expect to encounter problems...maybe even lots of problems.

> Oh, and the gnome-logout screen wasn't fixed on time, so the shutdown menu is not clean and concise as it was in hardy.

Wasn't fixed in time?  As above, Ibex hasn't been released yet. There's still plenty of time to fix bugs.

So now that we have that out of the way, what exactly are your problems?  We may be able to help you.

---

### Post by Sef on 2008-09-28
I have had problems with FF and Epiphany too.   Opera has worked well.  Just downloaded the Hardy version.

---

### Post by Luke has no name on 2008-09-28
ThrobbingBrain66: Beta freeze was thursday, artwork freeze was before that. It's possible, but I doubt they'll fix it. I hope they do, though.

I might try a fresh install, but I might just install hardy for the next month until Ibex is released. I know the hard drive problem is not specific to Ubuntu, but it's a huge problem. As far as Firefox, my Flash has no sound, npviewer.bin crashes a lot, and Facebook is disgustingly slow.

---

### Post by olskar on 2008-09-28
> **ThrobbingBrain66 said:**
> I think its been said many times that the "bug" is distro agnostic.  It's caused by over-aggressive power management in the firmware.


I'm so sick of the argument that only blaim the harddrivemakers.

That logic would not work anywhere else in the world, especially since Ubuntu HAVE the tools to fix this there is NO reason for Ubuntu not to fix this! Or they want to teach the harddrivemakers a lesson? If so, who will suffer from that? Yes, the users. This is actually one of the few things that really annoys me with Ubuntu.


Quote from bugreport> 
Do you really want to kill the harddrives (including all the data loss) of these people because you don't want to solve a problem that is the fault of bad firmware settings? Seriously. What ever happend to being a good samaritan. The fact that ubuntu _can_ solve this issue, puts _some_ of the responsibility on Ubuntu.

---

### Post by olskar on 2008-09-28
> **Luke has no name said:**
> ThrobbingBrain66: Beta freeze was thursday, artwork freeze was before that. It's possible, but I doubt they'll fix it. I hope they do, though.

I might try a fresh install, but I might just install hardy for the next month until Ibex is released. I know the hard drive problem is not specific to Ubuntu, but it's a huge problem. As far as Firefox, my Flash has no sound, npviewer.bin crashes a lot, and Facebook is disgustingly slow.

There is still lots of time :)

The betafreeze is just so it is possible to make a beta at all. Beta is made for finding bugs!

---

### Post by ThrobbingBrain66 on 2008-09-28
> **olskar said:**
> I'm so sick of the argument that only blaim the harddrivemakers.

That logic would not work anywhere else in the world, especially since Ubuntu HAVE the tools to fix this there is NO reason for Ubuntu not to fix this! Or they want to teach the harddrivemakers a lesson? If so, who will suffer from that? Yes, the users. This is actually one of the few things that really annoys me with Ubuntu.


Quote from bugreport

And I'm sick of of everyone complaining that Ubuntu hasn't fixed the problem yet. :)

Not only that, but hard disk firmware is proprietary, is it not?  That means that Ubuntu *does not* necessarily have the tools to fix the problem.

The point is that it can't be blamed on just one entity.  Lots are involved and lots should work together to fix the problem.

---

### Post by psyke83 on 2008-09-28
> **ThrobbingBrain66 said:**
> And I'm sick of of everyone complaining that Ubuntu hasn't fixed the problem yet. :)

Not only that, but hard disk firmware is proprietary, is it not?  That means that Ubuntu *does not* necessarily have the tools to fix the problem.

The point is that it can't be blamed on just one entity.  Lots are involved and lots should work together to fix the problem.

Have you used Windows much? I use Linux and Windows on a daily basis, and I can attest that Linux (and thus Ubuntu) is much more disk-intensive. With the minimum necessary processes and daemons running, Ubuntu seems to write to disk every five seconds, whilst Windows XP (when properly configured without all the associated junkware) is capable of keeping the disk idle for long periods.

To be honest I would be inclined to believe that it's Ubuntu's "fault" (though in reality, it's the hard-drive manufacturer's fault for choosing poor defaults).

---

### Post by zoomy942 on 2008-09-28
i dont get it.  all these people having flash problems - i use intrepid alpha 6 and used this to install flash

[http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html")

and its 100% fine.  no trouble at all

---

### Post by ThrobbingBrain66 on 2008-09-28
> **psyke83 said:**
> Have you used Windows much? I use Linux and Windows on a daily basis, and I can attest that Linux (and thus Ubuntu) is much more disk-intensive. With the minimum necessary processes and daemons running, Ubuntu seems to write to disk every five seconds, whilst Windows XP (when properly configured without all the associated junkware) is capable of keeping the disk idle for long periods.

To be honest I would be inclined to believe that it's Ubuntu's "fault" (though in reality, it's the hard-drive manufacturer's fault for choosing poor defaults).

Until 2.5 years ago, I had used Windows exclusively since Windows 3.1.
Since then, I've used Linux exclusively on my computers.  Listen, I'm not saying it's not an issue (again, the issue is distro agnostic...they all suffer from this). I'm saying that now that we know it's an issue, everyone needs to work together to fix it, instead of passing on the blame.

---

### Post by olskar on 2008-09-28
> **ThrobbingBrain66 said:**
> Until 2.5 years ago, I had used Windows exclusively since Windows 3.1.
Since then, I've used Linux exclusively on my computers.  Listen, I'm not saying it's not an issue (again, the issue is distro agnostic...they all suffer from this). I'm saying that now that we know it's an issue, everyone needs to work together to fix it, instead of passing on the blame.

The bug has been known for at least two years, it was reported 2006-09-09.

According to the bugreport, Suse and Debian (possibly more distros) has fixed the bug.

There is a number of possible fixes in the bugreport.
Here is one of the better:

> I'm highly in favor of the blacklist approach used by Novell/openSUSE as well. It tracks different laptop/hard disk combinations and knows exactly which apm value (254/255) fixes the problem for each entry. The storage-fixup script was written and is maintained by kernel developer Tejun Heo by the way, you can read more information and find the latest version of the script and config file at [http://ata.wiki.kernel.org/index.php/Known_issues](http://ata.wiki.kernel.org/index.php/Known_issues)

IMHO there is no reason not to fix this bug now, if Debian has fixed the bug it should be possible to fix in Ubuntu too?

---

### Post by ThrobbingBrain66 on 2008-09-28
Fair enough.  If that's the case, I am curious too as to why the fix hasn't been incorperated into Ubuntu.

---

### Post by jespdj on 2008-09-28
> **psyke83 said:**
> Have you used Windows much? I use Linux and Windows on a daily basis, and I can attest that Linux (and thus Ubuntu) is much more disk-intensive. With the minimum necessary processes and daemons running, Ubuntu seems to write to disk every five seconds, whilst Windows XP (when properly configured without all the associated junkware) is capable of keeping the disk idle for long periods.

To be honest I would be inclined to believe that it's Ubuntu's "fault" (though in reality, it's the hard-drive manufacturer's fault for choosing poor defaults).
Well, have you used Windows **Vista**? On Vista, the harddisk is constantly active, even when you're not using the computer - much more so than on Ubuntu.

It doesn't matter whose "fault" the load cycle problem is. Even if it's caused by computer BIOS or harddisk firmware writers that doesn't mean that Ubuntu developers should not include a workaround or fix for the problem. It's already known that the problem can be worked around / fixed, it would be strange if Ubuntu didn't include the workaround just because the problem isn't caused by Ubuntu.

---

### Post by lavinog on 2008-09-28
I hate to turn this thread into the load cycle thread:
In that 30+ page thread, no one was able to show proof that the load cycles caused by ubuntu were actually excessive enough to damage a laptop hard drive.
Hard drive manufacturers state limits on their smart monitoring firmware, but exceeding those limits do not actually mean that failure is imminent.


As for the OP: Have you filled out any bug reports?

---

### Post by Luke has no name on 2008-09-28
> **lavinog said:**
> I hate to turn this thread into the load cycle thread:
In that 30+ page thread, no one was able to show proof that the load cycles caused by ubuntu were actually excessive enough to damage a laptop hard drive.
Hard drive manufacturers state limits on their smart monitoring firmware, but exceeding those limits do not actually mean that failure is imminent.


As for the OP: Have you filled out any bug reports?

Admittedly, I haven't. I know the hard drive bug is documented, and I've complained on freenode about the gnome-logout thing. I should fill out a fix-request for gnome-logout, and again, I've seen a good amount of complaints about flash in FF on Ibex, so I assume a bugs is out on that.

---

### Post by Delvien on 2008-09-30
> **Luke has no name said:**
> Firefox and flash have really been broken on Intrepid, and one of the most critical bugs in the distro wasn't (hasn't yet been) fixed (the ACPI / laptop hard drive killing bug).

The only things I wanted out of Intrepid was a new network manager, better suspend, and a few other things. I don't know what I'm going to do, but this web browser is getting SOOOOO bogged down, it's ridiculous. Wireless N support isn't in hardy, and suspend doesn't work well either, but I don't know if that functionality is enough to keep me on Ibex when I can't get sound out of flash, or browse facebook without the browser crapping out.

Oh, and the gnome-logout screen wasn't fixed on time, so the shutdown menu is not clean and concise as it was in hardy.

This release is in ALPHA, and is going to be buggy. If you don't like it now, wait until its finished and ready for release.. 

I don't really know what you expect. You have to be patient, and you have to wait for things to be fixed/tested before posting a complaint. 

If you arent testing things and helping the community / devs with bug reports, then you have no business using an alpha phase release.

---

