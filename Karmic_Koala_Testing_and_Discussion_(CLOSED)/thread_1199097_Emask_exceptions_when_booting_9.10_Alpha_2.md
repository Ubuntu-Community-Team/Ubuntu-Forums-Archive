---
title: "Emask exceptions when booting 9.10 Alpha 2"
date: 2009-06-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rippy on 2009-06-28
I recently purchased a new Acer laptop (AS3810TZ), and immediately rearranged the partitions to dual-boot Vista and Ubuntu. I don't need to use Ubuntu seriously for a few months, so I thought I'd try the Karmic alpha.

My problem occurs at boot. I see the loading bar for about 10 seconds, then it falls back to a command-line and displays all kinds of errors. Some snippets are:

"exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
* Reading files needed to boot..."
"Emask 0x2 (HSM violation)"

It's not consistent either. At first it booted despite all the errors, and I was able to perform a hefty upgrade which I hoped would fix things. After the upgrade, it would attempt to do a filesystem check, which would fail, and then it would prompt for a manual run of fsck. I did this 4 or 5 times because each time fsck would "fix" a ton of errors, but new ones would appear when I restarted. This time it booted but the network manager and system clock are not present.

I'm guessing this is a hard disk or filesystem error. I've run Spinrite on level 4 on the entire drive though and it showed no errors, and Vista has run flawlessly, so I don't think it's something physically wrong with the drive. I don't see how the installer could irreparably mess up the ext4 filesystem, though, so I don't know what the problem is.

Any help is appreciated, thanks!

-Rippy

---

### Post by nystire on 2009-06-28
Sorry for the "list of demands", but:
Any particular reason that you chose to use ext4fs? 
Do you know if this happens with any of the other file system types?
Are you willing to reinstall with ext3fs and seeing if the same problem occurs?

---

### Post by psyke83 on 2009-06-28
Sounds like buggy IDE/SATA drivers. Some ideas:

[LIST]
[*]Boot your system without the "quiet splash" boot options to see if you see any revealing error messages.
[*]Boot with the option:
```
all_generic_ide
```
[*]Disable NCQ on your drives. See: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137470](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137470)
[*]Update your BIOS (very important for laptops).
[/LIST]

---

### Post by Rippy on 2009-06-28
> **nystire said:**
> Sorry for the "list of demands", but:
Any particular reason that you chose to use ext4fs? 
Do you know if this happens with any of the other file system types?
Are you willing to reinstall with ext3fs and seeing if the same problem occurs?

Because it's the default with Karmic, and I've heard that it's marginally better? I can try with ext3, but I'd rather get things working with ext4 if it's possible.

I'll try your suggestions, psyke83. I tried booting in recovery mode and didn't see any new errors, I'm guessing that would do the same as turning off quiet splash? As for the rest, I'll need time to try em out tomorrow, updating my BIOS is probably a good idea regardless though.

Thanks for the replies, I know this is kind of a vague problem...

---

### Post by psyke83 on 2009-06-29
> **Rippy said:**
> Because it's the default with Karmic, and I've heard that it's marginally better? I can try with ext3, but I'd rather get things working with ext4 if it's possible.

I'll try your suggestions, psyke83. I tried booting in recovery mode and didn't see any new errors, I'm guessing that would do the same as turning off quiet splash? As for the rest, I'll need time to try em out tomorrow, updating my BIOS is probably a good idea regardless though.

Thanks for the replies, I know this is kind of a vague problem...

Yes, recovery mode will show the same verbose output as a regular boot without "quiet splash".

---

### Post by Rippy on 2009-06-30
Updated my BIOS, reinstalled 9.10 Alpha 2 with ext4 again, reinstalled with ext3, reinstalled with ext4 once again to then try disabling NCQ, all without success.

How do you specify a boot option? I'll try it, but I'm not very confident it'll help at this point...

I'll probably just try installing 9.04 and hope that doesn't have any issues.

---

### Post by psyke83 on 2009-06-30
> **Rippy said:**
> Updated my BIOS, reinstalled 9.10 Alpha 2 with ext4 again, reinstalled with ext3, reinstalled with ext4 once again to then try disabling NCQ, all without success.

How do you specify a boot option? I'll try it, but I'm not very confident it'll help at this point...

I'll probably just try installing 9.04 and hope that doesn't have any issues.

If you're using GRUB1:
Restart your computer, and, if necessary, press ESC to enter the GRUB menu. Highlight the line to boot Ubuntu and press the "e" key to edit the entry. Add the boot option to the end of the line that finishes with "quiet splash", and then press the "b" key to boot.

If you're using GRUB2:
Restart your computer, and, if necessary, press ESC to enter the GRUB menu. Highlight the line to boot Ubuntu and press the "e" key to edit the entry. Add the boot option to the end of the line that finishes with "quiet splash", and then press Ctrl+X to boot.

I may have forgotten something, but that's the procedure as far as I can recall.

---

### Post by Rippy on 2009-07-03
No change.

I reinstalled back to what I initially had (9.10 Alpha 2 and ext4fs), and again it worked after about 5 minutes of errors, and then no longer worked after performing a partial upgrade. It gives an ext3 error saying that drive sda5 cannot be mounted due to unsupported optional features, gives some more emask errors, and prompts for a manual fsck check which does nothing to fix things.

---

### Post by dentharg on 2009-09-16
Last updates also give me a manual fsck every 2-3 bootups.
Also after yesterday update (updated upstart + mountall) it does not get up.
Last working was Alpha 5

---

