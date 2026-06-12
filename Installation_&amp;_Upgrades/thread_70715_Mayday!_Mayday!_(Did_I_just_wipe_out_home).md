---
title: "Mayday! Mayday! (Did I just wipe out /home?)"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by twoseids on 2005-09-30
I am in the process of cutting a second slice off my Windows partition to add it to Ubuntu. I currently only have one Linux partition, which is housing / and /home.  I just found out this is not advisable, so I was planning on making this new partition /home.  I have a buddy who, via e-mail, is helping me through the process.  My most recent step was to make a /tmp/newhome directory, where I was going to put my /home files until the new partition was ready to be "moved into."  I had some errors when trying to do that, so I e-mailed my friend and went to bed.
This morning, I can't log into KDE.  I'm at the login screen, but it either doesn't recognize my password or is ignoring my attempt (no error message).  When I select Gnome session, same thing.  When I select KDE session (as opposed to leaving it default), then I get some error messages, as follows:
> There was an error setting up inter-process communications for KDE. The message returned by the system was:
Could not read network connection list. //.DCOPserver_eric_0
Please check that the "dcopserver" program is running!
And then...
> Will not save configuration.
Configuration file "//.kde/share/config/ksplashrc" not writable
Configuration file "//.kde/share/config/kdeglobals" not writable
Please contact your system administrator
And then...
> The following installation problem was detected while trying to start KDE:
No write access to $HOME directory (/).
KDE is unable to start.
And finally...
> Could not start ksmserver. Check your installation.
And then it brings me back to the KDE login screen.
I was able to do the console login, so I now have a command line:
> eric@eric:/$
When I went to the /home directory and typed **ls**, I got nothing.  This can't be good.

So did I totally hose my /home directory? Is there any hope? If there isn't, I guess I can at least merge those two partitions into one, reinstall Ubuntu and partition it the right way from the start, huh?

---

### Post by aysiu on 2005-09-30
I don't know what happened, but if you use a live recovery CD (not Ubuntu's live CD--something more like Knoppix), you can probably recover the data before you reformat, if it comes to that.

---

### Post by twoseids on 2005-10-01
[QUOTE=aysiu]I don't know what happened, but if you use a live recovery CD (not Ubuntu's live CD--something more like Knoppix), you can probably recover the data before you reformat, if it comes to that.[/QUOTE]
Is Knoppix a distro too?  Sorry, I'm a total noob.

Can you give me a URL where I can download a live recovery CD?

---

### Post by aysiu on 2005-10-01
[QUOTE=twoseids]Is Knoppix a distro too?  Sorry, I'm a total noob.

Can you give me a URL where I can download a live recovery CD?[/QUOTE] Yes, Knoppix is a distro, too. You can go here to get a bunch of mirror downloads:

[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)

There are two kinds of Knoppix--DVD and CD. If you prefer a faster download, you may want to use the CD--it's fully functional. Also, if you don't speak German, you may want to avoid the ISOs that end in DE. The ones that end in EN are the English versions.

When Knoppix boots up, it'll immediately place all your partitions on the hard drive. When you click on the drives, they will mount and open. You can then search around and find your /home data and back it up.

---

### Post by twoseids on 2005-10-01
Okay, I'll give it a shot.  Now may I ask a basic question?  What do I do?  I've agreed to the Terms and Conditions, and now I'm looking at ftp index page, with all kinds of files listed there.  ([ftp://csociety-ftp.ecn.purdue.edu/pub/knoppix/](ftp://csociety-ftp.ecn.purdue.edu/pub/knoppix/))

Do I have to select all of them and download them individually?  And the folders too?  And then burn them onto a CD?  Sorry, I've never done this off the web before - all I've used is a ready-made CD.

---

### Post by aysiu on 2005-10-01
[QUOTE=twoseids]Okay, I'll give it a shot.  Now may I ask a basic question?  What do I do?  I've agreed to the Terms and Conditions, and now I'm looking at ftp index page, with all kinds of files listed there.  ([ftp://csociety-ftp.ecn.purdue.edu/pub/knoppix/](ftp://csociety-ftp.ecn.purdue.edu/pub/knoppix/))[/quote] If you prefer English the German, download the one called *KNOPPIX_V3.9-2005-05-27-EN.iso*. That's the only one you need to download.

> 
Do I have to select all of them and download them individually?  And the folders too?  And then burn them onto a CD?  Sorry, I've never done this off the web before - all I've used is a ready-made CD. You then burn it as a CD image. What CD burning software do you have available? Nero? Easy CD Creator? K3B? Gnomebaker? All of these have the ability to burn as disk image--this is different from burning as data.

---

### Post by twoseids on 2005-10-01
PROBLEM SOLVED - WITHOUT DOWNLOADING A NEW DISTRO

Since I'm a noob, whenever I get a solution to a problem I post about here, I like to post the solution in case future noobs have the same problem.  Anyway, here's what I did:

1.  Login as root.  (Or just type "sudo" before everything below)

2.  Do "umount /home" and then do "ls /home".  You should see your OLD
user homes, which are simply "covered up" by the newly created and
mounted /home partition you built.

3.  Logout with the "exit" or "logout" command.  Try logging in 
again.  It should work normally. 

4.  Edit the /etc/fstab, and put a "#" at the beginning of the line for
your new /home partition.  This will preserve your ability to reboot and
login until we can figure out the problem.

Anyway, I'm back in my own computer, thanks to Paul my Fedora buddy for his help!

---

