---
title: "updates/upgrades and what they mean...."
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2008-10-25
i'm trying out ubuntu 8.1 (the version i am using was installed from a live cd that i created before the release candidate was available)...

my questions:

what is the difference between an update and an upgrade as it pertains to the entire OS ?

when the OS is officially released, will people that use beta's and rc's get the official upgrades/updates to make their version same as the official release ?

---

### Post by Afkpuz on 2008-10-25
Update usually means that something you already have will be improved.

When you install a beta/alpha version of ubuntu, you will get tons of updates up until the release point, fixing the little bugs that are found.

Then, when the distro is finally released (next thursday), you'll see a little box pop up saying there is a new distribution available.  Then, you will upgrade!  Secretly, you are just downloading updates and more bug fixes, but when we say upgrade, we mean you're moving from one distro to the next.

But yes, you'll be brought up to speed and be official.  Update manager also handles everything.  Although, it sometimes takes a long time to update since the servers get a huge load.  I just prefer to download the CD and be done with it.

---

### Post by zero7404 on 2008-10-25
> **Afkpuz said:**
> Update usually means that something you already have will be improved.

When you install a beta/alpha version of ubuntu, you will get tons of updates up until the release point, fixing the little bugs that are found.

Then, when the distro is finally released (next thursday), you'll see a little box pop up saying there is a new distribution available.  Then, you will upgrade!  Secretly, you are just downloading updates and more bug fixes, but when we say upgrade, we mean you're moving from one distro to the next.

But yes, you'll be brought up to speed and be official.  Update manager also handles everything.  Although, it sometimes takes a long time to update since the servers get a huge load.  I just prefer to download the CD and be done with it.

thanks....

i wanted to be sure that it'll be up-to-date without having to download another image and reinstall the OS...although i might do that anyway.

now, can you tell me if there's any specific tools i'd need to use to keep my installation clean and running healthy ?

since this isn't windows, there's no such thing as a registry, would i also need to use defragmenting tools in ubuntu ?

---

### Post by ddrichardson on 2008-10-25
> **zero7404 said:**
> since this isn't windows, there's no such thing as a registry, would i also need to use defragmenting tools in ubuntu ?

No, Ext works differently to Fat/NTFS resulting in less fragmentation and its checked every so many mounts.

The only thing that needs cleaning, IMHO is the downloaded packages, which you can do by typing:

```
sudo apt-get autoclean
```

As for upgrade - I'd avoid it.  Personal experience is that it often introduces more problems than installing a new version.

---

### Post by tgalati4 on 2008-10-25
Upgrade==agony.  Only Upgrade if you feel like building a system from scratch right now.  Upgrade gives you a whole new operating system.  Think new car financing.

It's unfortunate that one selects Upgrade thinking it is an instant improvement only to find that they have completely hosed their system.

Update==less agony.  Helpful for security fixes and some bug fixes.  Avoid kernel and xorg (video) updates unless you like to fix things right now.  Think wax job on the old car.  But don't pull the engine out (kernel/xorg updates).

When will Ubuntu implement a graded (Level 1 to Level 5) update scheme like the Linux Mint folks?  It could reduce the load on the forums.  mintUpdate is a simple, yet effect scheme for new users to update their system in a sane fashion.

---

### Post by zero7404 on 2008-10-25
> **ddrichardson said:**
> No, Ext works differently to Fat/NTFS resulting in less fragmentation and its checked every so many mounts.

The only thing that needs cleaning, IMHO is the downloaded packages, which you can do by typing:

```
sudo apt-get autoclean
```

As for upgrade - I'd avoid it.  Personal experience is that it often introduces more problems than installing a new version.

thanks for the code, i used it and it removed quite a few files.
i also use system cleaner under apps/system tools, but i don't think that does the same thing as autoclean.

---

### Post by zero7404 on 2008-10-25
> **tgalati4 said:**
> Upgrade==agony.  Only Upgrade if you feel like building a system from scratch right now.  Upgrade gives you a whole new operating system.  Think new car financing.

It's unfortunate that one selects Upgrade thinking it is an instant improvement only to find that they have completely hosed their system.

Update==less agony.  Helpful for security fixes and some bug fixes.  Avoid kernel and xorg (video) updates unless you like to fix things right now.  Think wax job on the old car.  But don't pull the engine out (kernel/xorg updates).

When will Ubuntu implement a graded (Level 1 to Level 5) update scheme like the Linux Mint folks?  It could reduce the load on the forums.  mintUpdate is a simple, yet effect scheme for new users to update their system in a sane fashion.

when 8.10 goes mainstream, would that not appear as an 'upgrade' to those that are using the beta/rc and previous builds ?

i had a lousy experience once when i tried doing an upgrade. since my second re-install of the OS, i have not done an upgrade, just updates, so far everything has been working smooth...

---

### Post by ddrichardson on 2008-10-25
Probably but I rarely do it - developing bits and pieces means a lot of us use virtual machines for the RCs and I bin them on release. I tend to run the LTS.

---

