---
title: "Thunderbird won't start after Dapper-&gt; Heron upgrade"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by tomWright on 2008-06-15
Just upgraded from Dapper to Heron.
HP ZD8000, dual boot with XP. 4 drive partitions: WinXP, Ubuntu, Swap, Shared Fat32

After upgrade Thunderbird will not start.
Firefox starts, and even found the shared bookmarks file on the Fat32 partition that both Win and Ubuntu versions use. Thunderbird was set up in a similar way, with mail and account folders in the shared partition so that I can read and send mail whether I am in Win or Ubuntu.

When Heron first booted, the icon for Thunderbird was blank. I was able to change it, but when I try to start it, I get this error:

Could not launch application
Failed to execute child process "mozilla-thunderbird" (No such file or directory)

I reinstalled using Synaptic, but no change.

Ideas?
:confused:

---

### Post by tomWright on 2008-06-15
Figured it out. The icon on the panel was pointing to the wrong place. Hence the message.

I uninstalled the transition package and deleted the icon from the panel. 

THen added it back using the "add to panel' utility and choosing Application Launcher and then Internet and selecting Thunderbird from there.

It opens now, and finds all the mail folders and acct settings and will download email.

So it was just a ghost from the Dapper install.

---

