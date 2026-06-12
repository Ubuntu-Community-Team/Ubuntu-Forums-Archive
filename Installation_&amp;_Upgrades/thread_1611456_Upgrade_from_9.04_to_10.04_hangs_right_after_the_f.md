---
title: "Upgrade from 9.04 to 10.04 hangs right after the fsck"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by francisu on 2010-11-01
(Sorry made a mistake in the title. I was on 9.10 (Karmic) and doing the upgrade through the software updater gui -- I had been on 9.04 for so long I forgot about the brief upgrade to Karmic which went fine).

1) I'm running the recovery mode boot and the last thing it shows are two fsck lines for the two disks that I have which show as successful. 

There is a bunch of output in console mode before that (which does not seem to indicate any errors) and then it shows "fsck from util-linux-ng 2.17.2" and then the two clean fsck lines.

If I use control-alt-delete it will emit a few lines and reboot, no other keys. Hitting escape again shows the fsck lines again (along with one line before them).

I tried other keys (as suggested in a bug report below, like s, m, n, etc and they don't work).

The kernel is 2.6.32-25 (10.04.1).

This seems to be related to these bug reports:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576001](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576001)

Which is a dup of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571444](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571444)

But I don't think it's this since the keys "s" etc have no effect.

2) The same machine boots perfectly from a live CD of 10.04.

3) It's a Asus P5B Deluxe, 64bit.

4) I have looked at a number of other issues that seem related and ruled them out:

a) The machine does not actually boot, I tried to ssh to it and can't, so it's not a graphics card issue that's hiding the boot (and besides, it works fine from the CD). [https://bugs.launchpad.net/ubuntu/+bug/573356](https://bugs.launchpad.net/ubuntu/+bug/573356)

b) I added the "dev" entry to the fstab based on some link I found, did not help.

c) I tried all 3 kernels that were present (2.6.23-25, 31-22), the oldest of which (2.6.27-19) got a segv in plymouth

d) I tried the "nomodeset" when booting.

Any other ideas?

I guess I could re-install, but I don't have my disk partitioned so that the user data is separate from the OS data, so fixing the upgrade is preferred at this point.

---

### Post by oldfred on 2010-11-02
You must not have housecleaned old kernels. The kernels of the major revision are the only ones that have a chance of working. 

I have seen where users could boot liveCD but still had video issues with install. Something was different. Also some have required other boot parameters.

What video card do you have, from liveCD?

sudo lspci | grep VGA

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

Check BIOS for settings and sometimes other parameters:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by Slim Odds on 2010-11-02
There is no direct upgrade path from 9.04 to 10.04

Can you explain what you were trying to do?

---

### Post by francisu on 2010-11-02
> **Slim Odds said:**
> There is no direct upgrade path from 9.04 to 10.04

Can you explain what you were trying to do?

Sorry my Mistake, from Karmic (9.10 to 10.04). I was using the software updater upgrade distribution.

---

### Post by francisu on 2010-11-02
> **oldfred said:**
> You must not have housecleaned old kernels. The kernels of the major revision are the only ones that have a chance of working. 

I have seen where users could boot liveCD but still had video issues with install. Something was different. Also some have required other boot parameters.

What video card do you have, from liveCD?

sudo lspci | grep VGA


01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

---

### Post by francisu on 2010-11-02
Thanks for the help, I just went ahead and repartitioned my disk and installed 10.10 (no upgrade) and it's fine.

---

