---
title: "Finding a misplaced thunderbird profile"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Mel_K on 2009-12-05
Hi,
While I was overseas for a month my husband upgraded our home pc to 9.10. He thought he was being helpful, however he did not make a back up.
This has caused many issues and I want to take off my stuff and start from scratch.

Unfortunately, I cannot find my profile for Thunderbird. I found a file that says profile, but it hasn't changed since 2006.

I probably did not set it up properly when I first started ubuntu in 2006 and initially downloaded and installed a lot of things like I would have in Windows without using Synaptic.(i.e.. download file directly, open zipped file...) I have since cured myself of that habit.

What can I do?  Is there a way to search for files last modified by date?  I know the date the file would have last been changed- October 31. I need to find this as I have quite a lot of work email messages and email addresses in my address book that I actually need. 

Any advice or pushes in the right direction are always appreciated.

---

### Post by phillw on 2009-12-05
> **Mel_K said:**
> Hi,
While I was overseas for a month my husband upgraded our home pc to 9.10. He thought he was being helpful, however he did not make a back up.
This has caused many issues and I want to take off my stuff and start from scratch.

Unfortunately, I cannot find my profile for Thunderbird. I found a file that says profile, but it hasn't changed since 2006.

I probably did not set it up properly when I first started ubuntu in 2006 and initially downloaded and installed a lot of things like I would have in Windows without using Synaptic.(i.e.. download file directly, open zipped file...) I have since cured myself of that habit.

What can I do?  Is there a way to search for files last modified by date?  I know the date the file would have last been changed- October 31. I need to find this as I have quite a lot of work email messages and email addresses in my address book that I actually need. 

Any advice or pushes in the right direction are always appreciated.

Hi,

things mozilla are held in a hidden directory within your ~home directory.

```

ls -a .moz*

```Should point you to your FFox & Thunderbird areas.

Having pin-pointed where they are, you should be able to use this --> [http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

For going digging.

If you need root privalideges, do NOT use **sudo** .. use **gksudo**

Hope that helps,

Phill.

---

