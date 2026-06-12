---
title: "Systemd makes the boot fail"
date: 2018-01-01
forum: Installation &amp; Upgrades
---

### Post by enricobe on 2018-01-01
Hello, i bought a new PC ([ASUS N55VX-FW131T]("https://www.eldomcat.com/computer-asus-N552VXFW131T/product/5864065")) and I can't install ANY distor which uses systemd. I've tried with Ubuntu (the one I would like to install) and then many other distros (for test) but none of them boots. Other distros _without_ systemd work fine (Deuvan, MX Linux, ...)

When I boot Ubuntu I get this error

```

tmp.mount
tpm_crb MSFT0101:00:00: [Firmware bug]: ACPI region does not cover the entire command/response buffer. [mem 0cfed40000-0xfed4087f flags 0x200] vs fed40080 f80
tpm_crb MSFT0101:00:00: [Firmware bug]: ACPI region does not cover the  entire command/response buffer. [mem 0cfed40000-0xfed4087f flags 0x200]  vs fed40080 f80
systemd-tmpfiles-setup.service
console-setup.service
systemd-update-utmp.service

```

and the boots stops at this point. I can't reboot and I need to long-press the Power button to shutdown the PC... 

Any suggestion?

---

### Post by TheFu on 2018-01-03
Does the live-CD work?
Is this just an installation issue?

Which release are you trying to install?  17.10 has known issues for new installs.

---

### Post by enricobe on 2018-01-03
> **TheFu said:**
> Does the live-CD work?
Is this just an installation issue?

Which release are you trying to install?  17.10 has known issues for new installs.

Hi and thanks for your reply! The LiveCD doesn't boot. I've tried with  lubuntu & ubuntu 17.10 and daily isos of 18.04. Non of them boot  correctly.
This is not an installer issue as I can't even boot the Live system because it stops showing the messages above

---

### Post by TheFu on 2018-01-03
And 16.04?

17.10 has issues with fresh installations last time I checked, except if you do an upgrade install.

Brand new equipment is the "bleeding edge."  I didn't look up the age of that model.

Google found this solution:
[https://askubuntu.com/questions/867134/problem-with-installing-ubuntu-on-asus-n552vx](https://askubuntu.com/questions/867134/problem-with-installing-ubuntu-on-asus-n552vx) It needs a grub option that I've never seen used before.

Regardless, I wouldn't use 17.10. Stick with the last 16.04.x LTS. It should have the current HWE stack.

---

### Post by rbmorse on 2018-01-03
Systemd probably doesn't have anything to do with the problem.  More likely it's the Nvidia gpu.  You'll need to manually add the option 
nomodeset to the boot options on the GRUB menu stanza for installing Ubuntu.  Which for the life of me I've suddenly forgotten how to do.  

Maybe this is it (if not someone who knows what they are doing will be along to set you right):

on the GRUB menu highlight "install Ubuntu" then press the "e" key to open the boot options editor.  Somewhere you'll see the phrase splash quiet.   Just before that enter:

nomodeset

then press the F10 key to proceed to the boot.  Maybe?

---

### Post by enricobe on 2018-01-04
> **TheFu said:**
> And 16.04?

17.10 has issues with fresh installations last time I checked, except if you do an upgrade install.

Brand new equipment is the "bleeding edge."  I didn't look up the age of that model.

Google found this solution:
[https://askubuntu.com/questions/867134/problem-with-installing-ubuntu-on-asus-n552vx](https://askubuntu.com/questions/867134/problem-with-installing-ubuntu-on-asus-n552vx) It needs a grub option that I've never seen used before.

Regardless, I wouldn't use 17.10. Stick with the last 16.04.x LTS. It should have the current HWE stack.

thanks for the link, this worked! I already have the last version of the BIOS but I've never tried with the boot option described in the post. I'm now running PopOS by System76 because this one booted as liveCD (but not when installed) but I think I'll come back to some kind of *buntu (probably Xubuntu because i don't like Gnome and KDE). Anyway, thanks for the link! It seems that you solved my problems =d>=d>

---

### Post by TheFu on 2018-01-04
If it is solved, please mark this thread as [solved] using the thread tools above to help the rest of the community.

---

### Post by enricobe on 2018-01-06
[SIZE=3][FONT=arial][/FONT][/SIZE]> **TheFu said:**
> If it is solved, please mark this thread as [solved] using the thread tools above to help the rest of the community.

Marked as solved.

I write here the fix in the case that the link above goes offline.

For booting: press E to edit the boot options and modify "quiet splash" in "quiet acpi_osi=!"

When installed:
edit (as sudo) the file /etc/default/grub
edit the part GRUB_CMDLINE_LINUX_DEFAULT="quiet" as GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=!"
save
use the "sudo grub-mkconfig -o /boot/grub/grub.cfg" to apply the changes

---

