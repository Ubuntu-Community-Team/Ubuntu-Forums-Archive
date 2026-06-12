---
title: "problem with ttf-mscorefonts-installer"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by rolandpish on 2009-11-14
Hello. 
I recently installed Karmic Koala and I'm having some issues with ttf-mscorefonts-installer. It finishes with this:

ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now, every apt-get install that I execute, tries to install again ttf-mscorefonts-installer and it's very annoying. Is there some way to cancel this "pending" install and try to install this package later?
I'm finding some way to "clean" the installation to avoid trying to reinstall this mscorefonts package each time I use synaptic or apt-get.

Thanks in advance

---

### Post by Maerwyn on 2009-11-15
I'm having this exact same problem and I don't know what to do about it. I'm also using Karmic Koala, which is a recent install. I tried using the command apt-get upgrade and it isn't able to install any updates due to the  mscorefont problem. I noticed that some of the error messages have something to do with it not being able to resolve the host downloads.sourceforge.com. 

Does anyone have any suggestions on how to handle this?

---

### Post by Wilzon on 2009-11-15
Hey 
I m from egypt...
this is my very first post to any forum  site :D
i m a new user of ubuntu and i like it alot 
i had the same issue with the msttfcorefonts-installer

luckily i fixed it !!!
i installed ubuntu tweak when i first installed karmic and i used it to install ubuntu restricted extras
that's when the problem begun so i easily used ubuntu tweak to clean all the packages first then unuinstalled the restricted extras... 
and now i think my karmic is working fine 

i hope this is useful for you 
good luck

---

### Post by Maerwyn on 2009-11-15
I tried a few things this morning: 

I ran "aptitude clean" and "aptitude autoclean". I also ran "apt-get update". None of this helped with the problem. 

I ran, once again, "apt-get upgrade" and paid more attention to the output. I won't paste all of it because it is a lot of the same kind of stuff and it goes on forever...that being said there's a lot of stuff that looks like this: 
---
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-15 12:54:01--  [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving cdnetworks-us-2.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `cdnetworks-us-2.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
---

What I find interesting is the checksum mismatch warning and the "no such file or directory" listing. These are different from the others and indicate, to me, that the problem is on the host's end. 

I think that, until the host situation is resolved, there is nothing I can do. Does anyone know how I can notify the "Proper Authorities"? Does this call for a bug report or something else? Am I wrong in my assumptions? Your help is greatly appreciated.

---

### Post by rolandpish on 2009-11-19
Ok, the problem is solved now.
Basically, the installer was able to download the packages and installation of mscorefonts finished successfully.

Even though, I would like to know how to "clean" those unsuccessful or interrupted installations.

Regards

---

