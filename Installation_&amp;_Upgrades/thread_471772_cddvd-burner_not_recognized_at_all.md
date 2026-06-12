---
title: "cd/dvd-burner not recognized at all"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by RobotJox on 2007-06-12
Hi,

Feisty does not recognize my laptop-burner at all.

It's a TSST ts-l632d that came with my ASUS latop.
It works in Vista and I even installed Feisty with it. Bios recognizes it and I can boot with it.

However it's totally invisible in Feisty.

```
dmesg | grep CD
```

gives me nothing

it's in Fstab, but when I try to mount it I get:

> special device /dev/hdb does not exist

PLEASE HELP - this is depressing... :(

---

### Post by wpshooter on 2007-06-12
Is it recognized in earlier versions of Ubuntu ?

---

### Post by RobotJox on 2007-06-12
> **wpshooter said:**
> Is it recognized in earlier versions of Ubuntu ?

I haven't tried other versions, but it's not recognized in kernels 15 & 16. Do you think I should try earlier versions or other distros?

---

### Post by wpshooter on 2007-06-12
You might want to make sure that your firmware on the CD drive is at the latest & greatest and if that does not work then I would definately try an older version.  I think there are still a lot of bugs in Feisty.

---

### Post by Pumalite on 2007-06-12
> **wpshooter said:**
> You might want to make sure that your firmware on the CD drive is at the latest & greatest and if that does not work then I would definately try an older version.  I think there are still a lot of bugs in Feisty.

Check this too:

[http://ubuntuforums.org/showthread.php?t=405630&page=5](http://ubuntuforums.org/showthread.php?t=405630&page=5)

---

### Post by RobotJox on 2007-06-14
I have upgraded the firmware, but that didn't help.

The one thing that baffles me:

The drive is recognized in **DAPPER** - but I would rather not stay with Dapper :)

it is NOT recognized in **Gutsy**

I have even tried other distros:

**Fedora 7**: can't install - the installer won't recognize the cd-rom, even though it boots from it :[B](
PCLinuxOS[/B]: WORKS!

thanks for the link - that didn't solve my issue - the drive is not recognized at all.

Thanks for the help so far... Any more ideas?

---

### Post by RobotJox on 2007-06-14
I forgot to mention that I had to install Ubuntu using the Alternate Install-cd, because the live-cd does not support the Geforce 8600m GS card. I'm beginning to think that this is somehow important...or not...

Btw. my notebook is a Asus S96S with a Santa Rosa chipset.

Please help!!!

---

### Post by RobotJox on 2007-06-14
I have just installed Edgy - and behold! the drive is recognized!!! I will try to update to Feisty from Edgy and see if this works. I guess this means that there is a bug in Feisty?

---

### Post by RobotJox on 2007-06-14
Yep - upgrading Edgy to Feisty makes my drive "disappear". So I guess this really is a Feisty bug, huh?

---

### Post by RobotJox on 2007-06-15
Solved!!!!

These instructions did it for me:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603/comments/66](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603/comments/66)

thanks povvy, whoever you are :D

---

