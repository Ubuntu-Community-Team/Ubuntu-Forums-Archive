---
title: "Is it possible to upgrade Ubuntu without an internet connection?"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by Virtua-Touch on 2008-09-09
On my WIn98 computer, I dual booted Ubuntu using Wubi, and was wondering if it's possible to install updates without an internet connection. (Maybe download them from my Xp machine)

---

### Post by mike1234 on 2008-09-09
You can download packages for sure, but good luck. If there are any dependencies involved (which there will be) you'll get all kinds of error messages. You could try small packages, save them to a disk and install with gdeb or gdebi. But I doubt if you'll have much luck. It's a real hassle. You can download the full DVD so you'll have "everything" but it's not an update. Is there anyway you can sync your xp machine with your ubuntu? 

M.

---

### Post by iaculallad on 2008-09-09
> **Virtua-Touch said:**
> On my WIn98 computer, I dual booted Ubuntu using Wubi, and was wondering if it's possible to install updates without an internet connection. (Maybe download them from my Xp machine)

Try using AptOnCD if it will work.

---

### Post by mike1234 on 2008-09-09
> **iaculallad said:**
> Try using AptOnCD if it will work.

 Isn't that basically a backup and or restore disk of sorts? I can see a use for it already for me so If I do an install I don't have to bother updating or installing everything I have now. But he has no internet connection. 


M.

---

### Post by Virtua-Touch on 2008-09-09
I only have the internet on the XP. (Living Room) The Win98 is in the playroom. (About 30 feet away) I cannot install my WiFi adapter because Win98 isn't compatible with wireless, and my wireless adapter doesn't support linux.

---

### Post by iaculallad on 2008-09-09
> **mike1234 said:**
> Isn't that basically a backup and or restore disk of sorts? I can see a use for it already for me so If I do an install I don't have to bother updating or installing everything I have now. But he has no internet connection. 


M.

He could use it from other machines (installed with Ubuntu of course) that are currently updated, having the updates files from the cache folder (OP could use it to copy the update files then transfer it to the PC w/o net connection). 

Alternately, you could just use the Alternate CD if the OP installed Ubuntu on a dedicated disk.

---

### Post by doas777 on 2008-09-09
just to clarify, do you mean upgrade (as in gutsy to hardy) or update (as in patch a specific package)?

---

### Post by mike1234 on 2008-09-09
> **iaculallad said:**
> He could use it from other machines (installed with Ubuntu of course) that are currently updated, having the updates files from the cache folder (OP could use it to copy the update files then transfer it to the PC w/o net connection). 

Alternately, you could just use the Alternate CD if the OP installed Ubuntu on a dedicated disk.

 Yea I see what you're saying. Thanks for the heads up on aptoncd. I wasn't aware it was available. I get bored sometimes and try a new distro. But always come back to Ubu. :)

M.

---

### Post by iaculallad on 2008-09-09
> **mike1234 said:**
> Yea I see what you're saying. Thanks for the heads up on aptoncd. I wasn't aware it was available. I get bored sometimes and try a new distro. But always come back to Ubu. :)

M.

I'm glad to have cleared the relation b/w aptoncd and PC w/o net connection :)

```
sudo apt-get install aptoncd
```

For trying other *new* distros, try Zenwalk too.. v5.2 is already available.

---

### Post by Virtua-Touch on 2008-09-10
As in updating. Where you get the notification update saying "You have 100 software updates"

And, I just looked at the website, and I'll have a go at it tomorrow. I'll update you when it happens.

---

