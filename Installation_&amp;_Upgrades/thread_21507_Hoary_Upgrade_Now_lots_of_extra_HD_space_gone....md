---
title: "Hoary Upgrade: Now lots of extra HD space gone..."
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by wernst on 2005-03-22
All,

So I updated from Warty to Hoary. Things are generally working fine, but...

There's now 600 MB of new files on my Linux partition compared to Warty. That's basically one whole CD's worth of files. Since my Linix parititon is only 5 GB, that's a fairly significant loss of space.

I am assuming that lots of the .deb files from Warty are still hiding out somewhere, taking up space.

Can anyone offer me pointers for clearing out some of that stuff so I can get some more space back?

-Warr

---

### Post by underworld on 2005-03-22
Hello,


Apt-get, synaptic or any other package management tool do download the *.deb files to /var/cache/apt/archives.
You can remove them with the command "sudo apt-get clean". This could give you back some space ;)


Greetings,
Daniel

---

### Post by wernst on 2005-03-22
Brilliant!

That worked, changing my free space from 1.3 GB to 2.1GB, which is actually more space than I had before (I guess I had some old packages there from before).

Thanks very much.

-Warr

---

