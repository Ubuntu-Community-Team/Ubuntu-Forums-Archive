---
title: "Getting the installer to use a repository in my country"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by detly on 2011-10-04
I'm trying to install Ubuntu 11.04 from a USB stick created with Startup Disk Creator. I'd like to use a repository in my country (Australia) instead of in the US. Is this possible?

---

### Post by MAFoElffen on 2011-10-04
> **detly said:**
> I'm trying to install Ubuntu 11.04 from a USB stick created with Startup Disk Creator. I'd like to use a repository in my country (Australia) instead of in the US. Is this possible?
When the installer gets to the set local time and date phase, when you set it to somewhere nearest you, it also looks up and sets the local repository to you based on that decision... That is as far as I can tell...

---

### Post by detly on 2011-10-05
> **MAFoElffen said:**
> When the installer gets to the set local time and date phase, when you set it to somewhere nearest you, it also looks up and sets the local repository to you based on that decision... That is as far as I can tell...

I don't think this is correct. Firstly, it starts downloading packages before it asks me where I am. Secondly, if I expand the terminal pane, I see that it's downloading package lists from the US server. Maybe I've got this wrong, but it seems odd.

---

### Post by MAFoElffen on 2011-10-05
> **detly said:**
> I don't think this is correct. Firstly, it starts downloading packages before it asks me where I am. Secondly, if I expand the terminal pane, I see that it's downloading package lists from the US server. Maybe I've got this wrong, but it seems odd.
Wait one- booting a LiveCD to test this...

Got a way.  When you boot the LiveCD. Use try without Installing... When it Boots:

System > Synaptic Package Manger > Settings > Repositories > that will bring up the Software Sources

Look in this popup about half way down. It will say "Download from:" and have a pulldown that says "Main Server" > Click on the Pulldown > ""Other"  Wll bring up another popup tiled Choose a "Dowload Server"...  > Choose your local server > Press all the accept buttons for all the popus.

Install from the Try's GUI's "Install Ubuntu" Icon...

---

### Post by detly on 2011-10-05
> **MAFoElffen said:**
> 
System > Synaptic Package Manger > Settings > Repositories > that will bring up the Software Sources


Aha! Seems like a kinda obvious thing to try now that you say it. I'll see how that goes.

---

### Post by detly on 2011-10-05
Nope, still downloads from us.archive.ubuntu.com

---

### Post by detly on 2011-10-05
I've just gone ahead and installed anyway. Turns out the problem I thought was due to a flaky internet connection was due to my installation media.

---

