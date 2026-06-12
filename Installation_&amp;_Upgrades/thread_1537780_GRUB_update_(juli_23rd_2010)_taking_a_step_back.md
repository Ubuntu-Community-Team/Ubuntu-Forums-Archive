---
title: "GRUB update (juli 23rd 2010): taking a step back?"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by robenroute on 2010-07-24
Having several distros on my computer (including Windows), I prefer BING (BootIt NG) as an overall boot manager. This way, I just install a distro together with GRUB to its dedicated partition, and keep full control over what partitions are available/visible and bootable when family members use the computer.

Yesterday, I tried to update Lucid (Ubuntu 10.04) and got a problem with the newly available GRUB (1.98-ubuntu7): it said that installing GRUB to a partition was a "BAD" idea, and, luckily, refused to update. I've noticed this behaviour during my last install of Sidux (great distro to keep track of what's happening at the KDE front, by the way). Same problem, same message. Result: no more new Sidux releases...

What's going on? Is this intended behaviour and thus making it impossible for people to manage their booting their own way? Are we talking about a bug here? There seems to be a mentioning of this behaviour on Launchpad, but it's unclear whether it's a bug or not; at least to me.

Any feedback would be greatly appreciated. Thanks in advance.


Kind regards,
Rob

---

### Post by hal8000 on 2010-07-24
I have multiple distros on my PC, but control booting through grub legacy.
You may be able to solve this by uninstalling grub on the distributions that do not control your boot process.

Not tried BING, thanks for the info.

---

### Post by robenroute on 2010-07-24
Thanks for the reply. GRUB legacy is a dead-end street, as far as I know. I suppose I could go the GRUB2 way, but it's all beta and officially not recommended for production systems. Bit of a frying pan and fire situation, I guess.

What puzzles (and worries) me though, is the seemingly lost ability/functionality to install GRUB to a partition, instead of the MBR. I thought Linux was about choice; not much choice left here.

By the way, the latest Mint (9) also suffers from this.

---

### Post by Hyler on 2010-07-24
I'm not sure if this is related, but you can install GRUB to a partition, only the partitions must exist already. So, if you create them with, say, GParted first (or install Ubuntu, then run the installer again), it will let you choose, say, /dev/sda2 as the target for the bootloader.

That's what I did (old Inspiron 8600, alongside Windows XP) and I wanted to let Windows manage the booting process because I honestly don't trust GRUB, so I did the good ole

```
dd if=/dev/sda2 of=boot.lin bs=512 count=1
```

and put that file in the Windows root folder and let Windows boot GRUB, which in turn boots Ubuntu.

The above method has worked greatly in the past, until 10.04. Since last night, I've performed 3 clean installs, and the method works every time *until* I run an update, at which point, after the update is finished and I restart, GRUB either hangs or displays Invalid Partition Table.

How many more tries do I give this thing? Makes me feel really smart for not putting (not *ever* putting) GRUB on the MBR.

I'm not trying to bitch, but what am I supposed to do at this point?

George

---

### Post by robenroute on 2010-07-25
Hi George (and others),

The new GRUB apparently doesn't support installing to partitions. That's the whole problem. My choice for BING comes from having to deal with partitions (creating, backing up, hiding, etc.) all the time, and that in an environment where 3 people use a single computer.

I've noticed a few times too often that distros, when being installed, don't recognize already installed other distros (incl. BSD). When you've got GRUB installed in the MBR, a new installation of a distro might completely mess up your boot set-up. That is the very reason I went for BING and have all my partitions with their own GRUB set-up: that way a distro can do what it wants and not jeopardize my boot config.
But it seems now, this is no longer possible with GRUB.

Basically, this is what you do with your Windows set-up. The "only" difference is that BING offers a lot more additional functionality and an easier way of kick-starting partitions than the "dd" command.

---

### Post by efflandt on 2010-07-25
Not sure what your specific problem is.  Do you have or are you trying to install grub2 to a primary partition, or extended or logical partition.  I have never had any trouble installing either grub to a primary partition instead of the mbr.  It may bitch, but if you know what you are doing and ignore the warning, it works fine (at least on a primary partition).  I have not tested if grub or grub2 works on extended or logical partition.

