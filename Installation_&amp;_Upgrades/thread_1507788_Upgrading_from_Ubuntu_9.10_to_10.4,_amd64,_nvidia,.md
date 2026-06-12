---
title: "Upgrading from Ubuntu 9.10 to 10.4, amd64, nvidia, broken display"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by maphew on 2010-06-12
...other troubles not detailed here happened during my upgrade, then: after reboot the display was broken. Unlike some messages I find in the forums my display was not black, but a series alternating light and dark bars, perhaps 1.5cm in width. The pattern within the bars was like the "snow" seen on old tv sets tuned to a blank channel, but multicolored and smaller grained.

[Ctrl-Alt-Backspace] and [Ctrl-Alt-Delete] had no effect. Eventually learned [right-alt]-[SysRq]-[k] is the new kill-X magic, however all that did was go to black for a few seconds and then return with the alternating bars. Some time later figured out that [r-alt]-[sysrq]-[k] followed by repeated [ctrl]-[alt]-[del] would reboot the machine and let me try again.

Selecting one of the Recovery boot options, and then choosing Failsafe X did NOT work. There was a message about "no screens found".

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture) applied to me. Had to read the instructions for editing grub[*] carefully as what I intuited was wrong. Namely: `nomodeset` doesn't go on it's line, but is rather appended to the end of the `kernel` line. Also it's helpful to remove the `quiet splash` from the same line. If you press [b] after editing to boot and the boot sequence goes all the way back to showing BIOS and mem count etc. instead of starting linux it probably means there was a typo or some other syntax mistake.

[*] [https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---

### Post by maphew on 2010-06-12
see end of [https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace) for info about the new kill-x command.

my video card is nvidia geforce 6500

---

### Post by neerajgups on 2010-06-18
Hi,
I have a HP Pavilion dv9000 notebook (AMD Turion 64 processor).
I installed Ubuntu 10.4 recently and get strange display problems - there are dots all over the screen and some areas on the display appear in weird colors and strange fonts.

I think you have faced a similar problem. Installing nVidia drivers did not help either - in fact when I do that my display does not work - I get a display full of vertical lines after booting.

Could you please help?
I have attached a screenshot alongwith a log of lshw.


Thanks in advance for your help.

Regards,
Neeraj

---

