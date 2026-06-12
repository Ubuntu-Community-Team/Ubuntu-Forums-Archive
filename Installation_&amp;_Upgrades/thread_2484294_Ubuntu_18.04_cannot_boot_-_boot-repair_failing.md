---
title: "Ubuntu 18.04 cannot boot - boot-repair failing"
date: 2023-02-22
forum: Installation &amp; Upgrades
---

### Post by neviem on 2023-02-22
Hey there, was running ubuntu 18.04 and system suddenly crashed; upon restart would not boot, and none of the kernels I have would either (generic or recovery). Boot repair paste-bin can be found here:  [https://pastebin.com/hiFnV8kX](https://pastebin.com/hiFnV8kX) / [https://paste.ubuntu.com/p/K57w9yR73d/](https://paste.ubuntu.com/p/K57w9yR73d/)


I also get ```
error: attempt to read or write outside of disk 'hd0'
``` when trying to boot now.

[B]What I have tried
[/B]
[I]In grub rescude mode:

[/I]```

grub rescue> ls
(hd0) (hd0,msdos1)
grub rescue> set prefix=(hd0,msdos1)/boot/grub
grub rescue> set root=(hd0,msdos1)
grub rescue> insmod normal
error: attempt to read or write outside of disk 'hd0'

```

[I]Booting from a live usb:
[/I]
[LIST]
[*]mounting /dev/sda1 etc and reinstalling linux-image++
[*]boot-repair (which ran "successfully" but reboot went straight into attempt to read or write outside etc)
[/LIST]

Not sure if there are any suggestions, would ideally not transfer to external drive + reinstall with newer version of ubuntu, but currently can't see what else to try.

Appreciate your help/time.

---

### Post by TheFu on 2023-02-22
I'd check the log files for errors and warnings first.  
I'd also backup everything I couldn't live without ASAP!  5 yrs is a common time when hardware starts failing, not that hardware can't work for 10-20 yrs, but sometimes, especially with HDDs, hardware fails around 5 yrs in.

BTW, boot repair has not been as great as it was before UEFI got involved. Best not to use it.  You could boot from the same version Ubuntu ISO, then setup a chroot and reinstall grub to the HDD. Since I won't look at the boot-repair log (requires a login), I can't say this is or isn't the issue. If you were doing weekly system backups, it is likely not caused by bit-rot.

The good news is that some real booting experts will show up in the next few hours and respond with excellent advice. Wait for them, if you can.

You already know that standard support for 18.04 is ending in a few months, so it is time to migrate ASAP to a newer, supported, release. I'm in the same boot as you, working on moving systems now, today.

---

### Post by tea for one on 2023-02-22
You have 18.04 installed in Legacy mode.

Some observations:-
Legacy mode is now somewhat old-fashioned.
18.04 reaches End of Life in April 2023.

Is there any reason not to back up your data and install Ubuntu 22.04 in UEFI mode with GPT?

---

