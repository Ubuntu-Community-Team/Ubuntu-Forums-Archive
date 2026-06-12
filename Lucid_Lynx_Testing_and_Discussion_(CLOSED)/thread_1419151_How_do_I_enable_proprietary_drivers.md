---
title: "How do I enable proprietary drivers"
date: 2010-03-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brawd on 2010-03-01
Hi All,

I'm using 10.04 (Lucid) and have a message at boot up saying video is out of range. Then the machine goes on to boot and everything apparently works normally. This may be a Lucid teething problem - or not - but I thought it was time to activate the proprietary driver for my nvidia mobo.

I brought up the list no problem and I have 4 to choose from with one recommended by Lucid HQ. Taking guidance I went to activate it but there doesn't seem to be a button that says 'Activate' on it. I have the ones that says 'Remove', 'Help' and 'Close', but no activate.

Anyone know how to activate this in Lucid please?

regards,

brawd.

---

### Post by Perfect Storm on 2010-03-01
Moved to Lucid Lynx Testing and Discussion.

---

### Post by philinux on 2010-03-01
> **brawd said:**
> Hi All,

I'm using 10.04 (Lucid) and have a message at boot up saying video is out of range. Then the machine goes on to boot and everything apparently works normally. This may be a Lucid teething problem - or not - but I thought it was time to activate the proprietary driver for my nvidia mobo.

I brought up the list no problem and I have 4 to choose from with one recommended by Lucid HQ. Taking guidance I went to activate it but there doesn't seem to be a button that says 'Activate' on it. I have the ones that says 'Remove', 'Help' and 'Close', but no activate.

Anyone know how to activate this in Lucid please?

regards,

brawd.

If your graphics card is nvidia then select nvidia-current.

---

### Post by coffeecat on 2010-03-01
> **philinux said:**
> If your graphics card is nvidia then select nvidia-current.

Nvidia-current was problematic with my GeForce 8400GS card. I got the login screen OK, pressed enter on my username and then the screen just displayed some blocky green and other coloured squares, with the whole system locking up solid. I had to do a hard power-down.

After booting into recovery mode and deleting xorg.conf to get the 'nv' driver back, I activated the 173 driver (175? - I'm going from memory - I'm in Karmic atm), and that was OK, although not ideal.

---

### Post by haydoni on 2010-03-02
Was it an Upgrade to LL? It sounds like it's already installed.

I have noticed that upon installing the proprietary driver I can't activate the open driver (by activating), which is pre-installed. I want to as the proprietary one doesn't work on BBC iplayer/news videos.

Try removing it then (hopefully) the activate will become available.

---

### Post by haydoni on 2010-03-02
Yep, remove the one which is currently activated and restart. (if it says remove - it means it's installed).

There seems to be an issue meaning you can't activate installed drivers. Does this happen for anyone else? Is this bug is already known (I can't find it)?

*Wohoo now BBC works again!*

---

### Post by ratcheer on 2010-03-02
On my system, when I activate the recommended (v 195) driver and reboot, the Hardware Manager says, "This driver is activated but not currently in use". However, I think the part about "not currently in use" must be in error, because I can use the compiz features, which I cannot do with the Nouveau open source driver.

Tim

---

### Post by brawd on 2010-03-02
Hi all and thank you for your suggestions. I was so long getting back simply because I haven't been able to boot.

The installation of LL was an upgrade from something or other, I forget which version but now I'm back online I'll get the .iso and burn a cd.

My upgrades aren't going too well either, what with unmet dependencies, broken count and crashes (?), LL choice of words not mine.

Not that I understand any of it anyway, particularly the bit about sending an error report, which I did. Then I had to log into Launchpad. ?????? What's that?

Don't answer, that bit was rhetorical.

I'm about to try your suggestions - so here goes.


regards,

brawd.

---

### Post by brawd on 2010-03-03
I'm afraid the whole machine has bitten the dust.

Serve me right for not having the .iso to hand.

I've downloaded it on another machine and will try a complete re-install later.

I'm sorry (but grateful to you all) that it didn't work out this time.

But it's a good looking operating system and I am well aware it's still being developed. I'm sticking with it as I have other computers available to me.

regards, and thanks again,


brawd

---

### Post by Kevbert on 2010-03-03
If you have unmet dependencies it may be due to a bad ISO download (have you md5sum/checksummed ?), badly burnt CD (have you checked the disk integrity via the install menu ?) or if you try to install other packages that aren't in the repos.

---

### Post by haydoni on 2010-03-03
> **brawd said:**
> I'm afraid the whole machine has bitten the dust.

Sorry to hear that. Good luck with the fresh install (I expect this process is much more streamlined at the moment). If you have a separate /home partition then it's (pretty much) no bother to do a fresh install everytime - but then I don't stray too far from the default...

Upgrade testing did however start on the 18th of Feb, so I'm guessing there is somewhere to (bug-)report this to...?

---

