---
title: "Upgrade to 10.04"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by kelmark2180 on 2010-09-04
I did an upgrade and now after grub starts I get nothing but a blank screen. I should have left the well working alone. Any suggestions on what to do? I have no terminal, nothing any longer.
Thanks

---

### Post by oldfred on 2010-09-04
If it is after the grub menu? What video card do you have. Try the editing of the kernel line.

I have nvidia & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

---

### Post by kelmark2180 on 2010-09-04
RE: "If it is after the grub menu? What video card do you have."

Yes, I can see the grub menu and after it goes away it says it's loading and then nothing. It is a Intel mitx Atom processor from Intel and has on-board graphics. I will follow your instructions and try your suggestions.
Thanks so very much for the help.

---

### Post by kelmark2180 on 2010-09-04
I think xforcevesa could work but I fail on how to get it to boot with the changed setting.

# Using the arrow keys to navigate, delete quiet and splash and again insert one of the options below.
# Press Ctrl and X to boot.

After I change quiet to xforcevesa and key ctrl X it does nothing. I key enter and instructions say B to boot. Key B and the bios loads again, grub comes up but I don't know whether the xforcevesa is really there?, let it continue, and I still see a blank screen. I suppose I'm going to try a live cd and see if I can recover some config files before I go back to 9.02. Everything says this is due to old hardware, but the box is only a year old.

Jump higher, dive deeper, come up drier has put me back to never doing an upgrade again.

---

### Post by oldfred on 2010-09-05
Control x should start you booting, if you reboot the change you made is gone as it is a one time change only. Sometimes it takes a bit before you see anything on the screen.

---

### Post by kelmark2180 on 2010-09-06
RE: "Control x should start you booting, if you reboot the change you made is gone as it is a one time change only. Sometimes it takes a bit before you see anything on the screen."

I guess I just don't have a normal machine. 
I edited and changed "quiet" to xforcevesa, pressed enter,it showed:
UUID
KERNEL
INITRD
XFORCEVESA...........I keyed Ctrl + X and got a cup of coffee upstairs. The screen was at the same place. Ctrl/X just does not work here. I pressed "b" to boot and I guess it booted to somewhere (I still have no display) since I am now able to access the server through Putty on my Windoze desktop upstairs. I will look for a Linux video driver for the D945GCLF2 Intel board. I see a Linux driver on the Intel site but I haven't a clue how to download/install it from a Putty terminal.
Thanks for all your time, it is greatly appreciated.
If I can make this work through a Putty connected terminal on a Windows system, someone needs to look up "IRONIC".
Thanks, so very much; 
Don

---

### Post by oldfred on 2010-09-06
You should be replacing the quiet splash on the kernel/linux line. Not adding a new line.
from this ( this has my UUIDs so do not copy):
linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5e25282c-9c54-45df-9e79-514011e98648 ro   [COLOR=Red]quiet splash[COLOR=Black]
to this:
linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5e25282c-9c54-45df-9e79-514011e98648 ro   [COLOR=Red]xforecevesa[/COLOR][/COLOR]
[/COLOR]

---

