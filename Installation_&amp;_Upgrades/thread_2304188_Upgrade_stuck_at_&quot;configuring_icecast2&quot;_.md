---
title: "Upgrade stuck at &quot;configuring icecast2&quot; for 24 hours."
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by joomla1 on 2015-11-24
I started an upgrade from the previous version of Kubuntu to the most recent one, a night and a day ago. It finished downloading and yesterday morning appeared stuck at "Configuring icecast2 (amd64)" as seen here [IMG]https://imgur.com/HPpuf0u.png[/IMG]
Now my computer is still running, nothing else is stuck. Clicking show terminal does nothing. How do I continue the upgrade from here?

---

### Post by T.J. on 2015-11-25
I'm sorry to say that you probably can't.   It sounds like you found a bug.  I'm truly sorry I cannot give you better news.   I could make some suggestions as to how to attempt a recovery with apt, if you want.  Just let me know.  Before you ask, I want you to understand I make no promises.  If you are performing a dist-upgrade, attempting to recover would probably leave your system in an unusable state.  At this point, I believe you are probably better off reinstalling Ubuntu cleanly from disc rather than an upgrade.  In fact, given Ubuntu's real world track record, I never recommend in place upgrades.   


I have been using Linux for something to the tune of 18 years, and a programmer for 25+. I mention this not to demean you, but only so that you understand I have experience and I am being very serious. I always wipe and reinstall when I use Ubuntu.  I think that anyone who is not a programmer should be using only the LTS (Long Term Support) versions of Ubuntu, rather than the 6 month releases.  The 6 month releases are based on the Debian Unstable branch and are not suitable for users who do not want bugs.


Have a great evening!

---

### Post by Bucky Ball on 2015-11-25
> **T.J. said:**
> I'm sorry to say that you probably can't.   It sounds like you found a bug.  I'm truly sorry I cannot give you better news.   I could make some suggestions as to how to attempt a recovery with apt, if you want.  Just let me know.  Before you ask, I want you to understand I make no promises.  If you are performing a dist-upgrade, attempting to recover would probably leave your system in an unusable state.  At this point, I believe you are probably better off reinstalling Ubuntu cleanly from disc rather than an upgrade.  In fact, given Ubuntu's real world track record, I never recommend in place upgrades.   


I have been using Linux for something to the tune of 18 years, and a programmer for 25+. I mention this not to demean you, but only so that you understand I have experience and I am being very serious. I always wipe and reinstall when I use Ubuntu.  I think that anyone who is not a programmer should be using only the LTS (Long Term Support) versions of Ubuntu, rather than the 6 month releases.  The 6 month releases are based on the Debian Unstable branch and are not suitable for users who do not want bugs.


Have a great evening!

??? :-k

Did you install a PPA manually for icecast? If so, go to Software and Updates> Other Software and disable or remove it, reboot and tell us what happens. It appears you have a repo or an app installed that is not for 15.10. This is a very common cause of problems after and during an upgrade. Best to update the machine, get it to as vanilla as possible by disabling any manually added PPAs.

The advice to reinstall at this point is premature, sorry. It may come to that later, though, but let's consider that a last resort. :)

---

### Post by T.J. on 2015-11-25
Good afternoon. 

If you can get him/her working Bucky, I would be very interested in the particulars.  I say that completely without sarcasm. Honest. =)  I truly wish you both luck. 

The reason I said what I said is that Joomla1 mentioned he/she was upgrading from a previous version of Ubuntu when it failed.  Since that changes things such as Upstart or Systemd - depending on version, I believe that a clean reinstall is the best way to go in order to fix that and future problems that might turn up.  You don't want stale libraries on from two different versions of GLibc on the system.  Without proper care, it can cause unforeseen bugs, which then are not resolved since they can't be replicated by others.

Take care. =)

---

### Post by joomla1 on 2015-11-25
I'm quite sure I was on 15.04 and was upgrading to 15.10 Interestingly, when I try to check my version now (I still haven't restarted or attempted fixing it yet, it's still on icecast2 heh) it says I'm using using version 15.10

