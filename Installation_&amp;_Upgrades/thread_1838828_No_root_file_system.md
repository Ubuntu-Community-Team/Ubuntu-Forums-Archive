---
title: "No root file system"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by Jorjasdad on 2011-09-04
hi...so the story so far! I've used Wubi installer for Windows to download and install ubuntu. The download and installation were successful and I was asked to reboot the computer, which I did.
I then selected ubuntu at start up and to complete the installation.

This is when I received the following message;

No root file system
Please correct this from the partitioning menu

I'm running Windows 7 Ultimate on a RAID 1+0(10) setup. I've read a number of possible workarounds because of the RAID configuration that I'm using, but is there any way I can get ubuntu to install without creating or altering my RAID or partition configuration. The computer is a critical office machine which I can't afford to have down or even worse corrupted.

Any one have any ideas how to correctly install ubuntu with RAID....or failing this how do I remove ubuntu as it doesn't appear on my program list within windows?

Regards

---

### Post by Hakunka-Matata on 2011-09-04
Hi, Welcome to the forum.

The root file system partition may not have it's mount point set, or set correctly.,

Are you try/intending to run in Wubi mode?

---

### Post by Jorjasdad on 2011-09-04
...thanks for the first reply...cheers Hakunka-Matata!

I've been looking for an alternative to Windows 7 and so have set up a dual boot configuration, Windows 7 was installed first and works fine, then today installed ubuntu.

I think in answer to your question, I've used Wubi as the install manager? then just intend to boot on start up into ubuntu.

Sorry if I haven't answered your question correctly, I'm a bit out of my depth when it come to more complex dual boot configurations.

Thanks for any help you can provide.

---

### Post by Hakunka-Matata on 2011-09-04
right.  Wubi (where ubuntu is installed into Windows Environment) installs ubuntu into a virtual drive on the Windows Environment.  Wubi install is intended to offer the user a 'test drive' of ubuntu.  If you decide you like it and you want to install ubuntu onto it's own harddrive, and separate it completely from the Windows Environment, that's another ball of wax.  It's pretty much painless, and the right way to go if you're going to use ubuntu everyday.

---

### Post by bcbc on 2011-09-04
Ubuntu (with or without wubi) has an issue with fakeraid 10.

Someone wrote an article on it and linked to some bugs with workarounds, which may or may not be useful: [http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/](http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/)

There should be an Ubuntu entry in Add/Remove programs, but if not, try running \ubuntu\uninstall-ubuntu.exe (see here for more info including manual options to uninstall).

---

