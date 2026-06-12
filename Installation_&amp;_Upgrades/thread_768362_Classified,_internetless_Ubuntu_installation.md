---
title: "Classified, internetless Ubuntu installation"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by casperlingus on 2008-04-26
I am tasked with setting up Linux on a machine that has no internet and has strict security requirements.  I have done a bit of googling, but have not yet found anyone else who has done this.  Am I the only ubuntu user that's tried to use it on classified machines?  Apparently, SuSE and Fedora can do this easily, Ubuntu cannot.  I need help with the following:

1) I need to be able to enforce strong passwords, and they must be changed every 3-6 months.  This is not the same as TELLING them to pick a strong password, and TELLING them to change it.  The system must enforce it.  I got one lead on using passwdqc (libpam-passwdqc) but I'm not sure how to set it up appropriately.  I suspected maybe I'll link /usr/bin/passwd to /usr/bin/passwdqc or whatever it is.  But that doesn't solve the passwd-frequency problem...

2) I need a login banner. When the machine boots into the login screen, there must be a window that pops up with all this jargon about being arrested if you are unauthorized to use the computer and you agree to be monitored, etc.  I am pretty sure this must be a window that pops up and requires you to click "OK."  At least this is how they have it on Windows.  I might just change one of the theme backgrounds, and add the text above the login box...that *might* be sufficient.

3) I need the first computer I set up to act as a repo-server to distribute, among other things, security updates once a week.  I know this is possible, but I haven't quite figured out how to do this.  I know it will involve setting all the other computers /etc/apt/sources.list to a local server IP address, but I need to figure out the server part.  For xferring packages, I found things like apt-move and APTonCD but I'm not sure that's going to complete the server functionality.

4 (OPTIONAL)  I'd like to clone the machines once they are setup properly.  I found 
[this]("http://www.ubuntu-unleashed.com/2007/09/remaster-and-clone-your-ubuntu-install.html").  Has anyone tried this?  Any other ideas?

Long post, I know.  But I think if I can do this, I will have significant impact bringing at my office, bringing Ubuntu to a bunch of engineers who otherwise never even knew what it was.  I'm excited about this opportunity.

-Casper

---

### Post by casperlingus on 2008-05-14
Bump! 

It looks like I'll be defaulting to SuSE which already has this functionality.

---

