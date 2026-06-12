---
title: "Kernel advice for 13.04"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by teXLRmQ on 2013-08-14
So I just installed Ubuntu 13.04 on my Toshiba laptop yesterday. I've used Linux before but not for a while. As soon as my install was done I got a notification for some updates, including a kernel update. I installed but afterwards my computer would not boot. I got an error saying "kernel panic not syncing vfs unable to mount root fs on unknown block" and after that all I got was the GRUB command line.

I looked up troubleshooting steps for this online but I could not get any of them to work. I booted from a live CD and tried to mount the system from it but it kept saying the mount points didn't exist, then I got more problems with chroot. I am guessing this is because I set that install up in an encrypted LVM.

Anyway, after trying and failing to make it work, I just did a clean install (with only my home folder encrypted, no LVM this time) since my initial install was only a day old anyway, and now I have it back up and running (and dual booting with Debian perfectly).

**My question, however, is now I have it up and running, how do I update the kernel on Ubuntu without the same problem coming back?** If I don't let the built in updater do it, but instead update to the latest Linux kernel manually[ with a tutorial like this]("http://www.liberiangeek.net/2013/06/linux-kernel-3-9-8-released-how-to-upgrade-in-ubuntu-13-04-raring-ringtail/"), will that avoid the issue?

Thanks in advance.

---

### Post by lukeiamyourfather on 2013-08-14
If you update the Linux kernel manually you're asking for trouble. I simply would not update the kernel if the default one works. You can prevent the kernel from being updated with this command.

```

sudo apt-mark hold linux-image-$(uname -r)

```

I've never tried it before, but that should do it. Someone please correct me if that's wrong.

---

### Post by tgalati4 on 2013-08-14
Do some [searching]("https://help.ubuntu.com/community/PinningHowto") on how to "pin" packages to keep them from being updated.  The above command should work as one method to pin the kernel to the installed version and no higher.  Did you reboot after the initial installation?  Perhaps the updater got messed up because it required some updates and a reboot in order to work properly.  

Generally, you want to hold off on updates until you assess how your system is working.  I like to wait a few weeks.  That way you will have a comprehensive list of what doesn't work or small annoyances that you want to fix.  Then, as you install updates, you can see if any items get fixed automatically and what still needs manual tweaking.  Also, install the updates is smaller groups so that you can see if there are any regressions--things that were working and are now not working due to an update.  Installing several hundred updates at once is convenient, but increases the chances of borking your system with little clue as to what specific update caused the borkage.

You might have a hard disk issue.  How many hours on the disk?

```
sudo smartctl -a /dev/sda
```

---

### Post by teXLRmQ on 2013-08-14
> **lukeiamyourfather said:**
> If you update the Linux kernel manually you're asking for trouble. I simply would not update the kernel if the default one works. You can prevent the kernel from being updated with this command.

```

sudo apt-mark hold linux-image-$(uname -r)

```

I've never tried it before, but that should do it. Someone please correct me if that's wrong.

Ran that command it said "linux-image-3.8.0-19-generic set on hold." so it looks like it worked :)

> **tgalati4 said:**
> Do some [searching]("https://help.ubuntu.com/community/PinningHowto") on how to "pin" packages to keep them from being updated.  The above command should work as one method to pin the kernel to the installed version and no higher.  Did you reboot after the initial installation?  Perhaps the updater got messed up because it required some updates and a reboot in order to work properly.  

Generally, you want to hold off on updates until you assess how your system is working.  I like to wait a few weeks.  That way you will have a comprehensive list of what doesn't work or small annoyances that you want to fix.  Then, as you install updates, you can see if any items get fixed automatically and what still needs manual tweaking.  Also, install the updates is smaller groups so that you can see if there are any regressions--things that were working and are now not working due to an update.  Installing several hundred updates at once is convenient, but increases the chances of borking your system with little clue as to what specific update caused the borkage.

You might have a hard disk issue.  How many hours on the disk?

```
sudo smartctl -a /dev/sda
```

I did indeed reboot after the initial installation, I turned it off at night. A lot of people had the same issue judging by my googling.

Are there no problems with keeping the kernel as-is then? It came up as a security update, I'm no less secure with an old kernel if I'm just using it as a normal computer am I?

When the updates came up on this new install I unticked all the kernel related stuff before hitting install but it started downloading the kernel images anyway so I cancelled it and used the "sudo apt-get --only-upgrade install packagename" command in order to update Firefox and leave everything else untouched. Any idea why the graphical updater downloaded kernel images even when I unticked them though?

The "smartctl" command is not found by my system and apt-get doesn't seem to know it either. I would be very surprised if I had a hard disk issue though, this is a brand new laptop and I had very little issue in Windows aside from, you know, the usual Windows stuff :P

---

### Post by teXLRmQ on 2013-08-14
Okay new development: I just updated Ubuntu without the kernel image and it all ran fine, rebooted after and system seems to have no issues. However at the end of the update, apt-get told me:

```
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic
```

According to my googling that is what the system failed to do before and that's what caused my problem. But it did this with me holding the kernel back this time.

Stranger still, this time when I booted, even though apt-get still tells me the kernel is on hold, uname -r and GRUB are telling me my kernel *has* been updated to the version listed above.

So now I'm just confused. Wat do?

---

### Post by lukeiamyourfather on 2013-08-14
What does this command say? It will tell you the kernel running at that exact moment with all the details about it.

```
uname -a
```

---

### Post by teXLRmQ on 2013-08-14
The output for that command is:

```
Linux tread-lightly 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

That's the same version that I've held back. Has it gone and updated anyway?

---

### Post by lukeiamyourfather on 2013-08-14
> **teXLRmQ said:**
> 
That's the same version that I've held back. Has it gone and updated anyway?

I think so, but if it's working there's no issue, right? The breakage before might have been a fluke or a bug that's difficult to reproduce.

---

### Post by teXLRmQ on 2013-08-14
> **lukeiamyourfather said:**
> I think so, but if it's working there's no issue, right? The breakage before might have been a fluke or a bug that's difficult to reproduce.

True. So is it safe to unpin those updates then?

---

### Post by lukeiamyourfather on 2013-08-14
I'd try it now before you get too far along. If it breaks again at least you won't have lost much in the process compared to finding out a few weeks from now.

---

### Post by teXLRmQ on 2013-08-14
> **lukeiamyourfather said:**
> I'd try it now before you get too far along. If it breaks again at least you won't have lost much in the process compared to finding out a few weeks from now.

Kernel update installed, everything's fine :D

It does still tell me:

```
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic


```

Even though they're not on hold according to apt-get.

But yeah everything seems fine.

I would like to know how the hell the kernel installed even when I held it back though. Any ideas on that? That in itself seems like a bug.

---

### Post by tgalati4 on 2013-08-15
The kernel is only one of several parts that make up the initial boot up.  It's possible that the post-installation configuration script tried to to make a new initrd and couldn't find the matching kernel image.  

*Smartmontools* is used to monitor your disk health.  It is not installed by default.  If you found others with boot problems after this particular update, then that would indicate a regression.  A later update would normally fix that.

---

### Post by teXLRmQ on 2013-08-15
> **tgalati4 said:**
> The kernel is only one of several parts that make up the initial boot up.  It's possible that the post-installation configuration script tried to to make a new initrd and couldn't find the matching kernel image.  

*Smartmontools* is used to monitor your disk health.  It is not installed by default.  If you found others with boot problems after this particular update, then that would indicate a regression.  A later update would normally fix that.

That was my initial thought, but then why did uname -r tell me the new kernel was installed?

I installed that and ran it, says my drive is fine.

---

