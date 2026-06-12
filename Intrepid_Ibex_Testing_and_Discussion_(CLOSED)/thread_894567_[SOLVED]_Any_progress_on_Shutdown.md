---
title: "[SOLVED] Any progress on Shutdown?"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-08-19
I know I read some where that when people were clicking the 'Shutdown' button that is was not working. I am still encountering that , although I have worked around that via other methods.
Has a fix been provided yet?
Thanks

---

### Post by Nullack on 2008-08-19
Best off asking upstream

---

### Post by ronacc on 2008-08-19
I checked upstream and didn't see anything that looked like it might be this so mabye it is ubuntu related .they marked my launchpad bug as a dupe of another bug that suposedly was patched but the patch either hasn't been applied yet or else didn't fix this .

---

### Post by danbuter on 2008-08-19
Shutdown works in kubuntu and xubuntu intrepid.

As for asking about upstream, why can't the ubuntu guys fix the problem and submit it to upstream? Novell and Red Hat do.

---

### Post by Nullack on 2008-08-19
Canonical is not the size of Red Hat or Novell :) They have project teams working on one thing that is larger than all of the devs in Canonical.

EDIT: Ronacc your spot on there. Sebastien clarified to me its patched by Debian / Ubuntu. He committed to fixing it before the beta.

---

### Post by taavikko on 2008-08-19
There's an workaround for the shutdown.
Logout->
Switch user-> throws you back at Login screen->
Reboot/shutdown from the menus. 

Not pretty, but works.

But eventually this bug is going to be fixed :)
2 thumbs up for all the testers and developers.

---

### Post by DougieFresh4U on 2008-08-19
> **taavikko said:**
> There's an workaround for the shutdown.
Logout->
Switch user-> throws you back at Login screen->
Reboot/shutdown from the menus. 

Not pretty, but works.

But eventually this bug is going to be fixed :)
2 thumbs up for all the testers and developers.

Thanks for all replies.
The method you show is what I have been using. Not a major problem as I am patient  and I also realize Intrepid is in development and  blah blah blah (just thought I would throw that in before some wise guy gives me the "you do know that Inteprid is..........)

---

### Post by gnomeuser on 2008-08-19
Do we have a bugreport tracking this.

Also please stop the excuse for working upstream that we lack manpower.. that is precisely a reason to work upstream, all the time, no excuses. From feature or fix concept to implementation, leverage everyones work.

---

### Post by RAOF on 2008-08-20
Yes, [this one](https://bugs.edge.launchpad.net/ubuntu/+source/consolekit/+bug/250506).  It's not an upstream bug; it's to do with consolekit/policykit integration.

---

### Post by IanW on 2008-09-02
> **taavikko said:**
> There's an workaround for the shutdown.
Logout->
Switch user-> throws you back at Login screen->
Reboot/shutdown from the menus. 

Not pretty, but works.

But eventually this bug is going to be fixed :)
2 thumbs up for all the testers and developers.

This does NOT work for me on an EeePC701. I can't even shutdown from a terminal!:(
Comments added to bug mentioned above.

---

### Post by RAOF on 2008-09-02
> **IanW said:**
> This does NOT work for me on an EeePC701. I can't even shutdown from a terminal!:(
Comments added to bug mentioned above.

You've clearly got a different problem.  Quite a strange one, really :).

What *is* the output of running 'sudo shutdown -h now'?

---

### Post by lonniehenry on 2008-09-02
User Switcher is the one that seems to work on my machine.  Add it to the panel.  It allows the user to switch easily to another user or a guest. Shows online status for empathy, allows close session, reboot and shutdown that works immediately,  I removed the logout icon.

---

### Post by scradock on 2008-09-02
> **lonniehenry said:**
> User Switcher is the one that seems to work on my machine.  Add it to the panel.  It allows the user to switch easily to another user or a guest. Shows online status for empathy, allows close session, reboot and shutdown that works immediately,  I removed the logout icon.

Yes, that one was a great step forward. 

Unfortunately, for me at least, the kernel upgrade that followed on its heels resulted in what looks like a crash during the reboot/shutdown sequence, however I initiate it, that leaves me with a screen full of crash dump and a frozen computer. Nothing to do but power off or SysRq-REISUB.

Does anyone else get this? It happens every time......

---

### Post by IanW on 2008-09-02
> **RAOF said:**
> You've clearly got a different problem.  Quite a strange one, really :).

What *is* the output of running 'sudo shutdown -h now'?

The same thing happens - OS closes down, EeePC stays powered up. :confused:

Now reported as [Bug #264072](https://bugs.edge.launchpad.net/ubuntu/+source/consolekit/+bug/264072)

Askar commented on my bug, asking if it was related to the contents of [this page](http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy).
I'm embarrased to say that this was indeed my problem. :oops:

---

### Post by olskar on 2008-09-02
> **IanW said:**
> The same thing happens - OS closes down, EeePC stays powered up. :confused:

Now reported as [Bug #264072](https://bugs.edge.launchpad.net/ubuntu/+source/consolekit/+bug/264072)

Check here:

[http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy](http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy)

---

### Post by Gina on 2008-09-02
I sometimes get that with Hardy - OS shuts down but power stays on - with my P4 desktop system.  I'd assumed it was a funny with my hardware - it is over 4 yrs old and been in use almost every day since.

---

### Post by FishRCynic on 2008-09-02
> **olskar said:**
> Check here:

[http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy](http://www.ubuntu-eee.com/index.php5?title=Fix:_The_shutdown_on_hardy)

thanks for the link olskar
the eeepc fix slightly modified
(ie replace eeepc with gateway)
finally allows my gateway p4 to shut down properly.

many thanks.

---

### Post by olskar on 2008-09-02
> **FishRCynic said:**
> thanks for the link olskar
the eeepc fix slightly modified
(ie replace eeepc with gateway)
finally allows my gateway p4 to shut down properly.

many thanks.

Glad I can help :)

---

### Post by ericy on 2008-09-02
About 'sudo shutdown -h now' not working (PC stays on, not off), I had this problem long ago (could be from Fedora, before I switched to Ubuntu) and I solved it by issuing 'sudo /sbin/init 0'. I have been using this command ever since (Easier for me to remember I guess).

I tried it on 8.10 Alpha ... 3(I think) and it still worked.

I used the same command to power off 8.10 Alpha 4(in KVM virtual machine) now and then.

---

### Post by ronacc on 2008-09-02
this has been going on sice alpha 1 and is just the kind of thing that makes people say "linux isn't ready for the desktop" . we are 2 days away from alpha 5 and things are looking a bit disheartening .

---

### Post by DavidONE on 2008-09-03
FWIW - this problem is 'solved' by issuing shutdown from [Gnome Do]("http://do.davebsd.com/").

---

### Post by cjm5229 on 2008-09-03
If you go up to the user switcher you will find options to reboot and shutdown there, under online, offline and some other stuff that should be in Pidgin, Anyway they work. I just can't figure out why they put that stuff there instead of where it belongs.:confused: Ireally have to find out what kind of Coffee they have been drinking lately, and then make sure my doesn't get any:).

---

### Post by cariboo on 2008-09-03
Shutdown does work now if you select it from the system menu, it is still not very intuitive. Who would think that the shutdown menu is under system. We still need a big shutdown button.

Jim

---

### Post by Nullack on 2008-09-03
I use the single icon gnome menu rather than the default three menu which takes up alot of panel space . For me it works nicely the logout is close to the menu open icon.

---

### Post by plun on 2008-09-03
The Shut down applet can be added to the panel, normal procedure.

It also works....:)

---

