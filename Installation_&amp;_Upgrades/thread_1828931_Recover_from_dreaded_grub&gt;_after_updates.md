---
title: "Recover from dreaded grub&gt; after updates"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by zx5000 on 2011-08-19
This was taken from a few sources but it applies to the latest kernel update.

After I rebooted from the update pushed out on 8/19/11 I got the dreaded ```
grub>
``` prompt.

```

set root=(hd0,1)
linux /vmlinuz root=/dev/sda ro
initrd /initrd.img
boot

```

System now boots properly. Open a terminal and type the following.

```

sudo grub-install /dev/sdZ
sudo update-grub

```

Now you can reboot normally.

I've lost count of how many times updates / upgrades do this but I'm really glad there was an easy solution.

---

### Post by ottosykora on 2011-08-20
The Q remains: why does the boot manager fail so often? 

And would it bring better results if all the efforts put into things like unity would be invested to a development of a boot manager which really works and does not breaks every odd time.

---

### Post by Quackers on 2011-08-20
Grub2 doesn't fail unless something is done to it.
Without specific details of the particular installation and what has been done to it, it is impossible to say what caused a boot failure!

---

### Post by zx5000 on 2011-08-20
All I had to do was allow the update manager to do the updates. If this is a problem for a small percentage of users who aren't doing anything outside the norm then it must be a bug with the updater.

For me this has happened on various hardware.
Updating from 9 -> 10 broke grub. Updating from 10.04-10.10 broke grub. Fresh install of 10.10 broke grub. Update from 10.10->11.04 broke grub. Update from 2.6.38-10-generic-pae -> 2.6.38-11-generic-pae broke grub.

If you don't think it's a problem or think I'm doing something wrong then just google grub> and see how many hits relate to update/upgrade issues.

Personally I don't care enough about the tool or developer's ego to file a bug. My concern is to help the other people who need a solution when it *_does_* happen.

Isn't Ubuntu all about helping each other?

---

### Post by Quackers on 2011-08-20
If you really want to help other people then maybe you should file a bug report.
As I said earlier, without the specific details it's difficult to say what has happened in any boot failure. There could be many causes where the only thing you see is a grub rescue or grub prompt and the natural assumption there would be to blame grub.
A simple upgrade of an installed system (not wubi) should not normally lead to a grub failure.

---

### Post by metra on 2011-08-22
> **zx5000 said:**
> This was taken from a few sources but it applies to the latest kernel update.

After I rebooted from the update pushed out on 8/19/11 I got the dreaded ```
grub>
``` prompt.


I am running 10.4 LTS and I think I've ran into the same problem. Just one of the upgrades has screwed things up

instead of grub>

I have rescue:grub>

These were my results when I tried to follow your solution
```

ls
error:no such disk
set root=(hd0,1)
linux /vmlinuz root=/dev/sda ro
error:no such disk
initrd /initrd.img
error:no such disk
boot
error: no loaded kernel

```

I've tried to reinstall grub however I"m having problems with the live LTS CD

Am trying boot-repair-disk

Not sure what else is relevant other than its GRUB 1.97 beta

There are no other OS installed and other than the upgrades from the manager no other changes have been made.

I'd appreciate any ideas or direction in fixing this, thanks.

---

### Post by metra on 2011-08-22
In the end the [boot repair disk]("https://help.ubuntu.com/community/Boot-Repair") fixed this.

I'm still not sure what went wrong or how to submit a bug report for this...normally when things break it asks permission and sends a report.

Either way, glad this thread was here because at the very least I knew this wasn't caused by a new installation.

---

### Post by zx5000 on 2011-08-22
Metra,

I'm glad the boot repair disk helped. There is no rescue option on the USB startup disk so I'm unfamiliar with it. I had also tried to repair grub from the live USB key but it failed to resolve the problem.

Judging from the hits on google it seems that there are many different problems that result in the grub> prompt each with it's own solution.

---

### Post by YannBuntu on 2011-08-23
Dear all, happy to see that Boot-Repair helped. It is a new tool, so if you have 5 minutes, please help translating it in your language : [https://translations.launchpad.net/boot-repair/trunk](https://translations.launchpad.net/boot-repair/trunk)

regards

---

### Post by zx5000 on 2012-05-04
For anyone following this I discovered that my issue was a BIOS issue. I just installed a new BIOS from HP and it solved the problem. It would always work when installing Ubuntu from scratch but every update would give errors like the grub prompt or "error: cannot load Linux header." I was in this position after updating to 12.04 but after updating the bios from circa 2006 to 2008 the new 3.2 kernel booted fine.

The following link tipped me off to this solution.

[http://superuser.com/questions/381539/cannot-read-the-linux-header-new-install-old-machine](http://superuser.com/questions/381539/cannot-read-the-linux-header-new-install-old-machine)

---

