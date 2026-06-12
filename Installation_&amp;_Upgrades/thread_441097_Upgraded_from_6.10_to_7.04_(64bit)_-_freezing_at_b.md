---
title: "Upgraded from 6.10 to 7.04 (64bit) - freezing at boot &amp; black screen."
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by derGhostrider on 2007-05-12
Hello!

I upgraded from 6.10 64bit (100% working, self-compiled 2.6.20.4 kernel) to 7.04 with Adept (There is a new version of Kubuntu available...).
The upgrade seemed to work fine and even the first reboot was no problem. (First reboot was no problem IF I REMEMBER CORRECT!)

Since the second reboot the screen turns black and the monitor enters standby right after the point where grub asks for the Kernel-Version / OS to load.
**If I try to start in recovery mode of any of the installed kernel versions it works without problems!** I have to login as root and I can even start the Xserver (startx) without any problems. Of course I do not want to work as root...

At first I thought that it would be a problem with the graphic settings because I changed the display before I upgraded. As root I upgraded the xorg.conf (dpkg-reconfigure xserver-xorg). It does not make a difference if I use the "ati" or the "fglrx" driver. The x-server will come up without any problems as long as I am logged in as root.

After I checked that x is still functional I tried to reboot: The monitor turns off again.
I tried to boot my self-compiled kernel: The monitor turns off.
I tried to boot the recovery-mode of the self-compiled kernel: The system boots up as root.
I started x: The xserver works.
I tried to boot the new kernel that came with 7.04: The screen turns black and the system hangs. :(

Everytime when the screen turns black and enters standby mode the system hangs and does not respond to CTRL+ALT+Backspace or anything else. I have to power it of by hitting the power button for 4seconds or longer.


System:
CPUs: 2x Opteron 246
Mainboard: Tyan Thunder K8W S2885
Graphics card: ATI X800Pro
...
Other parts should not matter. If you need additional information please let me know.


Is there some kind of "trick" to restore "out-of-the-box" startfiles for kubuntu? Does anyone have an idea what I can do to get my system up and running again?

----------------------------------

Edit:

Solved it myself.

I had to add "acpi=off apm=off noalpic" to the line that loads the kernel in the file /boot/grub/menu.lst
That's all - now it's working again...

---

