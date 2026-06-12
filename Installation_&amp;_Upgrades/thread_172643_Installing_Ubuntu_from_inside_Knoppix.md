---
title: "Installing Ubuntu from inside Knoppix"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by morrow0233 on 2006-05-09
I know that's a strange subject line, but there's a reason for my request.  Honest.

I volunteer for the Alameda County Computer Resource Center (accrc.org).  We take donated old computers and fix them up, then give them to schools, non-profits, low-income folks, etc.  Currently, we get a computer working, then install Linux on it, then temporarily run Parallel Knoppix on it so that it can join our cluster and run for a little while doing something CPU- and RAM-intensive.

Recently I had a crazy idea.  What if we just got the machines working, then booted them directly into Parallel Knoppix, started them off doing cluster work, then had them install Linux to the hard drive in the background?

Has anyone out there done anything like this?  It seems like it should be possible, but there's probably a whole slew of issues I haven't considered.  Basically, I'm looking for a bash script or something similar that installs Ubuntu over the network on a running Linux system.

Thanks,
Jeff Morrow

---

### Post by Dr. Nick on 2006-05-09
I have done something similar with gentoo, it is possible and not that hard when well documented. I found a link written for ubuntu detailing how to install it from within another linux system, so I assume it would work out of knoppix, here it is

[http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apcs04.html]("http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/apcs04.html")

It is step by step but I have never tried it so cant guarantee it works correctly. Your current way may be a better alternative unless you can make that link into a script, which would be cool. Unfortunately I dont know much on scripting so I wouldnt know how to do it.

Good Luck

---

### Post by morrow0233 on 2006-05-09
Ah, that looks really excellent.  Should be just what I need.  Thanks alot.

Jeff

---

