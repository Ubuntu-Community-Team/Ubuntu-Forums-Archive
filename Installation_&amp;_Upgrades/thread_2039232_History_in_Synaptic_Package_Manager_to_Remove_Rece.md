---
title: "History in Synaptic Package Manager to Remove Recent Packages Suspected Problem"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by rpete on 2012-08-08
Hi, after accepting recommended updates one day, the next day my keyboard no longer worked.  I did not do an upgrade, only updates.  Still have Ubuntu 10.04LTS.  I am unable to enter Synaptic Package Manager because it requires you to type the password.  I am going to attach a different keyboard and try it.  In Synaptic Package Manager, if I go to file and History can I identify the packages installed within the past week and uninstall them?

In another thread someone suggested the problem is a hardware problem, but I wanted to test whether software caused the keyboard to stop working.

Any opinions on this strategy or other possible reasons for the problem are appreciated.

Richard

---

### Post by drs305 on 2012-08-08
There would be several issues. First, if you uninstall a package it could cause more problems. What you ideally would do would be to 'roll back' to an earlier version of the suspect packages but this isn't easy to do unless you were using something (like duplicity) to back up your system. 

You would need to correctly identify the package, then might be able to go to launchpad to download and install an earlier version.

I make backups of my system from time to time just to prevent the situation you've run into. It makes it easier to recover from a bad update.

You might also go to Launchpad and look through recent bug reports to see if your issue has been reported by others (along with possible solutions). You can also look for recent forum posts.

---

### Post by rpete on 2012-08-08
Thanks Drs305.  I believe the most recent set of packages updated and listed in History will contain the suspected troublemaker.  After all, I am sure the sequence was accept recommended updates, next day no keyboard.  There were no further updates in between.  

I have heard of Duplicity. 

What is your opinion of whether it is a software or hardware problem because I've gotten both responses?  It is a Dell XPS I have had since 2008 so it may be hardware/keyboard.

---

### Post by drs305 on 2012-08-08
> What is your opinion of whether it is a software or hardware problem because I've gotten both responses? It is a Dell XPS I have had since 2008 so it may be hardware/keyboard. 

I can't really give you an informed opinion on what's to blame. I'd tend to think it was an update, as that is what has changed recently. However, components can and will fail at some point. 

Did the other keyboard work? That should probably give you a good indication. Just two days ago I thought I had a mouse failure. I was ready to reinstall from a backup but simply re-plugging the device fixed things.

In later versions of Ubuntu Duplicity (deja-dup) is easily set up to make backups. It was available in 10.04 but I don't think it was as integrated as it is now.

I personally use fsarchiver to make a backup from a terminal command, but many others use rsync and other backup solutions.

If the alternate keyboard doesn't work and you know or have a good idea which package caused the problem it might be worth it to dig up the previous version on [Launchpad]("https://launchpad.net/ubuntu").

---

### Post by rpete on 2012-08-08
Thanks again for the advice.  I have not been able to try an alternate keyboard. You said if that doesn't work and I know which package caused the problem I should try to dig up the previous version on Launchpad.  You provided the link, but could you explain in more detail what that would involve doing?  I identify the guilty package. Then I go to the launchpad site.  How do I know which is the previous version?  Do I do a search for that package?

---

### Post by drs305 on 2012-08-08
The easiest method is to see if the previous version is still available on your system. In Synaptic, highlight the package name and then from the top menu "Package". If "force version" is an option, it means the older package is still on your system and you may be able to reinstall it.

Otherwise, note the current package version or run the following command. I'm going to use *gnome-menus* as an example. On my system, it is version 3.4.0-0ubuntu1. You can check the package version in Synaptic or via this command:
```
apt-cache show gnome-menus
```

You can see the installed version and the previous version. 

Short advice: Rather than drill through the Launchpad pages, you can quickly do a Google search for the package name, deb, download and the older version number. Hopefully it will produce a result which you can download and force install.

If you find a reference in Launchpad or Ubuntuupdates,org I'd use one of them.

PLEASE NOTE: This is a pretty poor solution to your issue, as there may be multiple dependency issues. If your issue is really with a package, there is a good chance others are having the same problem and the issue will be fixed in a new update. Since I don't know what package is causing your issue I can't comment on its status.

---

