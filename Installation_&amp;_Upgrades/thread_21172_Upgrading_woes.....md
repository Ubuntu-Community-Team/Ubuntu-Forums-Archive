---
title: "Upgrading woes...."
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by spacemonkey on 2005-03-20
So I got excited and decided to upgrade to Hoary.  I changed my apt sources from warty to hoary and did apt-get update, then apt-get dist-upgrade, it took a few hours to download everything, then it installed it all.  When I came back, the only resolution    I could get was 1024 by 768, and there were tons of programs listed in Applications.  I tried to fix the resolution, and the x-server screwed up and wouldn't start anymore.  I reinstalled warty because I really needed my computer back.  I spent the whole day setting everything up again.

Next I decided to download the hoary preview install cd, and install to a different partition, just to test it out.  It installed great, everything seems to be working.  There are the usual number of programs in the applications menu, not tons like when I upgraded.  I'm planning on waiting until the official release to upgrade warty again.  My question is this however.  How should I upgrade?  changing the apt sources seemed easiest, but things went crazy last time.  Will the official release work out better?

---

### Post by Gary Powers on 2005-03-20
I've done both methods of upgrading to Hoary and they both worked well.  Regarding the problems using the repositorities as path to upgrade, sounds like maybe there is something wrong with your sources list.  I don't remember all that many programs downloading.

Gary

---

### Post by spacemonkey on 2005-03-20
You say both methods?  What is the other method?  Is there a way to upgrade from the CD?

Also, the only sources I've got on my apt sources are the default ones, and the ones listed on ubuntuguide.org.

---

### Post by Gary Powers on 2005-03-20
Well, originally I upgraded a Warty installation by changing repositories and doing a dist-upgrade.  Worked without problem.

When the preview for Hoary was released, I loaded that on a different box with excellent results.

Gary

---

### Post by spacemonkey on 2005-03-20
Oh, ok.  Well my apt sources are identical to the sources shown on ubuntuguide.org.
That includes:
warty main restricted
warty universe
warty-security main restricted
warty multiverse
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
warty-backports main universe

I assume to upgrade, I should change all instances of warty to hoary, and perhaps remove the backports source from the list?  Any other instructions of what to do for the upgrade?

I haven't really installed that many things from apt.  I did install kdelibs for a kde program I wanted to compile and run, as well as gkrellm, nvidia drivers, and that's pretty much it.

---

### Post by trinoo on 2005-03-20
use "sudo dpkg-reconfigure xserver-xorg" command to fix the resolution. i solved mine  :)

---

### Post by spacemonkey on 2005-03-21
Anyone have any explanations as to why it loaded tons of programs into my applications menu....almost like it decided to install all the programs in the repositories.  It took over two hours just to download everything when I upgraded, on a highspeed connection.  Any explanations, and ways to prevent it next time?

---

