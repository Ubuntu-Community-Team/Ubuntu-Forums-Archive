---
title: "Reinstalling from Older Live CD..."
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by Valkyr333 on 2011-04-21
Hi,

I'm preparing to reinstall Ubuntu (actually, install it as a partition instead of a Wubi Install) but my Live CD was created from the disc image file that the Ubuntu site gave before the changes in Grub happened recently. My question is, will I need to make a new Live CD with an updated Disc Image, or is it likely that the old one will still install/fetch the right stuff?

Thanks,

-Val

---

### Post by mikewhatever on 2011-04-21
What 'right stuff'? The files needed to be installed are on the cd. Also, can you be a little less vague about the version of the live cd. ;)

---

### Post by Valkyr333 on 2011-04-21
Right, sorry. By "right stuff," I mean a working/current version of the Grub software and all the things with which it works in order to run the system. When Grub was changed/updated from what I was using when I installed Lucid Lynx from the same version as I have on that live CD, suddenly I couldn't log into Ubuntu at all (started [this thread]("http://ubuntuforums.org/showthread.php?t=1710380") to figure it out) but ended up uninstalling the Wubi from my Windows in favor of re-doing it with a proper partition install (I didn't know the difference  when I installed it the first time.) What I don't know is, will installing Lucid Lynx via a Live CD created before the Grub changes produce the same problems booting in Ubuntu/Kubuntu as I was having before? Maybe this is a "windows mindset" problem, but if the CD contains an outdated version of the software required, would using that CD not just give me the same or similar trouble?

I can create another, more current Live CD if I really need to, but it will require buying discs, figuring out how to do the disc image file thing since my setup has changed since I last did it, etc. so I'm trying to see if I can spare myself the trouble.

---

### Post by mikewhatever on 2011-04-21
Thank you for clarifying. Most of the packages on 10.04 CD or in the repository are not the latest version, or, as some may say, outdated. That said, they do receive maintenance and bug fixes. Ubuntu's LTSs are somewhat similar to Debian stable releases, where the emphasis is on stability, rather then the latest and greatest software.
On the other hand, the problem you've experienced with the wubi installation may have been wubi, and not grub, related.
In short, think the existing cd should do just fine.

---

### Post by Valkyr333 on 2011-04-26
Okay, thanks. I'm going to try reinstalling it. I'll leave this thread open until I get it done properly.

---

