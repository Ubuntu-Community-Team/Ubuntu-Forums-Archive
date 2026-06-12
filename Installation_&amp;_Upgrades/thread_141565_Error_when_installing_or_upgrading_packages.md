---
title: "Error when installing or upgrading packages"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by AndyC_772 on 2006-03-08
Just tried to install today's upgrade of Mplayer, and installation failed with an error:

**E: /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: subprocess new post-removal script returned error exit status 1**

I installed Lilypond last week but no longer have any need for it, and I've already tried to remove it once. Nevertheless, I tried again (using Synaptic) and got an error telling me that I needed to manually run **dpkg --configure -a**, which I did. It finished configuring Mplayer, apparently with success.

Nevertheless, Lilypond-data is still on my system, according to the Synaptic window. So I marked it for complete removal again and hit 'apply', and got the 'successfully applied all changes' window. Expanding the terminal, however, shows that nothing has actually happened - it's empty. Closing that window brings up the error again:

**E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.**

So I did. Nothing happened.

How do I get rid of this package and stop it from causing errors every time I try to install or upgrade something?

---

### Post by Xian on 2006-03-08
Read this [THREAD](http://ubuntuforums.org/showthread.php?p=746069) for a possible solution.

---

### Post by AndyC_772 on 2006-03-10
Thanks. I sorted it eventually - though the exact commands in that thread didn't seem to work for me. What eventually did was actually very simple, though:

sudo aptitude install tetex-bin
sudo aptitude remove lilypond-data
sudo aptitude remove tetex-bin

That simple :)

---

