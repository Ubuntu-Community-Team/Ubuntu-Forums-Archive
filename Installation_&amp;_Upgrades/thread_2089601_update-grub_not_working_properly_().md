---
title: "update-grub not working properly (?)"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by elmuchacho on 2012-11-29
Hello,

I have a problem with Grub 1.99 on a laptop since my last update of Ubuntu 12.04 LTS  about a week ago.

My first gripe is, since this update, I started to see the Grub menu, without me ever asking for it. In fact, I would like to avoid it, because this PC is going to be sent to our customer, and I don't want him to play with Grub, so I'd rather NOT have Grub menu be displayed by default.

Secondly, there is no timeout in this Grub menu by default, and that is a real problem, because the PC must be able to reboot without manual intervention.

So after googling a bit I checked the /etc/default/grub file, and it contained the following header:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

That looked good to me, nevertheless, I typed:
sudo update-grub, which regenerated the /boot/grub/grub.cfg file, according to timestamps.

Unfortunately, this hasn't changed anything, it behaves as if GRUB_TIMEOUT=-1 (infinite). Indeed, modifying the /etc/default/grub file doesn't seem to affect the result at all.

edit: "Indeed, modifying the /etc/default/grub file doesn't seem to affect the result at all."
This is in fact incorrect, the file IS modified and the timeout variable is updated correctly, but the behaviour of Grub at boot time doesn't change.

What am I doing wrong ? Is there a bug in this latest release of 12.04 ? (Stability has lessened with this version, I often get popup windows showing "internal crashes", something I didn't have before the update).


edit: I seem to be not alone in that situation:
[http://askubuntu.com/questions/191686/grub-menu-not-waiting-despite-of-grub-timeout-10?rq=1](http://askubuntu.com/questions/191686/grub-menu-not-waiting-despite-of-grub-timeout-10?rq=1)

---

### Post by oldfred on 2012-11-30
I posted in this thread that I really do not know grub settings. drs305 knows a lot about grub2 and posted some hints.

This was for older version but still grub2.
       Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

---

### Post by elmuchacho on 2012-11-30
This seems to be a bug, there is yet another reports:

[http://askubuntu.com/questions/202309/cannot-get-grub-menu-to-timeout-or-go-away?rq=1](http://askubuntu.com/questions/202309/cannot-get-grub-menu-to-timeout-or-go-away?rq=1)

BTW, I DID try to change 

```

if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi

```
into 
```

if [ ${recordfail} = 1 ]; then
  set timeout=5
else
  set timeout=5
fi

```
in grub.cfg (with vi, and being very careful at that).

I definitely don't recommend doing this as the next boot crashed grub. I've no idea why, but it looks that it's not safe to assume that grub.cfg is merely a script. Fortunately the following one did run (bypassing grub entirely, if I remember well) and I could run sudo update-grub to reset it fine (i.e to the initial situation).

---

### Post by oldfred on 2012-11-30
Did you try Boot-Repair as that often fixes issues.

And  many suggest Grub Customizer for changing grub's settings.

---

### Post by YannBuntu on 2012-11-30
Hello
I recommend you:
1) reset GRUB settings by running [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") --> Advanced options --> "GRUB options" tab --> tick "Purge GRUB and reinstall it --> Apply.
Reboot, the timeout should work.
2) then you can use [GRUB-Customizer]("https://launchpad.net/grub-customizer") to hide GRUB.

---

### Post by elmuchacho on 2012-11-30
Hello YannBuntu, I haven't tried boot-repair.

Yet I managed to get a solution that seems to work (for me at least): the file /boot/grub/grubenv contained the line 

set recordfail=1 

Simply deleting that file and re-running update-grub afterwards repaired the bootloader. It seems that somehow, this file is modified, maybe when the OS isn't shut down properly (??), and this triggers the bug.
I guess that's more or less what "Purge Grub" does.

Anyway, I'll change the title of this thread as solved.

---

### Post by oldfred on 2012-11-30
That is not a bug, but a feature. :)

If system is shutdown improperly, it is assumed you may need to boot in recovery mode so grub gives you menu.

---

### Post by elmuchacho on 2012-12-01
> **oldfred said:**
> That is not a bug, but a feature. :)

If system is shutdown improperly, it is assumed you may need to boot in recovery mode so grub gives you menu.

Ah ok, so it's a feature of grub, but the problem is update-grub doesn't seem to be aware of it (and THAT's a bug :) ) as there is no other means I know of to recover from this state apart from doing what I've done (I haven't tested boot-repair, as the bootloader isn't really corrupt).
According to the links I've given and the answers given so far (most of the solutions given in the links don't work), not too many people know how to solve this problem.
So I think either this should be corrected via software, or it should be corrected via the manual/user guide/web page/whatever.

---

### Post by dino99 on 2012-12-01
a few things i suspect not exact:

- to change the grub settings: sudo gedit /etc/default/grub , then sudo update-grub

- the grub menu is only displayed when there is more than 1 OS installed

- grub-timeout=0 does not show the menu (loaded too quickly to see it)

- in case of old system upgraded, with still old grub (legacy = grub1) and its menu.lst around, will disturb grub2 and give unexpected result (so need to be purged)

---

