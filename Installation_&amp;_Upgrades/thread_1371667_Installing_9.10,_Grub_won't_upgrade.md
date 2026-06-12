---
title: "Installing 9.10, Grub won't upgrade"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by jus71n742 on 2010-01-03
I deleted the old partition that contained 8.04.  I then proceeded to install 9.10 along side Windows 7 ultimate.  When I was installing I recieved a prompt to install Grub to the master boot record.  I said yes.  Should I have said No?  Because when I now boot, I get GRUB loading stage1.5

GRUB loading, please wait...
Error 15

So I am guessing that I should not have installed GRUB to the master boot record.
Correct?
I figured it would over write the old grub also.

---

### Post by jus71n742 on 2010-01-03
ok, so I have rebooted with an 8.04 live cd just to see what I can find.  I know now that it can't find what isn't there.   So my question is now this.  how can I delete GRUB 1.5 so that GRUB 2.0 can take over?  Or just a way to install GRUB legacy (1.5) since in the installation the installer would not complete installation with 1.5. It basically demanded 2.0

---

### Post by onesojourner on 2010-01-06
bump. I would like to know how to do this too.

---

### Post by kansasnoob on 2010-01-06
> **onesojourner said:**
> bump. I would like to know how to do this too.

Well I hadn't seen the OP's post but in order to sort this out we'd need to see your individual results from the Boot Info script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

But just as an FYI the old grub is 0.97, package name "grub", aka legacy grub or grub-legacy. The new grub is commonly referred to as grub2 although the package name is "grub-pc" and it's version # is 1.97.

---

### Post by jus71n742 on 2010-02-14
> **onesojourner said:**
> bump. I would like to know how to do this too.

Best to just do a clean install. Unless you do an upgrade to 9.10. Then you can do an update on GRUB

---

### Post by darkod on 2010-02-15
> **jus71n742 said:**
> Best to just do a clean install. Unless you do an upgrade to 9.10. Then you can do an update on GRUB

9.10 already comes with grub2 (ver number 1.97) so there is no need to upgrade grub, it's already the latest. You didn't investigate further your original problem, t could have been a number of reasons. For example, if you have 2 or more disks maybe grub2 from the new install went to a different disk than you expected, and that error was in fact because you were booting from another hdd and the 8.04 partition with the old grub1 config files is gone.
Just an assumption.
One thing is for sure, clean install of 9.10 comes with grub2.

---

