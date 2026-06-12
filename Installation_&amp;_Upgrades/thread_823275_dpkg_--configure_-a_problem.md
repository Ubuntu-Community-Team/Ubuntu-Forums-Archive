---
title: "dpkg --configure -a problem"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by chizzy7 on 2008-06-09
Hello, I have been recently having problems with the 'dpkg --configure -a' command.

It seems that when I run it, I come across a hanging while it is configure phpbb2-conf-mysql (2.0.22-3)

It hangs at the 'Creating search_time column if it doesn't exist yet...'

I have been scowering the net trying to find a fix, and have come up with nothing as of late.

Any help would be appreciated.

---

### Post by Partyboi2 on 2008-06-09
Is your problen the same mentioned in[[COLOR=Blue] this bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/phpbb2/+bug/218492")?

---

### Post by chizzy7 on 2008-06-09
> **Partyboi2 said:**
> Is your problen the same mentioned in[[COLOR=Blue] this bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/phpbb2/+bug/218492")?

Yes, but I'm having trouble understanding the methods of resolving it.

---

### Post by Partyboi2 on 2008-06-09
Looks like there has been modifications to the package, you can download the deb package from the links that are provide and double click on the downloaded file to install.

---

### Post by chizzy7 on 2008-06-10
> **Partyboi2 said:**
> Looks like there has been modifications to the package, you can download the deb package from the links that are provide and double click on the downloaded file to install.

I've tried using the .deb packages, but I get the error that I need to close other package management programs, when I do not have any opened. I closed update-manager, and everything else. I read that it happens when I need to use 'dpkg --configure -a', but I can't because it hangs in that one spot.

---

### Post by chizzy7 on 2008-06-11
Is there anyone that can help me with this?
I'm on the verge of re-installing, but I do not want to lose all the data on my server.

---

### Post by Sef on 2008-06-11
> I'm on the verge of re-installing, but I do not want to lose all the data on my server. 

Do you have a separate home partition?  If you do, you should not lose your data, but **back up** your data first before reinstalling.

---

### Post by Partyboi2 on 2008-06-11
If you don't have a seperate home partition you can follow [[COLOR=Blue]this[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") guide to create one before you reinstall ubuntu.

> but I get the error that I need to close other package management programs, when I do not have any opened.Is the message you getting this one:
> [B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

---

