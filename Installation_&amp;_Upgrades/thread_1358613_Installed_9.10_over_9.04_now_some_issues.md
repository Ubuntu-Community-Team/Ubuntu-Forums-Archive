---
title: "Installed 9.10 over 9.04 now some issues"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by walkerx on 2009-12-18
I previously had 9.04 installed on my pc in the following layout

20GB EXT3 /
10GB SWAP
160GB EXT3 /home

On installation of 9.10 I left the settings as above, but told it to wipe just my / and swap partitions of which it done.

Installation went in and my desktop is exactly like it was under 9.04 but minus my cairo-dock.

Should I have wiped my home location or removed the old apps before upgrading

thanks

---

### Post by mikewhatever on 2009-12-18
What's the problem exactly? Please don't be vague, what do you mean by 'some issues'? Just list them, 1,2,3 ....

---

### Post by phillw on 2009-12-18
> **walkerx said:**
> I previously had 9.04 installed on my pc in the following layout

20GB EXT3 /
10GB SWAP
160GB EXT3 /home

On installation of 9.10 I left the settings as above, but told it to wipe just my / and swap partitions of which it done.

Installation went in and my desktop is exactly like it was under 9.04 but minus my cairo-dock.

Should I have wiped my home location or removed the old apps before upgrading

thanks

No, your /home should remain safe & sound. that's a good reason to keep a seperate /home.

You're swap is rather large .... You want about 1GB min or whatever your RAM is.

Your Cairo will most likely have to be re-installed as it is an application - To do so head over to [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

Regards,

Phill.

---

### Post by walkerx on 2009-12-18
Hi thanks for the replies,

Sorry for being vague (was distracted while entering the post) - the problem was I had no launchers to run any apps, the only thing had on the desktop was icon for computer, network and world of warcraft.

I created new launcher app for terminal and was able to redownload cario-dock, then realised I had forgotten to download the ati drivers.

So done all that rebooted and now fine - configured my x-fi and remembered to download the info-panel again.

I wasn't too sure on what size to set the swap so just set it to 10GB when originally installed 9.04 as got 4GB of memory and not sure how linux used the swap compared to windows.

So far everything seems to be working again, just need to re-install wine and thunderbird I think

---

### Post by phillw on 2009-12-18
> **walkerx said:**
> Hi thanks for the replies,

Sorry for being vague (was distracted while entering the post) - the problem was I had no launchers to run any apps, the only thing had on the desktop was icon for computer, network and world of warcraft.

I created new launcher app for terminal and was able to redownload cario-dock, then realised I had forgotten to download the ati drivers.

So done all that rebooted and now fine - configured my x-fi and remembered to download the info-panel again.

I wasn't too sure on what size to set the swap so just set it to 10GB when originally installed 9.04 as got 4GB of memory and not sure how linux used the swap compared to windows.

So far everything seems to be working again, just need to re-install wine and thunderbird I think

okies, but 4GB swap would be fine. 32bit Ubuntu will only see about 3.5GB RAM natively - you can pop on PAE to 'see' the full 4GB.

A note on WINE, I'm not a WINE user, but reading thru' some of the threads on it, it seems some people are having really good results with the latest beta, over the stable release.

Phill.

---

### Post by walkerx on 2009-12-18
> **phillw said:**
> okies, but 4GB swap would be fine. 32bit Ubuntu will only see about 3.5GB RAM natively - you can pop on PAE to 'see' the full 4GB.

A note on WINE, I'm not a WINE user, but reading thru' some of the threads on it, it seems some people are having really good results with the latest beta, over the stable release.

Phill.

Running 64bit version as my gfx card has 2GB of memory.

I think I'll try the beta version as the shortcut to start wow from desktop doesn't seem to be firing up, and for some reason wine's added a load of other disks into it's list which could be the reason

---

