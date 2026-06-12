---
title: "Upgrade Warty to Haory without internet?"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by bigkahuna on 2005-04-15
Hi all,

I'm still pretty new to Ubuntu and "finally" got my installation of Warty about where I'm happy with it.  I'd like to upgrade to Haory but I don't have access to the internet on this system.

Can I upgrade my installation with the Haory install CD or will it completely wipe Warty (which is what I'm guessing will happen).  Is there a way to apt from the install disk?

Thanks,

Paul

---

### Post by Dr Gonzo on 2005-04-15
You *should* be able to add the Hoary CD to the apt repository list.  I assume you haven't installed any packages at all from the internet on this machine.

Open /etc/apt/sources.list and look at the top entry.  It should be the warty cd.  Now, comment that line out (with a #) and add this line:```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
```  I assume, since this is a non-internet system, that you have all the other lines commented out.  So, try an ```
apt-get update
``` and see if it works.  If so, you should be able to upgrade.

NOTE that I give no guarantees that this will work.  However, I can't from my perspective see why it wouldn't.  Your mileage may vary. :)

---

### Post by az on 2005-04-15
sudo apt-cdrom add
or use synaptic to add the cd repository.  Then do a smart upgrade.

No, it will not wipe your Warty install.  This is debian, not windows.

---

### Post by bigkahuna on 2005-04-15
Thanks for the tips, I'll give them a try.

[QUOTE=azz]No, it will not wipe your Warty install.  This is debian, not windows.[/QUOTE]

 I'm not a complete convert to Linux yet, so I'm still a bit "gun shy" when it comes to installing apps.  Thanks again,

Paul

---

### Post by Dana on 2005-04-16
Doesn't the Hoary installation CD have an option to update your current installation?
Someone told me it did.

I was curious if it still installs the i386 kernel by default? That caught me by surprise when I installed Warty. Later I replaced it with the i686. Will that cause any problems if I update my installation from the Hoary CD when I receive it?

Dana

---

