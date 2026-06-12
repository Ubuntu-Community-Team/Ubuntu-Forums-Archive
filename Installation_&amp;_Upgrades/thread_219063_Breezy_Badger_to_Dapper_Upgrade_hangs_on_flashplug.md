---
title: "Breezy Badger to Dapper Upgrade hangs on flashplugin-nonfree"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by gatorbyte80 on 2006-07-19
So, as far as I can tell all of my updates downloaded successfully during the system update using the Ubuntu Update Manager.  Things looked great until I reached the flashplugin-nonfree installation, and I'm not exactly sure what's wrong there, but it's been hanging indefinitely for a good 30 minutes now, and I suspect that as long as I let it be, it will do just that - hang.  I can't tell from the outside what's happening, but top says that the thread is sleeping I believe (that is what 'S' stands for, isn't it?)  Previously I killed the child thread, labeled "update-flashplu" in top, and the update process went zombie.  So I restarted my computer, tried restarting the update, which is a bit of a pain, and found that I needed to run "dpkg --configure -a" to resume the process.  All of the packages up to the flashplugin install have no problems, and I bet that once I get past the flashplugin install, things will work great again.

So ultimately, I would like to know if there is a way to remove that package from the list of things to install, now that I've already added it, or if there is something that I might need to change somewhere to make the installer for flashplugin work.

Any advice would be greatly appreciated.  It should be simple, and yet I don't see the solution on my own.  Thanks,

Nathan

---

### Post by gatorbyte80 on 2006-07-19
Ooh I didn't know this, but I went to stop the entire process by hitting ^C, and I jumped right over the flashplugin process.  I guess I'll just need to install it manually later.

thanks,

Nathan

---

