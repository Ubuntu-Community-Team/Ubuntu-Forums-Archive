---
title: "Upgrade 13.10 to 14.04 without net connection"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2014-04-24
The live DVD sees 13.10 installed, but the option to upgrade is grayed out. It used to be that you used the Alternate ISO to do an upgrade without a net connection, but there are no longer Alternate ISOs. Am I forever stuck with 13.10?

---

### Post by ian-weisser on 2014-04-24
The LiveDVD upgrader is based on the old Alternate upgrader.

As to why it's grayed out on your system, I don't know. It's likely that the alternate .iso, if it still existed, would have exactly the same problem on your system.

So if you are unwilling to backup-and-reinstall, then yes, I suppose you are stuck with 13.10.

---

### Post by John Jason Jordan on 2014-04-25
> **ian-weisser said:**
> The LiveDVD upgrader is based on the old Alternate upgrader.
As to why it's grayed out on your system, I don't know. It's likely that the alternate .iso, if it still existed, would have exactly the same problem on your system.

I have discovered some more interesting things.

I decided to cheat and try the upgrade with a net connection (ethernet). After booting the live DVD the upgrade option was no longer grayed out. So I selected it and clicked to continue the upgrade, but just before doing so I pulled the ethernet cable. The upgrade whirred on for a few moments and then announced that it could not continue because the net connection had been lost. 

Conclusion: The upgrade option on the live DVD misleads you. It leads you to think you are upgrading from the USB or optical media but, in fact, it will pull all the files from the net the same as if you just did sudo apt-get upgrade from the command line without even having the media mounted.

Reading this forum I see numerous people whose upgrades were terminated unexpectedly and who suffered disasters as a result. And the Ubuntu decision to require a net connection for all upgrades is also bad for groups who want to get together for an upgrade session - with a lot of people in the room hitting the net at the same time the bandwidth is going to be pathetic.

---

### Post by grahammechanical on 2014-04-25
Have you tried going into System Settings>Software and Updates and setting that 14.04 disk as a software source/repository?

---

### Post by John Jason Jordan on 2014-04-25
> **grahammechanical said:**
> Have you tried going into System Settings>Software and Updates and setting that 14.04 disk as a software source/repository?

That is an interesting suggestion, but I can't figure out how to do it.

First, I do not have System Settings > Software and Updates. I suspect that it is not there because I have Xubuntu, not Unity. There is a place to modify repositories in Synaptic > Settings > Repositories, but there is no way to add the optical drive. There is a message in that dialog box that says "To install from a CD-ROM or DVD insert the media into the drive." But when I do so the media is automatically mounted, but nothing happens in the repositories. 

Maybe I can add it my modifying the sources file, but I don't know how to do that.

---

### Post by C.S.Cameron on 2014-04-25
I have read elsewhere in these forums that this upgrade option becomes available at the point release, 14.04.1, (or whatever), available about July.

I have read about solutions using terminal, but have not yet had success using one to upgrading from USB.

---

### Post by ian-weisser on 2014-04-27
> **John Jason Jordan said:**
> And the Ubuntu decision to require a net connection for all upgrades is also bad for groups who want to get together for an upgrade session - with a lot of people in the room hitting the net at the same time the bandwidth is going to be pathetic.

Not at all - that's what caching proxies are for. Several are in the Ubuntu Repositories, are trivially easy to install, and really speed up multiuser connections by eliminating all that duplicated downloading.

---

### Post by John Jason Jordan on 2014-06-27
> **C.S.Cameron said:**
> I have read elsewhere in these forums that this upgrade option becomes available at the point release, 14.04.1, (or whatever), available about July. I have read about solutions using terminal, but have not yet had success using one to upgrading from USB.

I started this thread on April 24 right after Trusty was released. I still haven't upgraded my 13.10 because I can't trust my net connection. Once several years ago I was upgrading and lost the net connection, causing a mess that took two days to repair. Once burned, twice shy, as the saying goes. 

It's now a couple months later, so I was wondering if it's possible to find out how close the 14.04.1 (or whatever it will be called) will be released. Is there a place where this is discussed or a log or some way to figure out how it is progressing?

---

### Post by mörgæs on 2014-06-27
13.10 loses support 17. of July and 14.04.1 is out 24. of July.

Upgrades are risky. A backup and a fresh install is recommended.

---

### Post by John Jason Jordan on 2014-06-27
> **mörgæs said:**
> 13.10 loses support 17. of July and 14.04.1 is out 24. of July.

Thank you for the information.

---

### Post by John Jason Jordan on 2014-07-25
> **mörgæs said:**
> 13.10 loses support 17. of July and 14.04.1 is out 24. of July.

Indeed, 14.04.1 came out in July 24. I downloaded it and booted to it, but you still cannot do an upgrade without a net connection. If there is no net connection the upgrade option will be grayed out. And if there *is* a net connection the upgrade will continue, but ignore the boot media. In fact, you can pop the media out and the upgrade will continue. This is very deceptive because the menu options lead the user to think the upgrade is continuing from the boot media.

---

