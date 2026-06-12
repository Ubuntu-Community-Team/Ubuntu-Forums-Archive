---
title: "Ubuntu Software Center reset a purchase &quot;status&quot; after 12.04LTS to 14.04LTS Upgrade"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by pcar916 on 2014-08-26
[I]I've just completed a dual-boot (Win7) 12.04 LTS to 14.04 LTS upgrade successfully. Congratulations to the team that made a fine job of that process. It went very smoothly with two exceptions. 
[/I]
**1. **I had to reinstall VLC Player to get it to show up in the context menus (trivial... solved).
**2. **A game purchase in the Ubuntu Software Center (3rd-Party PPA) that in 12.04 showed "Remove" or "Install" buttons, shows simply a "Buy" button now. So there is no memory of my earlier purchase. 
**Note on #2: **I believe this problem happened because I had removed the game yesterday, thinking it was causing the 14.04 upgrade choice  NOT to appear on my 12.04 Upgrade Manager. Why, you ask?

Because the 14.04LTS upgrade just became  available this morning. Prior to that, the 12.10 upgrade was the  only one available, and I didn't want an incremental version on my main machine. Before anyone asks, I had the proper boxes  checked in the "Settings" menu to show all releases.

_**Questions** _
**A. **Is there a way to reset the Ubuntu Software Center entry for that game back to an "already purchased" state with a configuration change on my end?

**B.** Anyone have an idea about why the 14.04 upgrade waited  until today to show up if it wasn't because of the game removal? That's the only thing that changed.

Thanks in advance for the help

---

### Post by pcar916 on 2014-08-26
Question B... more information.

I just started to upgrade my 12.04 laptop a few minutes ago. Like the desktop machine, the Update Manager icon in the Launcher also failed to present 14.04, and showed 12.10 only.

That was until I typed "update-manager" into the terminal screen. For some reason that window showed the 14.04 upgrade instead. Now I remember doing that with the desktop. From this point on the Update Manager from the launcher also has 14.04 listed.

**A replacement for Question B. **
What was the difference between the Launcher icon and typing into the terminal with respect to this utility?

---

### Post by kostkon on 2014-08-26
It should remember your purchase. Click on buy, login if asked, and see if it will allow you to install it without buying it again.

---

### Post by pcar916 on 2014-08-27
> **kostkon said:**
> It should remember your purchase. Click on buy, login if asked, and see if it will allow you to install it without buying it again.

That's what I thought as well but it appeared to want me to buy it again. However, I've resolved it another way since the original email confirmation of the purchase was archived on another machine.  Clicking on the link inside the confirmation email took me to the vendor download page where I could download the file again. There were both tar.gz and .deb versions, although there were no INSTALL or README files detailing the installation.

I've never installed anything using either of those file-types in linux, so after a bit of rtfm-time I discovered that I could copy the .deb file into /var/cache/apt/archives. There I found the original .deb file, which was an AMD version rather than the i386 I'd just downloaded. A right-click on the original file allowed running it with the Software Center, and it installed clean. Now the Software Center is reset.

I do need to know how to do this with the command line as well. So I'll uninstall it and give it a go. Unless I'm mistaken about .deb files, it'll pull in all of the dependencies regardless of how I process it. I'm not sure yet how to make that happen (dependencies) with the tar.gz file but since this thread is technically solved, I'll do that outside of this discussion.

Thanks

---

### Post by pcar916 on 2014-08-27
deleted

---

