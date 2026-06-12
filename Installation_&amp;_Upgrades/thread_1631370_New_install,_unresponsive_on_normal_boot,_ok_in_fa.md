---
title: "New install, unresponsive on normal boot, ok in failsafe"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by Kaiya on 2010-11-26
I'm very new to Linux. Last week I successfully installed Ubuntu/Gnome onto a 3 year old Toshiba Vista laptop which worked mostly brilliantly. Today I am trying to install it onto a 4 year old Toshiba XP laptop, but am having problems.

Laptop specs:
Intel 1.50GHz
488MB RAM
60GB HDD, partitioned by Ubuntu on install into 30GB/30GB, both partitions over 75% free space

The laptop, though old, still functions in XP, and the main reason we're  switching it to Linux is that it has issues managing wireless, plus  it's fun to do so - learning experience and all. The other laptop has better specs - multiply everything by 2 ;) but Windows was much less reliable as, after all, it is Vista, and switching to Linux there was a necessity.

The Ubuntu is 10.10 and it's the same live cd I used to install it onto the other laptop. It's installed alongside Windows XP and the install proceeded without issue. However when booting in normal mode it becomes unresponsive very quickly - sometimes as soon as the five pips on the loading screen become orange, the last time it lasted a whole 2 minutes before becoming unresponsive.

In failsafe graphics boot it runs without issue. The update manager tells me it's up to date, and I have installed Wine through SPM while typing this. It's behaving as I'd expect it to, with tiny lags on scrolling sometimes (perhaps related to being in failsafe graphics).

Is there some setting (graphics?) I should change to allow it to cope in normal mode? I'm aware 488MB RAM is slightly under the recommended amount, but it evidently can cope in failsafe so would appear to be enough to function?

Many thanks for any help!

---

### Post by viralmeme on 2010-11-26
> **Kaiya said:**
> Many thanks for any help!

er .. check the BIOS settings ... PCI, ACPI etc ..

---

### Post by Rubi1200 on 2010-11-26
Hi and welcome to the forums :-)

Also, what graphics card is installed on the laptop in question?

Thanks.

---

### Post by Kaiya on 2010-11-26
Thank you :)

It's a Radeon Xpress 200M. On googling that it appears to have had display problems with previous versions of Ubuntu - I don't get any display errors (weird lines, distortion etc.) just unresponsiveness.

System -> Administration -> Additional Drivers - all that was suggested here was a Software Modem driver, which I activated. It didn't help.

EDIT in Monitors the monitor is unknown and nothing can be set there. I don't know if this is also the case in the normal boot - it won't get that far before becoming unresponsive.

---

### Post by Rubi1200 on 2010-11-26
When the laptop boots and you see the GRUB menu, the entry for Ubuntu is highlighted.

Press "e" to edit and navigate using the cursor to the line that ends with > quiet splash
Remove quiet splash and type xforcevesa instead.

Then, "Ctrl" + "x" to boot and see if it makes a difference.

---

### Post by Kaiya on 2010-11-26
Although a bit laggy on some websites (especially animations), this appears to fix the unresponsiveness problem :) 

Thank you! I notice the command line reverts to quiet splash next time I restart - do I need to edit x.org to make this permanent?

---

### Post by Rubi1200 on 2010-11-26
> **Kaiya said:**
> Although a bit laggy on some websites (especially animations), this appears to fix the unresponsiveness problem :) 

Thank you! I notice the command line reverts to quiet splash next time I restart - do I need to edit x.org to make this permanent?

>  do I need to edit x.org to make this permanent?
Not right now; there is another way:

Open a terminal and run ```
sudo gedit /etc/default/grub
```

Find this line:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and change it to this:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa"
Save and then run ```
sudo update-grub
```

In any event, I am glad things are moving forward for you :)

---

### Post by Kaiya on 2010-11-26
Thanks - that has worked :) It's still very slow and I can cause it to freeze if I open too many programs, but if unchallenged it appears to function ok. I'm assuming I need too boost RAM to solve the remaining problems, so will attempt that next. I would switch to a lighter OS but as this laptop is intended to be used by a non-savvy person I think the Gnome interface is probably ideal.

Thanks!

---

### Post by Rubi1200 on 2010-11-26
You are more than welcome :)

Adding more RAM certainly might help.

---

### Post by efflandt on 2010-11-26
Instead of **xforcevesa**, you might try **nomodeset**.  That disables kernel mode setting and uses user space modules instead, which tends to work better with older ATI cards.  Although, with that amount of RAM shared for video, you may still have some video glitches if you try to do any gaming.

---

### Post by Rubi1200 on 2010-11-26
Thank you efflandt for the additional information.

---

