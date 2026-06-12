---
title: "Firefox won't start"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by joel@parke.ods.org on 2010-05-10
Firefox won't start following upgrade.  I have attempted to remove and reinstall anyversions of firefox I can find, but all to no help.  How can I remove all instances of firefox and reinstall?  You help is MUCH appreciated.

THANKS!

---

### Post by ddas4 on 2010-05-10
Do you have moonlight installed? If you do, then remove that and the mozilla plugin for moonlight using the synaptic pkg manager.
You should have firefox back.

---

### Post by joel@parke.ods.org on 2010-05-10
> **ddas4 said:**
> Do you have moonlight installed? If you do, then remove that and the mozilla plugin for moonlight using the synaptic pkg manager.
You should have firefox back.

Thanks for the reply - NO, I don't have moonlight installed and suspect that I have threads of old versions of firefox around.  How can I remove every trace?
THANKS!

---

### Post by Bobhuber on 2010-05-10
> **joel@parke.ods.org said:**
> Firefox won't start following upgrade.  I have attempted to remove and reinstall anyversions of firefox I can find, but all to no help.  How can I remove all instances of firefox and reinstall?  You help is MUCH appreciated.

THANKS!
It sounds like you have a corrupted profile. Go to your home directory CTRL H to see the hidden directory entries and remove the .mozilla directory.  Then go to the Synaptic package manager and remove and reinstall Firefox. This should give you a fresh install.

---

### Post by joel@parke.ods.org on 2010-05-10
Thanks for the posts and suggestions.... The problem was that I had a bad /usr/bin/firefox that was left over from an old beta (probably).  

SO I first deleted /usr/bin/firefox and attempted to reinstall firefox.  That FAILED with what I suspect is a bug:
Setting up firefox (3.6.3+nobinonly-0ubuntu4) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2

SO the solution was to creat a symlink:
sudo ln -s /usr/lib/firefox-3.6.3/firefox.sh /usr/bin/firefox

Now all is working properly!
I hope this helps someone else!

---

### Post by Arizon_Dread on 2010-07-13
> **Bobhuber said:**
> It sounds like you have a corrupted profile. Go to your home directory CTRL H to see the hidden directory entries and remove the .mozilla directory.  Then go to the Synaptic package manager and remove and reinstall Firefox. This should give you a fresh install.

I have this issue. 

My fox hangs when I launch it almost every time. What works for me is to launch it from commandline with:

firefox -P

which gives me the option to create a new profile. That starts it correctly and I'm able to run it normally most of the time, until it either hangs or I close it. On the next launch, I have to repeat the process. This is vastly annoying since all my bookmarks and addons disappear each time I make a new profile.

I also tried not installing anything. no bookmarks, no add-ons, no themes and it's the same issue.

I have tried reinstalling (with complete removal) but to no avail..

suggestions?

EDIT: SOLVED, I made a new symbolic link as stated above and it worked! 
I tried first by changing the "command" part of the firefox short cut to point directly to /usr/lib/firefox-3.6.6/firefox.sh and that worked, so I recreated the symbolic link of /usr/bin/firefox

---

### Post by Arizon_Dread on 2010-07-15
OK, so it worked for a while, now it's back to acting like a 3-year-old. :(

---

