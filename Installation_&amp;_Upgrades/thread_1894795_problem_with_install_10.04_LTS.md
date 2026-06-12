---
title: "problem with install 10.04 LTS"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by DFHansen on 2011-12-13
[FONT=Times New Roman]I am trying to install 10.04 on a ASRock G41MH-GE motherboard using its integrated video controller and am running into problems.  It seems to have problems specifically with this version of ubuntu (9.04 installed fine).  I finally got it to install correctly after adding a disk drive (could not install from USB) and using the nomodset boot option.  I then tried to reboot and could not get to the boot menu, so I rebooted and ran from the disk and tried to edit /etc/default/grub to include the nomodset boot option (edit GRUB_CMDLNE_LINUX_DEFAULT="quiet splash nomodset"), then following the instructions on[/FONT]
[FONT=Times New Roman][https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot) for the chroot option ran update-grub to try to solve this issue.   Rebooting I still cannot get to the boot menu (fails with display stopping at different spots, something like [4.45 708 4] ---[end trance 0805cbd0d6f424f4]---, or different numbers, but no error message).  Any clues on what I am doing wrong, or how I can get this to boot correctly?  Thanks in advance for any help![/FONT]

---

### Post by DFHansen on 2011-12-13
Sorry, I had a typo in the above post, should read "nomodeset".

---

### Post by DFHansen on 2011-12-13
I did find a very ugly solution to this.  I installed 11.1 (which installs correctly), then when I get to the boot prompt, I edited the boot options for 10.04 to include nomodeset.  This works, but would still like to know how to edit this if you cannot get to the boot prompt.

---

### Post by darkod on 2011-12-13
You should always be able to get to the boot menu, because it displays even before the OS starts loading. I think the problem is after the menu.

However, since having only one ubuntu OS does not show the menu (no other OS to choose from), you need to try by pressing (and letting go) Shift when the computer boot starts, in order to get the grub menu displayed.
In there you can edit the boot command for a one time fix, and later when you boot add it as permanent fix.

In fact, if you manage to boot it once I am not sure you even need the nomodeset as permanent fix, or by updating the video drivers (activating) the system will start booting even without nomodeset. The problem is to get to that first boot. :)

---

### Post by DFHansen on 2011-12-13
I seem to need to add the nomodeset option for it to work.

---

### Post by plucky on 2011-12-14
> **DFHansen said:**
> I seem to need to add the nomodeset option for it to work.

```
gksudo gedit /etc/default/grub
```

Then change > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

To> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nomodeset" and then run ```
sudo update-grub
``` and you will now have it in the grub command line.

Good Luck

---

### Post by DFHansen on 2011-12-14
Thanks, it all works now.

---

