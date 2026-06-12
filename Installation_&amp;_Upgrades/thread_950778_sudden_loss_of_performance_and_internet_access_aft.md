---
title: "sudden loss of performance and internet access after upgrading CUPS"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by gorcq on 2008-10-17
I have Ubuntu 7.10. Yesterday I upgraded CUPS using the automatic update system. Starting after that, I noticed that it was taking a startlingly long time to open any new program. On the order of 30 seconds to open gVim or 2 minutes for my browser, both of which are normally almost instantaneous.

When I did get my browser open, I discovered that internet access was very slow, and often my browser stopped with a "site not found" message. If this had not occurred at the same time as the other problem, I would have assumed that it was simply a problem with my internet connection, although wicd said I was properly connected. However, the system monitor shows that, even with all other programs turned off, something is sending out data fairly constantly to someplace.

My first thought was, I don't even use CUPS, this is a laptop. So, I went to uninstall it; but apt-get gave me a rather large list of programs that would also have to be removed, including ubuntu-desktop, so I decided not to do that. Then I restarted the computer and the problem was gone for about 15 minutes, when it returned with all the same symptoms I've described above. I killed the CUPS process with no effect.. Then it went away by itself, but returned later. So far, it always has.

Has anyone seen anything like this, or know what to do about it?

---

### Post by gorcq on 2008-10-20
Anyone?

---

