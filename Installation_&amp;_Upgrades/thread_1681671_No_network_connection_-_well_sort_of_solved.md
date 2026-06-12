---
title: "No network connection - well sort of solved"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by David1001R on 2011-02-04
Been using linux variations for sometime, mostly to experiment with.

I'm contributing this for those individuals that hit this truely rare bug.

This is a real oddity.  Wiped my external drive which had Ubuntu 10.04 and several previous versions, so that I could do some work with Windows 7. All was going well, had Windows 7 installed, Fedora 14 installed and OpenSuse 11 installed, just for fun.  All working, all had internet access.

Installed Ubuntu 10.10, no internet connection, but the LiveCD worked and had internet access. Dumped 10.10. Installed Ubuntu 10.04, no internet connection, again the LiveCD had worked, and the previous installation had been working (same cd).

I must have spent a weeks worth of evenings reading threads and trying different possibilities. Followed threads about Windows 7 vs. Ubuntu 10 breaking each other. Howto manually build up a network connection, and so on.

As an experiment I did an install of Wubi Ubuntu 10.04 in Windows 7 and it worked fine, networking was fine. Ok this is weird.

It wasn't until I specifically looked for problems with the Intel 82566DM-2 that I got some where. A bug had been reported, that in one kernel version it worked, but in the next version it wasn't, no network connection.

I tried several more reinstalls after this and checked the kernel numbers. Low and behold I started installing from a CD that was 2.6.32-24-generic, and finished the install at 2.6.32-27-generic. I ran this process again and noted network traffic during the install.  The installer progress messages do say that it is going on the internet and getting files, but its not like I had been reading these messages before.

During a Wubi install of Ubuntu 10.04 you are asked if you wish to do updates while installing, during a LiveCD install you are not, or at least its not obvious to me.  I by default don't do updates until after everything is working.

The solution is painfully simple, disconnect the computer from the internet before installing.  When done, I now have a working installation of Ubuntu 10.04.

Before doing anything more, customizing or additional software installs, I ran Update Manager and let it do its thing. Voila the system was updated to 2.6.32-27-generic, and I had a network connection and access to the internet.  I'm now up to 2.6.32-28-generic without issue.

Sorry if this seemed verbose, but it took a long time for me to find the solution, I felt it needed a good storyline to do my efforts justice.

Regards

David1001R

---

### Post by kroon78 on 2011-02-04
Fantastic write up!

---

### Post by David1001R on 2011-02-04
Thank you very much.

I had considered reporting it as a bug, but that process seemed to convoluted for the limited results. I'm not sure why, but the search engines don't seem to produce much in the way of useful results from the bug reporting systems.  The bug reference I found was in an email quoted on an internet webmail hosting site, so far removed as to be almost unrepeatable in a search.

In the end, other people may actually see this in their search results and be able to use it.

Best

David

---

