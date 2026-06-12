---
title: "Need 9.04+ java libraries on 8.04 install"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by fr4ncium on 2010-07-19
edit: please read the second post, the problem has changed quite a bit, but maybe this is useful background information

I'm about at my wits end here. I'm trying to get some software developed on Ubuntu 9.04+ to run on some Dell XPS machines. Unfortunately, from my personal experience and many  google searches, these have a myriad of problems getting ubuntu installed on them and I was only successful when using the alternate install disk for 8.04.. The problem at this point is now I need libraries that were only available in 9.04+ in 8.04. Specifically, the java libraries commons-math and jai-imageio. Can someone point me in the right direction? I've tried downloading the files I need from 9.04+ repositories but either
a) it installs, but I still can't verify it is going to work because other missing library errors are blocking compilation
b) it can't install because I'm missing other dependencies, which will take forever to track down and download individually.

If you need more info let me know. Thanks!

---

### Post by fr4ncium on 2010-07-19
OK, turns out the bug I was getting when upgrading from 8.04 to 10.04 was actually trivial to fix (uuid harddrive identification bug). So I'm sitting here with two 10.04 installs on Dell XPS 730s. One is running its installation just fine. The other complains about "**SRST failed (errno=-16)"** on various ata sources and sometimes says that /dev/sda5 does not exist and dumps to busybox. If I exit busybox I land in the ubuntu login, which works, but then I have no cd drive, etc. I added root delay, and now the busybox step is gone (though it still complains about various ata sources during loading). The weird part is that if I switch the harddrives of the two computers, the one that was booting fine still boots fine, and the one that was complaining about ata sources still complains about ata sources. Any ideas?

---

### Post by fr4ncium on 2010-07-19
More updates.

OK, so looking at the console output during the load sequence, after putting the rootdelay in there the only thing it complains about is ata_ not being ready, where ata_ is what the dvd drive is hooked up to (I've tried a couple different sata ports and cables). Eventually it gives up and limits it to 1.5GBps. I don't need the dvd drive now that I figured out how to turn off the stupid install upgrades message that wants me to insert my install disk, but I'm still curious what the heck is going on. The machines do have the same dvd drive.

edit: Should have waited a minute to post this. Now that I disabled the cd as an upgrade source, it says I am all up to date. When the cd was still a source it said I had one upgrade - something about upgrades to console, if I remember correctly. Totally confused but happy the machine is finally running....sorta

edit2: Stupid mistake, the update in question was still there, I was just looking at the wrong ubuntu install (I have two machines hooked up to one monitor). Update worked just fine though once I turned off the cd as a source.

---

