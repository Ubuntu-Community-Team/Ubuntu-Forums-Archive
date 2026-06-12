---
title: "Ubuntu on one disk. Windows on another disk. Switch via UEFI boot menu. Gotchas?"
date: 2015-11-14
forum: Installation &amp; Upgrades
---

### Post by bjrn on 2015-11-14
Hi.

I just built a new computer. I use Linux 99% of the time but wanted to play Fallout 4 so I got Windows 10 and installed that first.

I haven't touched new hardware in a while and I originally intended to dual boot (with "dual boot" I mean two operating systems being shared on one hard disk). But to get disk encryption with Ubuntu with all new UEFI/EFI/GPT whatever seemed to be a bit of a hassle.
So I just installed Linux on my fast SSD. Then I unplugged the disk. Plugged in my old spinning rust disk. Installed Windows 10 on that one.

Now I have this setup:

Disk 1: A fast SSD: UEFI. Ubuntu 15.10.
Disk 2: A slow disk drive. UEFI. Windows 10.

I just switch by UEFI boot menu. Linux is encrypted which I want.

Here's the question: Any way the above setup can be screwed up by accident? I worry for example that grub2 may be intelligent enough to detect that Windows is running on one of the disks, and Ubuntu may be friendly enough to try to "auto fix" my disks. Which I do not want :)

Thoughts?

---

### Post by sudodus on 2015-11-14
I think it is easier to avoid conflicts in a system like yours, with Ubuntu in one drive and Windows in another drive.

I do not worry that grub would tamper with the Windows drive during normal updates/upgrades, but when grub itself is updated, it is important that you do not let it do things automatically. Try to keep the previous settings and locations.

I have only tried the Windows 10 'version' Technical Preview, but I have read that there are problems with Windows in UEFI systems, that some updates try to lock Ubuntu out.

There is one possible option that I use myself: ***Connect your Ubuntu SSD via an eSATA and USB 3 external box***. So you can disconnect it, when you boot into Windows.

---

### Post by bjrn on 2015-11-14
Alright, so I experimented a little bit and let grub do writes all over the place. And it works well. Grub actually detected the windows EFI partition and did that "chain" thing. So now I can just let UEFI boot to the Ubuntu drive. And from there I can boot Windows too.

The scary part would of course be the other direction: Making sure that *Windows* does not touch my SSD. That is maybe a little bit out of scope for this forum but if you have any suggestions that doesn't require pulling out cables that'd be appreciated.

---

### Post by sudodus on 2015-11-14
> **bjrn said:**
> Alright, so I experimented a little bit and let grub do writes all over the place. And it works well. Grub actually detected the windows EFI partition and did that "chain" thing. So now I can just let UEFI boot to the Ubuntu drive. And from there I can boot Windows too.

The scary part would of course be the other direction: Making sure that *Windows* does not touch my SSD. [COLOR="#FF0000"]That is maybe a little bit out of scope for this forum[/COLOR] but if you have any suggestions that doesn't require pulling out cables that'd be appreciated.

I think it is ***within*** the scope of the Ubuntu Forums to help each other to make sure that our Ubuntu installed systems are not damaged :-)

---

### Post by grahammechanical on 2015-11-14
> Ubuntu may be friendly enough to try to "auto fix" my disks.

I would put it the other way around. Ubuntu is friendly enough NOT to auto fix our disks. If you mean by that, simply format the disks without asking. On the other hand I have seen several posts on this forum which indicate that some Windows 10 upgrades from Windows 8 repartition the disks and wipe away Ubuntu.

I would not be surprised if any update to the Windows boot loader did not replace the boot loader in all disks instead of just the disk with Windows 10 on. It is very impractical but the only really safe option is to disconnect the SSD before updating Windows 10. Either that or become familiar with boot repair and keep a backup of all your data on Ubuntu.

Regards

---

