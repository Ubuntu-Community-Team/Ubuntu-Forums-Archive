---
title: "Installing an older version of gcc"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by wastingthehours on 2006-11-13
Hi, I'm following this tutorial ([http://ubuntuforums.org/showthread.php?t=39513]("http://ubuntuforums.org/showthread.php?t=39513")) on how to run Windows programs in Ubuntu.  It's written for the Hoary version, while I'm using the Edgy version.  Everything works until I get to the part where I have to compile qemu.  It says my version of gcc was 4.x and I need to use version 3.x.  How do I install an older version of gcc.  I tried using apt-get to remove 4.x and install 3.x but now gcc doesn't work at all?  Thanks for the help!

---

### Post by jpkotta on 2006-11-13
You can install several gccs along side each other.  Only one will be invoked by running 'gcc', but others can be invoked by running 'gcc-3.4' or similar.  Usually, there is a configure option ```
./configure --help
``` that sets 'CC', make this point to whatever gcc you need.  E.g., ```
./configure CC=gcc-3.4
```

But more to main problem.  You want an emulator or VM or something to run Windows programs.  If you want to use qemu, install the one from the repos, just search for it in synaptic or whatever package manager you like.  Personally, I go for Wine, and if that doesn't work, I just use VMware server.  There are howtos in the wiki (link in my sig) and this forum for how to set up these environments.  All of these are pretty different in how they work.  I recommend the respective Wikipedia articles for the similarities and differences.

---

