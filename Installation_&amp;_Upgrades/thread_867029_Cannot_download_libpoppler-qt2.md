---
title: "Cannot download libpoppler-qt2"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by herold on 2008-07-22
I have Ubuntu 8.04 installed on a USB hard drive that I use for running Ubuntu while leaving Windows XP unchanged on the internal hard drive on my Dell Vostro 1500 laptop.  A few days ago, I purchased a new third edition of The Official Ubuntu Book, and saw a paragraph on "Can I Switch to Kubuntu If I have Ubuntu Installed Already?" on page 275.  I used Synaptic Package Manager and found kubuntu-desktop. I selected it, and then "Mark additional required changes."  I selected Mark.  It showed "216 to install/upgrade."  I clicked Apply.  I went away while the files downloaded.  When I came back, there was a message, "Some of the packages could not be retrieved from the server(s).  Do you wish to continue, ignoring the packages?"  I clicked Yes.  "An error occured"  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-qt2_0.6.4-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-qt2_0.6.4-1ubuntu2_i386.deb)
404 Not Found [IP: 91.189.88.46 80]
I again tried marking packages to be upgraded, and it showed three (rather than the 216 when I started), kdegraphics-kfile-plugins, kubuntu-desktop, and libpoppler-qt2.  I got the same error message that it couldn't fetch libpoppler-qt2.  I tried a couple of more times, with the same result.  Evidently the libpoppler-qt2 isn't available any more.

What should I do now?  Might the missing file be available somewhere else?

---

### Post by tech0007 on 2008-07-22
Change the mirror by going to System->Administration->Software sources. Then try synaptic package manager again.

---

### Post by herold on 2008-07-22
> **tech0007 said:**
> Change the mirror by going to System->Administration->Software sources. Then try synaptic package manager again.
Thanks, it worked!  I went from the us source to the main source, and was able to download everything and install it.  I can now run either ubuntu or kubuntu, depending on the option I select on the opening screen.

---

