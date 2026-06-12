---
title: "Will Ubuntu support my system:"
date: 2018-04-11
forum: Installation &amp; Upgrades
---

### Post by kiran45 on 2018-04-11
Hey guys i have a old system and i run windows 8.1 i know that i have 1.3 GB of RAM and i have no idea how it runs smoothly windows 8.1, So i wanted to upgrade to Linux Distributor so i wanted Ubuntu! Will Ubuntu 17.10 support a 1.3GB RAM PC?

---

### Post by TheFu on 2018-04-11
Welcome to the forums.

Answer - probably, but can't tell from the information provided.  Low RAM systems should stay with Lubuntu or Xubuntu.  Get the ISOs, create either optical or flash media using the correct tools.  Then TRY IT!  See what works and what doesn't. Common things to try;
* audio, music playback,
* youtube, other videos,
* wifi networking
* wired networking
* graphics resolutions, 2nd and 3rd monitors.
Running from flash storage or a DVD/CDROM won't harm the existing OS, provided you "Try Ubuntu" only.

Without knowing all the different parts of the system, nobody could possibly say if it will work or not, but in general, if Windows runs, so will Linux. If it is a laptop, google for the {specific model} and "ubuntu install" to see if special steps are needed.  

Before attempting an install, be certain to make a 100% know-you-can-restore backup of anything you cannot lose.  Sometimes, the install process breaks existing Windows.  Sometimes it wipes Windows due to user error. This is more common than people generally understand.  The answer to questions and other choices made during the install process really do matter.

Be certain you have 15+G of available storage and the ability to have *at least* 2 more partitions before beginning.  If you need help with that, download the 16.04 Lubuntu ISO and "Try Lubuntu" and run this command in a terminal, posting the output back here:
**sudo parted -l**  <-- that is an el, not an I or 1.

---

