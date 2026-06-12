---
title: "Install Ubuntu 20.04 with LUKS on a dual boot machine - possible?"
date: 2021-02-04
forum: Installation &amp; Upgrades
---

### Post by Bobby_James on 2021-02-04
Is it possible to install Ubuntu 20.04 with LUKS on a dual-boot system (with Windows). Or must one erase the entire hard drive to install Ubuntu with LUKS.

I think - based on the installation videos I've watched - that you need to install LUKS over the entire hard drive but I might be wrong.

---

### Post by TheFu on 2021-02-04
There is a different between what can easily be done and what might be accomplished by an expert with 3 months to spend.

There is no easy way to have full drive encryption with 2 OSes, one being Windows, loaded.
But no, you don't need to erase the entire hard drive either.  The Ubuntu installer will automatically do that when you choose whole drive encryption with LVM.  Obviously, Windows will be gone.

The easy answer for this sort of need is to run whichever OS you need most directly on the hardware and run the other OS inside a virtual machine.  For non-GUI stuff, 90-95% of native performance is possible using a VM these days, provided it is tuned correctly.

Dual booting hasn't been needed for most people the last 10 yrs.

Moving on ... if you want to have encrypted data partitions with LUKS, that isn't hard and will work under a dual-boot situation.
Don't forget that encrypted data is only locked when the partition/LV isn't mounted.  If it is mounted, then it is available just like unencrypted storage.  Encrypted storage is useful when a system is powered off only, not while running.  
It is handy if a HDD is under warranty and you need to send it in for replacement - all that encrypted data will not be accessible.

Encrypted storage doesn't magically make it unavailable to the world when the system is running.
And if using encryption, excellent backups are mandatory. Should an encrypted HDD die, there aren't any disk tools that can read that stuff and recover it. In fact, if just a few key sectors go bad (the LUKS headers), all the data will be lost. Have great, automatic, backups for any data you don't want to lose.

---

### Post by Bobby_James on 2021-02-04
Thanks for your input. So I assume from what you are saying is that I can setup 20.04 without LUKS then create specific partitions in Ubuntu with LUKS after everything is setup. Is that correct

---

### Post by oldfred on 2021-02-04
I do not use LVM, but there is this:
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

