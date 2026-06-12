---
title: "can't upgrade to 11.04 from 10.10"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by tlawren on 2011-06-19
I can't upgrade my Ubuntu 10.10 box to 11.04.  This is a brand new install, so I may be missing something.  (I had a 10.10 usb ready to go and I figured I could just install it and then do a release upgrade via the net.)

So far, I've tried checking for upgrades using upgrade manager, but no new releases are found.  "Normal releases" is selected under Settings->Updates->Release upgrade too. 

Additionally, I've ran sudo do-release-upgrade from the command line, but "No new releases are found" there either. 

I've also tried...
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo update-manager -c

but again, nothing!

Am I missing something?

EDIT:

sudo do-release-upgrade works now. I guess some source wasn't being found!

---

### Post by Dutch70 on 2011-06-19
Glad to see you've got it fixed & thanks for posting your solution. :KS
You can actually mark the thread "Solved" with "Thread Tools" in the upper right hand corner. Only you can do it & that will cause it to show up as solved in web searches as well, so others can find it easier.

---

### Post by nomko on 2011-06-19
Let me give you 1 advice: never do an upgrade from an existing version. This might give you trouble with conflicting files, missing files, etc. Best is to perform a fresh, clean install from zero. Takes a bit tiem, but then you don't "infect" your 11.04 installation with conflicting/older files from 10.10.

---