I just did Lucid updates on my old system that has standard Windows mbr and grub2 on sda3 (marked as boot partition), and the grub update did not complain at all or have any problems.  When I boot it says Version 1.98-1ubuntu7.

---

### Post by kansasnoob on 2010-07-25
From the changelog:

> grub2 (1.98-1ubuntu7) lucid-proposed; urgency=low

  * Update harmfully incorrect German translation of menu legend, which
    omitted mention of pressing Ctrl-x to boot (LP: #580178).
  * Rearrange postinst install_devices logic so that preparatory code is run
    only once and the while loop only encloses actual asking of questions,
    and so that the question being asked is always marked for redisplay when
    going round the while loop again (LP: #580408).
  * [B]Only offer partitions containing /, /boot, or /boot/grub for
    grub-install; installing to other partitions may have harmful effects
    such as making Windows unbootable, and installing GRUB to every single
    partition is likely to result in confusion anyway (LP: #576724).[/B]

So debconf should show options similar to this:

[ATTACH]164498[/ATTACH]

The old behavior would allow far too easily installing grub2 to any partition which should never be necessary.

Please post a screenshot of the behavior you encounter.

---

### Post by kansasnoob on 2010-07-25
@ Hyler, you said:

> I wanted to let Windows manage the booting process because I honestly don't trust GRUB

Why not trust grub? I've always used either legacy grub or grub2 with little trouble whatsoever.

Grub2 is actually getting quite great :)

I'll grant you that the version in Karmic was a bit rough around the edges but now it just keeps getting better.

Updates should not "silently" change where dpkg remembers grub-pc being installed originally, but if you want to avoid updates to the packages "grub-common" and "grub-pc" just choose to "Lock Version" in Synaptic.

---

### Post by robenroute on 2010-07-25
> **efflandt said:**
> Not sure what your specific problem is.  Do you have or are you trying to install grub2 to a primary partition, or extended or logical partition.  I have never had any trouble installing either grub to a primary partition instead of the mbr.  It may bitch, but if you know what you are doing and ignore the warning, it works fine (at least on a primary partition).  I have not tested if grub or grub2 works on extended or logical partition.

I just did Lucid updates on my old system that has standard Windows mbr and grub2 on sda3 (marked as boot partition), and the grub update did not complain at all or have any problems.  When I boot it says Version 1.98-1ubuntu7.

Indeed, trying to install grub2 to a logical partition (in this case, I'm trying to install Mint 9). But also the last Ubuntu 10.04 grub2 update: it actually did update (now on ubuntu7), but gave warnings that were worrying...

Like I mentioned before, Sidux (also featuring the latest grub2) also refuses to install grub2 to a logical partition. Perhaps they're just warnings that can be ignored?

---

### Post by robenroute on 2010-08-05
> **kansasnoob said:**
> From the changelog:



So debconf should show options similar to this:

[ATTACH]164498[/ATTACH]

The old behavior would allow far too easily installing grub2 to any partition which should never be necessary.

Please post a screenshot of the behavior you encounter.


Hi there KansasNoob,

Just re-read your posting. It's rather mind-boggling that the developers determine what is and what isn't confusing for users. I'd rather make my own decisions on how to configure my partitions, my boot procedure and sorts.

Ah well, I guess even the Linux world isn't what it used to be; perhaps in a while, I'll also have to toe the line and let others take control of my computers ;-)

---

### Post by oldfred on 2010-08-05
Are you mixing up a grub partition with the grub files and the grub boot loader that goes into the MBR (or the PBR). Installing grub2 boot loader to a partition with windows has caused massive boot failures for many users, it cannot be installed to a windows partition without corrupting the windows boot process. The same applies to any other systems that require boot info in the boot sector. So Grub2 (or old grub for tha matter) should not be installed to other systems partition boot sector.

You can install the  grub2 boot loader to your Ubuntu partition if you want. But be aware that it may be less reliable as it uses blocklists which I under stand are hard coded addresses. If the grub files get moved on changes/updates/fileschecks, then it may require reinstalling to boot again.

---

