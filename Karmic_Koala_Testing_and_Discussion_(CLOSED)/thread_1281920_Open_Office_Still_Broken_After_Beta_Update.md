---
title: "Open Office Still Broken After Beta Update"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NormanFLinux on 2009-10-03
After the beta update, Open Office is still broken. Its still the splash screen coming up and then shutting down.

Looks like the bug still has not been fixed and this is a known issue in Karmic where all instances of Open Office die after launch.

---

### Post by Longinus00 on 2009-10-03
Mine works... I've never even heard of a problem with OO in karmic before this post.

---

### Post by nanog on 2009-10-03
Just update again or --purge and update. There have been a ton of dependency errors with open-office.

---

### Post by NormanFLinux on 2009-10-03
The bug is a javaldx failed error. Does any one know what causes OOO to shut down?

---

### Post by Wise Ferret on 2009-10-03
Back up your ~/.openoffice.org/, ~/.openoffice.org2/ and ~/.openoffice.org3/ folders, then delete them. They may have become corrupt.

---

### Post by NormanFLinux on 2009-10-03
where do i find the open office.org 3 folders to delete?

---

### Post by forumache on 2009-10-04
> **NormanFLinux said:**
> After the beta update, Open Office is still broken. Its still the splash screen coming up and then shutting down.

Looks like the bug still has not been fixed and this is a known issue in Karmic where all instances of Open Office die after launch.

Here it's working.

You say it is a known bug, but please provide the link to it in Launchpad where all the bugs are stored. Thanks.

---

### Post by joepotter on 2009-10-04
I use openoffice all the time. All of it is important to my work as a teacher. It has worked in Ubuntu since the beginning or I would junk Ubuntu and go back to Debian.

That said, it may not work at your site. I would completely remove the entire openoffice and then make sure I removed .openoffice.org (rm -rf .openoffice.org). It is often the dot files that can mess you up.

After re-installing the package you should be up and running just fine. If not, something is seriously wrong with the install of Ubutu at your location.

---

### Post by NormanFLinux on 2009-10-04
I completely removed Open Office. I reinstalled Writer and the same error returned. The thing is - all my other applications run just fine. It appears to just be an issue with Open Office in Karmic.

---

### Post by NormanFLinux on 2009-10-04
Bug #417009. Its been reported to happen on armel but I have Intel Atom. Launching OOO graphically shuts down the splash screen after a few minutes.

On the command line, I get this error message:

javaldx failed!

terminate called after throwing an instance of 'com::sun::star::ucb::InteractiveAugmentedIOException'

Uninstalling and reinstalling Open Office does not resolve the issue. No other applications in Karmic appear affected.

---

### Post by forumache on 2009-10-04
try downloading and launching a java program.
maybe the problem is with java (don't know why, just guessing)

---

### Post by dino99 on 2009-10-04
> **NormanFLinux said:**
> After the beta update, Open Office is still broken. Its still the splash screen coming up and then shutting down.

Looks like the bug still has not been fixed and this is a known issue in Karmic where all instances of Open Office die after launch.

which system have you: 32 64 server ... ?
which java is installed: sun or else ?
is all the needed java packages installed ?

what return: sudo aptitude install -f ?

Look at logs for related errors.

---

### Post by NormanFLinux on 2009-10-04
I have 32 bit Atom Intel processor. Kubuntu Netbook Edition on a Dell Mini 10.

I have Sun Java 6 JRE and the related plug-in installed. Its like it doesn't see java even though its present.

It does run in sudo on the command line but dies in GUI and regular mode CLI interface.

---

### Post by NormanFLinux on 2009-10-04
I was finally able to get Open Office working by wiping the Alpha and installing the Beta. Everything works now, including Open Office, One problem now listed as solved.

---

