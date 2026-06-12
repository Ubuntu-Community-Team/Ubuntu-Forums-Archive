---
title: "Update manager/software centre reporting sources as untrusted."
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by ezebe on 2011-01-25
Hi, been using ubuntu a few years but my understanding of packages/repositories/sources is patchy at best...

When I try and update, or install a new program (gtkpod) update manager/software centre tells me the sources are untrusted for the apps concerned (libgpod-common libgpod4 ttf-droid ttf-umefont etc), but does not give me the name/location of the source or allow me to trust them, only a cancel button, which is very frustrating.

I have been able to install the "important security updates" no problems.
All boxes in settings form are ticked.

I had a bit of a mare yesterday, filling my hard disk to <4kb space remaining, as some movies I thought emptied from the recycle bin had not actually gone.  Have sorted this now by deleting them properly, but I think this damaged my keyring (I had to re-enter the password once after logging in) and also somehow wiped my evolution settings, though all my sent messages etc were there when i re-entered settings via the wizard.

Is this the cause? What do I add to my trusted sources list to allow the installation, how can I manually find out the source for a given package?

Any advice would be greatly appreciated!!

---

### Post by ezebe on 2011-01-25
the apt-get update command output ends:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 4EA3A911D48B8E25 Launchpad PPA for Paul McEnery
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)

---

