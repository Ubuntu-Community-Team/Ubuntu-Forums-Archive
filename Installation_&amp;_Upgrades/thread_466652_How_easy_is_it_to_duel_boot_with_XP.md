---
title: "How easy is it to duel boot with XP?"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Error47 on 2007-06-06
I want to install ubuntu on my other computer too. It has Windows XP on it. If I clear up enough space on it, I could duel boot both. My question is how easy would it be to make another partition to do this, and how easy would the process be? And If I wanted to erase ubuntu and keep windows with the full capacity of my hard drive, can I do that? One more thing, will I be able to access my Windows partition from ubuntu, to get things like video or music?

---

### Post by merlinus on 2007-06-06
Get the live cd from ubuntu.com.  That way, you can try it before installing.

It is a disk image (.iso) file, so be sure to burn it as such, not as a data disk.  Then you will be able to boot from it.

If you decide to install, be sure to back up your data, and defrag your windows partition several times.

Then you can select Install by clicking the icon on the desktop when the live cd is running.

There is a partitioning screen where you can choose Guided, and it will shrink your windows partition and use the free space for ubuntu.

If at some point you decide to go back to only windows (hopefully you will not), then you can use an open-source partitioning tool (gparted) to delete the ubuntu partitions and add that free space back to windows.

You can access your windows data from ubuntu, and by installing a driver can even write to that partition.

Good luck!

-merlin

---

