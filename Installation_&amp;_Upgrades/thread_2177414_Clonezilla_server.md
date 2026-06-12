---
title: "Clonezilla server"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by Michael_Lopez on 2013-09-28
Hello -

I haven't taken a moment to search through the forums for this issue, so I'll go ahead and post a new one. Perhaps it may be answered in a different thread. If that's the case, then I would appreciate it if someone were to direct me there.

Here's my situation. I've installed Clonezilla server on Ubuntu 12.04 LTS. Clonezilla works fine after I've installed it. The trouble that I have is this: I'll shut down that machine gracefully through Ubuntu's shut down command. After say, 10 minutes, for example, I'll restart the machine. I'll start Clonezilla server after the machine's fully restarted, only to find the Clonezilla server will not distribute DHCP IP addresses, and ultimately, will not display a PxE boot screen to the client machines.

One way to fix the issue is to start the DRBLPUSH -I command, and have the program re-install. I prefer to not have to do that repeatedly. 

Is there a method/command to gracefully shutdown the clonezilla server without having to do the whole drblpush command?

---

