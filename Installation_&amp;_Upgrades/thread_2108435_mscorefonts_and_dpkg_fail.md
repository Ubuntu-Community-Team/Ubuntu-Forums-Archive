---
title: "mscorefonts and dpkg fail"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by DrSnooz on 2013-01-24
This happens consistently, every time I  install 12.04. I try to install ubuntu-restricted-extras or netflix-desktop or some other package that requires the mscorefonts package and the package locks up while trying to download the fonts:

End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.

I have to go into the terminal and dig around in the processes to kill dpkg. Dpkg returns the favor by demanding that I run "sudo dpkg --configure -a" before letting me do any more downloading. That immediately begins downloading the fonts again, which errors out and dumps me into the seventh circle of Hell, chasing my tail, performing hours of Google searches (yielding nothing of any use). I've managed to finagle my way around this problem on two different computers, but it's been more dumb-luck than skill. How, exactly, should I be obtaining these fonts in a way that won't result in a vicious circle and a lot of swearing?

Is this a SourceForge problem, or my problem? Is there a good way around this ongoing issue in Ubuntu? It's beyond exasperating.

Thanks,

---

### Post by DrSnooz on 2013-01-26
Well, after trying it a dozen times, it worked. Don't ask me why.

I've done countless installations of Windows and this was my third install of Ubuntu. I have to say that, even with this dpkg problem, I've never had an installation go so smoothly. It has always taken me several days to get everything installed and set up on my Windows machines. Then it takes weeks more as I undo all the stupid configuration choices made on my behalf by Microsoft and others (getting rid of the silly paperclip and useless toolbars, labyrinthine activations, irritating cross-promotions, etc. etc. etc.). This Ubuntu install took half the time and is ready to go right now. It installs so easily and the software is all right there in the repositories. You download it and it works. You don't have to patch up 10,000 security holes. You don't have to fight viruses constantly or find special software to neutralize all the built in trojans. It just works the way you want it to the first time. 

Three cheers for Linux!!!

---

