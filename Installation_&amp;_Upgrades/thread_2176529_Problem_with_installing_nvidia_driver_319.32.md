---
title: "Problem with installing nvidia driver 319.32"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by josh23 on 2013-09-24
My computer has crashed and won't let me get on my GUI until I get the new nvidia driver 319.32. I can't use the GUI (just reminding you) and I am stuck in the command line recovery mode. Plus every time I try to install the ppa from launchpad for the repositories for installing the driver it just gives me and error about not being able to resolve host name so can anybody help me?

If you need my specs just ask

---

### Post by Karlchen on 2013-09-24
Hello, josh23.

Boot the machine from your Ubuntu live system. - Sorry, I forgot which version you are on. But use this version. - Then run an fsck on each Ubuntu partition on your harddisk.
Once this has been accomplished successfully, try to bootup your machine normally again.
Provided this can be done, then is the right time to think about installing nvidia319.32.
And unless you are on a pretty outdated Ubuntu version, no additional PPA is needed in order to get it.
Got it for Ubuntu 12.04.3 e.g. from the normal repositories.

Cheers,
Karl

---

### Post by josh23 on 2013-09-24
I did just everything you said while using the ubuntu live system it said that the fsck was ok too. When booted up my systems normally and booted myself into recovery mode to install the nvidia driver 319.32 it still gave me the same error about not being able to locate the repositories and ppa's

Btw: I also am using ubuntu 12.04 so can you be more descriptive too

---

### Post by spacesamurai2 on 2013-09-25
How are you accessing the command line in recovery? If you boot the system in recovery mode (not the live disk, although this could also be done), you should have a menu of options (Resume, Drop to Root, etc). There should be an option to start the network, after which you could try connecting to the PPA again.

---

### Post by Karlchen on 2013-10-08
Hello, josh23.
> the fsck was ok too. Good.
> When booted up my systems normally and booted myself into recovery modeWhy would you want to boot into recovery mode?
> to install the nvidia driver 319.32This should be feasible after you have booted your machine normally, not in recovery mode.
> it still gave me the same error about not being able to locate the repositories and ppa'srecovery mode without network support? In this case, the repositories and PPAs cannot be contacted.

Cheers,
Karl

---

