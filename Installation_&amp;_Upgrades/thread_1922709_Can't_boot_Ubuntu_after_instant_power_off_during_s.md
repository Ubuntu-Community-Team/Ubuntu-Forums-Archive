---
title: "Can't boot Ubuntu after instant power off during shutdown procedure"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by MadBrozzeR on 2012-02-09
Recently I've got laptop Dell Inspiron N7110 (i7, 6GB, geforce GT525M, Win7).
First I disassemble it, changed HDD, and installed Ubuntu 11.10 at new one. It was no problem.
But then, at the first day of use, laptop was out of battery power and instantly powered off during shutdown (or hibernation) procedure.
Next time when I tried to power it on it showed grub and froze after selecting normal boot.
And worse: LiveCD refuses to load itself, too. Just before starting GUI it freezes and CPU cooler begins to spin madly.
Tried on Ubuntu 11.10 and Xubuntu 8.10 LiveCDs.

Returned previous HDD with Win7 onboard works perfectly (but slow), but I don't want to live with it.
What can I try not to destroy my new laptop?

P.S. Sorry for my English.

---

### Post by darkod on 2012-02-09
Linux can usually handle sudden shutdown much better than windows. But even if that leaves it corrupted, not booting the CD has nothing to do with it. At least, it shouldn't have anything to do with it.

Are you sure it's not a hardware issue?

I would focus on booting with the cd or usb stick. Once you get that going, you can try to fsck the root partition from live mode (it must be unmounted for that).

---

### Post by MadBrozzeR on 2012-02-09
I'm prety sure that there is hardware related problem, really possible. But not HDD. I'v returned previous HDD with Win7 and it works (disk and windows). But LiveCD still freezes. Memtest (from grub menu) sees no errors in memory. Motherboard?

---

### Post by sudodus on 2012-02-10
> **MadBrozzeR said:**
> I'm prety sure that there is hardware related problem, really possible. But not HDD. I'v returned previous HDD with Win7 and it works (disk and windows). But LiveCD still freezes. Memtest (from grub menu) sees no errors in memory. Motherboard?
You get to the menu when booting from the CD? In that case, I suggest you try the boot options (press F6) one or several each time. See the following link
[[COLOR="Red"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

*nomodeset* is a hot candidate, but try the others too :-)

---

### Post by MadBrozzeR on 2012-02-10
Ubuntu 11.10 LiveCD doesn't show GUI with "Try" and "Install" options, but I didn't try to press any key in time when "keyboard=man" logo appears. Didn't realized what that means.
In case with Xubuntu 8.10 I've seen this advanced menu (as it was default menu).
Thank you for the link. I'll try it.

---

### Post by MadBrozzeR on 2012-02-11
> **sudodus said:**
> You get to the menu when booting from the CD? In that case, I suggest you try the boot options (press F6) one or several each time. See the following link
[[COLOR=Red]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

*nomodeset* is a hot candidate, but try the others too :-)

acpi=off did the trick. But now laptop can't be shutdown properly. System halts at logo:
Ubuntu
 . . . . .
And then only power button works.
Tried solution from [that]("http://ubuntuforums.org/showthread.php?t=1409486") thread - no result.

---

### Post by MadBrozzeR on 2012-02-11
Ehm... you know, linux is really strange thing.
First I've tried to place
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off apm power_off=1 quiet splash"
in /etc/default/grub as a last suggestion in thread I linked above. Placed the same parameters in /boot/grub/grub.cfg. No help.
Then I made an attempt to chenge line in grub to "acpi=ht". Worked!
But I was still worried about disabling ACPI (even if I don't really understand what that means). And tried to remove this parameter from grub. So I just returned grub to the first state. And now it's everything fine. Either boot and shutdown.

Thank you everyone for your help.

---

### Post by sudodus on 2012-02-12
Something must be changed, either you did it (and forgot about it) or an update by the system did it. Anyway, enjoy ... and if you are satisfied, please mark this thread SOLVED

---

### Post by MadBrozzeR on 2012-02-12
One final mark.
Installed Ubuntu 11.10 with /boot/grub/grub.cfg:
```
...
    linux    /boot/vmlinuz-3.2.0-15-generic root=UUID=b318c533-d63f-4e46-ac17-c46207e29969 ro   quiet splash vt.handoff=7
...
```
and with /etc/default/grub:
```
...
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
...
```
boots and shutdowns well.

LiveCD still reqires acpi=off to boot itself.
I don't remember when I changed kernel version to 3.2 - before or after deleting acpi=off from grub.

---

