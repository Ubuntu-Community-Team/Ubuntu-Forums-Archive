---
title: "After 398 updates, boot failure &quot;out of disk&quot;"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by andycivil on 2012-09-17
Ubuntu 12 installs OK, but asks for 398 updates. When they're installed, it wants to reboot, and on reboot gives this error:

Boot from CD/DVD:
Error: out of disk
grub rescue>_

A search of the internet indicates that it's a problem accessing the disk, but the disk is fine, and there's plenty of space. (It wasn't booting from the CD at this point, I just included that to indicate where the error was printed.)

It's a new computer with quad 3600Mhz processor 8GB RAM and a 64GB SSD.

What could cause that error?

---

### Post by YannBuntu on 2012-09-17
Please follow: [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)

---

### Post by andycivil on 2012-09-17
> **YannBuntu said:**
> Please follow: [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)
Great, I'm SURE that's the answer. There are two surprises for me.

1. Why didn't I find those instructions when I googled for this? Usually if it doesn't find the right page, at least it finds a forum post which points to the right page... and it has the search terms I used, contained within it.

2. This grub bug is described as being a possibility where the disk is "big" - defined as > 100GiB. In fact, because I wanted speed over capacity, my disk is only 64GB; actually quite smaller than the standard 1TB disks that people are using now. Why did I suffer it? I'm thinking that there may be some weirdness about SSD's that triggered it. Perhaps it's the parameters? I mean, do they use "cylinders tracks and sectors" any more? Do SSDs have 1 cylinder, 1 track and a billion sectors or something?

Anyway, thanks very much. It seems to me that this bug would be a priority, because it must be affecting more and more Ubuntu users.

---

### Post by YannBuntu on 2012-09-18
> **andycivil said:**
> It seems to me that this bug would be a priority

It won't be if nobody reports it to the devs. 
So please:
1) Indicate your current [Boot-Info URL]("https://help.ubuntu.com/community/Boot-Info")
2) try the solutions I gave you above
3) if that works, indicate your new Boot-Info URL.
4) then I will help you to report the bug

---

### Post by andycivil on 2012-09-20
> **YannBuntu said:**
> It won't be if nobody reports it to the devs. 
So please:
1) Indicate your current [Boot-Info URL]("https://help.ubuntu.com/community/Boot-Info")
2) try the solutions I gave you above
3) if that works, indicate your new Boot-Info URL.
4) then I will help you to report the bug

Unfortunately, since posting the question we tried Ubuntu 10 (the LTS one because we thought it might be more stable) and although it did give that error *just once* it has been working correctly ever since (and my wife prefers the gui in any case). This makes it impractical to go back to Ubuntu 12 just to get correct information to report the bug.

However, I did say that our current installation gave the error once; if it ever does it again, you can be sure that I will follow the instructions carefully so that we can report it. I totally get how important it is that users with the technical ability to report errors do so faithfully, otherwise you're working in the dark.

---

### Post by YannBuntu on 2012-09-20
Ubuntu10.04 will be obsolete in April 2013, so you'd better report the bug now, so that devs have time to fix it, and you won't be blocked next year.

Concerning the interface, you can get the same as 10.04 on 12.04 by installing gnome-panel.

---

### Post by andycivil on 2012-10-07
The computer had been working every day for about a week. We installed another hard disk of 1TB which had previously been in a windows computer; we formatted it ext4 with parted, and called it "Ruthsmedia". It continued to work for another week. Suddenly it decided to give an error again. The error seemed to list two devices this time*. I grabbed the "yannbuntu's boot repair" disc, and booted from it. It asked to update, which I allowed. It pasted my bootinfo at [http://paste.debian.net/197529](http://paste.debian.net/197529) - I guess the update flipped it back to "debian" instead of Ubuntu. The bootinfo is there, I looked at it.

Even though the boot repair disc claimed that it didn't write anything, after removing the disc and rebooting, it now boots correctly again. And this * is why I can't quote the error message character perfect, it's not doing it now.

Additional info: when booting from the boot repair disc, I saw these errors. I know that errors during booting is normal, but I thought I'd post them just in case. 'sr0' is the CD rom, I think???

0.387344] pci 0000:00:00.0:  BAR 3: address space collision on of device [0xe0000000-0xffffffff]

8.233027] end_request: I/O error, dev sr0, sector708624
8.233060] Buffer I/O error on device sr0, logical block 88578

(this error was repeated every four seconds or so)

Should I go ahead and try some of the repair suggestions? The suggestion in the bootinfo to "reinstall the grub2 of sda1 into the MBRs of all disks" and put the boot flag on sdb1 doesn't seem very helpful, since sdb shouldn't even be part of the boot process at all - I might take sdb out at any time.

---

### Post by YannBuntu on 2012-10-08
> **andycivil said:**
> [http://paste.debian.net/197529](http://paste.debian.net/197529)

I confirm it didn't change your boot/GRUB/mbr.
Why it was not working before is not clear for me, it may be due to a BIOS/disk problem.


> **andycivil said:**
> pci 0000:00:00.0: BAR 3: address space collision on of device

this one may show a disk error. The sr0 ones concern the CD, so they are not important.

> **andycivil said:**
> The suggestion in the bootinfo to "reinstall the grub2 of sda1 into the MBRs of all disks" and put the boot flag on sdb1 doesn't seem very helpful

I agree. Your GRUB is already correctly installed, reinstalling it wouldn't change anything. The boot flag on sdb1 wouldn't hurt, but wouldn't change anything either in your case.

---

### Post by andycivil on 2012-10-10
Update: I have abandoned Ubuntu 10.04.4 and installed Ubuntu 12.04.LTS again. This time around, I used gparted first, to set up a separate boot partition. I reduced the size from what was recommended, to 400MB, but even now, it's only 12% used. So far, it's working correctly. I have run YannBuntu's boot repair disc ***even though it's working correctly*** as a baseline, to see if anything changes. The url is [http://paste.debian.net/197929](http://paste.debian.net/197929) but I see no reason to visit, unless it breaks again. Thank you for your help.

---