I've left it up mainly to get debugging details if it's still possible. Let me know if you want some specific detail.


> **T.J. said:**
> I'm sorry to say that you probably can't.   It  sounds like you found a bug.  I'm truly sorry I cannot give you better  news.   I could make some suggestions as to how to attempt a recovery  with apt, if you want.  Just let me know.  Before you ask, I want you to  understand I make no promises.  If you are performing a dist-upgrade,  attempting to recover would probably leave your system in an unusable  state.  At this point, I believe you are probably better off  reinstalling Ubuntu cleanly from disc rather than an upgrade.  In fact,  given Ubuntu's real world track record, I never recommend in place  upgrades.   


I have been using Linux for something to the tune of 18 years, and a  programmer for 25+. I mention this not to demean you, but only so that  you understand I have experience and I am being very serious. I always  wipe and reinstall when I use Ubuntu.  I think that anyone who is not a  programmer should be using only the LTS (Long Term Support) versions of  Ubuntu, rather than the 6 month releases.  The 6 month releases are  based on the Debian Unstable branch and are not suitable for users who  do not want bugs.


Have a great evening!

Heh, I am a programmer and everytime I upgrade, having hope, that this  time it will work but yeah it hasn't worked for me the last few times I  upgraded. It is for this reason that I have my home on a separate  partition and I've backed up my encryption passphrase in case everything  goes to hell.
Thanks for telling me that, I might've left the machine in limbo much longer if you hadn't confirmed it.
I'm just going to install fresh.

---

### Post by T.J. on 2015-11-26
I can't confirm anything from here, but your message did give me that impression.  I hope all goes well for you.  For the reasons above, I no longer use Ubuntu unless it is an LTS.  I give the Ubuntu community a lot of respect and leeway, but the bare fact is that 6 months is just too short a release, especially from a Debian Sid base.  Good luck. Take care.

---

### Post by joomla1 on 2015-11-27
So as an epilogue, I restarted my computer. Had to do it with a terminal command of sudo reboot.

Though things appeared stuck for a while, eventually the login screen came up! Great! Then, just to check I tried the command:

sudo dpkg --configure -a

And it looks like the upgrade resumed! It went about installing stuff for a while and came to the fateful icecast question, which reproduce below:
etting up lib32tinfo5 (5.9+20150516-2ubuntu1) ...
Setting up pam-kwallet4 (4:5.4.2-0ubuntu1) ...
Setting up libjs-sphinxdoc (1.2.3+dfsg-1ubuntu3) ...
Setting up python-webob (1.4.1-1) ...
Setting up icecast2 (2.4.2-1) ...

Configuration file '/etc/icecast2/icecast.xml'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** icecast.xml (Y/I/N/O/D/Z) [default=N] ?



So, giving it the answer Y and pressing enter, let it continue past that. A while later, everything is complete. And I reboot just in case.
The system seems fine. Sometimes it looks like the screen is frozen but Ctrl+Alt+F1 still works and eventually it gets going again.

The upgrade actually worked! So go ahead and restart if you're stuck on this. You will likely have to restart with the terminal and sudo reboot.

---

### Post by tgalati4 on 2015-11-27
An in-place upgrade will encounter some configuration issues, as you have discovered.  You have to watch the progress, because the upgrade script can't automatically answer these configuration questions.  So, for each service that you have installed and modified, expect to have a configuration file that will possibly be overwritten that will either break the service or change it in an unhelpful way.  The post-installation script normally handles this case gracefully, but not always.  

Generally, by keeping your old configuration file, you will keep your old settings for a given service (icecast2 in this case), but there may be new features in the new configuration file that will not get set and break the new version of the service.  Keep a notepad handy and make a list of all the things that are broken or not working the way you expect after an in-place upgrade.  It can take a few days to research and fix all of these regressions.

With a fresh install, you are going to have to spend a few days adding new software and services and configuring anyway.  But, at least you have a clean system and one that is perhaps easier to troubleshoot in the future.

---

