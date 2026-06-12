---
title: "[SOLVED] Update manager problem"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by csc2ya on 2008-07-10
Odd problem with update manager. This has happened about 5 times today so far:

I keep getting a yellow triangle appearing on the top panel that has an exclamation mark in it. When I hover over it, I get the following message:

'The update information is outdated. This may be caused by network problems. Please update manually by clicking on this icon and then selecting 'Check'.'

When I do that, it says there are no updates available, and also that the last time I checked for updates was 7 days ago. However, there were a load of updates installed yesteday, so i'm not quite sure why it's saying that.

About the only thing that's changed lately, is I rebooted my router last night, but I don't think it's caused by that.

Anyone got any ideas?

---

### Post by jimv on 2008-07-10
Try "sudo apt-get update" in a terminal.

---

### Post by csc2ya on 2008-07-10
Thanks...seems to have sorted it. I'll find out soon.

Doesn't seem to be coming up now, so it looks like it has fixed it. Thanks again.

---

### Post by csc2ya on 2008-07-10
looks like I spoke too soon...it's started appearing again:confused:

---

### Post by iaculallad on 2008-07-10
> **csc2ya said:**
> looks like I spoke too soon...it's started appearing again:confused:

Try using different download Server:

System->Administration->Software Sources, under the "Ubuntu Software" tab, make sure that Main, Universe, Restricted, and Multiverse  are CHECKED. "Download From:" should equal to "Main Server". And, make sure that the option "Installeable from CDROM-DVD" is unchecked. Click on Close buttong and  select/click on "Reload" button on the next window that displays.

When done, Drop to your terminal and issue the command:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by csc2ya on 2008-07-11
I thought i'd wait a while before replying to check that it didn't come up again, but the sudo apt-get update && sudo apt-get upgrade seems to have fixed it.

I did that last night, and it still came up, but after being off for a few hours overnight, It hasn't occurred today at all, so it looks like it's fixed. Thanks for the help:)

---

