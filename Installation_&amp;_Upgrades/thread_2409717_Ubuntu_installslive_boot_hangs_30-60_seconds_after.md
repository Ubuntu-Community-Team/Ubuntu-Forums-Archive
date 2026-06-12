---
title: "Ubuntu installs/live boot hangs 30-60 seconds after loading"
date: 2019-01-05
forum: Installation &amp; Upgrades
---

### Post by apokkalyps on 2019-01-05
I have built a machine intended to run 18.04 Server.  It's a threadripper 2920x on Asrock TAICHI x399 motherboard with a zotac GT710 video card.  The installer always hangs on me about 30-60 seconds in no matter what I do.

Data points:
[LIST]
[*]I can boot off USB into passmark memtest and test my ram for 8+ hours with no issues.
[*]I can install windows just fine from USB and run benchmarks and SETI@home for 3 days with no issues.
[*]I can install Debian 9.6.0 and that runs fine for days.
[*]Attempting to install Ubuntu 18.4.1.0 Server or 18.10 Server with subsiquity text installer hangs 30-60 seconds in (regardless of where in the text menu I have made it to).
[*]Attempting to install Ubuntu 18.4.1 Desktop with gui installer also hangs 30-60 seconds in.
[*]Booting into Ubuntu 18.4 Desktop Live starts up and I can get on the internet etc briefly, but soon it hangs like the installers.  So it's not "just" the installer.
[*]When it hangs from this issue, if I do a soft reboot by hitting the reset button, it will freeze at the bios splash screen.  It must be powered off and back on to retry.
[*]Motherboard is on 3.30 firmware via 2.30 bridge firmware to support zen2.
[*]I'm aware of the ryzen idle issue, though I don't fully understand it beyond relating to going into idle states and not coming back. I have tried setting Power Supply Idle Control to Typical Current Idle, though this was not necessary for the others to work and I am not seeing it have any effect on the ubuntu instances hanging.
[*]I have also tried putting nomodeset and idle=nomwait in the grub linux line and behavior seems the same.  (Not sure if I did that correctly, however)
[/LIST]

Interested in any thoughts or suggestions.  In the worst case I can run this machine on debian though I'm more used to ubuntu and like being able to come to these forums.

---

### Post by apokkalyps on 2019-01-11
I've finally solved this issue and have my machine up and running.  For anyone else having a similar problem here's some information.  It wasn't just "debian works fine and ubuntu doesn't", debian 9.6.0 is a few years old and runs kernel 4.10, while ubuntu has been moving forward and at the moment the lowest kernel in a supported ubuntu version is (I think) 4.13.  I went back and installed unsupported zesty (kernel 4.9) and found that it worked, so this was kernel dependent, whatever it was.  With a working ubuntu zesty install, I then used the EOL upgrade path to kinda go through the backdoor to get an 18.04 install. As I sortof expected, that crashed immediately on boot like the installer, but having gone through the upgrade path left the series of kernels in my grub menu and I could run 18.04 off of 4.10 (instead of it's 4.15), and get into a stable system.  Then booting into kernel 4.10 I installed ukuu and installed (and tested) kernels 4.19.13 and (recent) 4.20 and saw that the issue persisted.

Finally I debugged the boot with initramfs breakpoints, (successively trying kernel flags: break=top, break=mount, break=mountroot, break=bottom, break=init) if I ran it to break=bottom I could see the last thing on the console before it would crash is "nvme: nvme0: controller is down; will reset" and then it would hang.  Googling this was the tipping point.  Lots of people have had this issue and some with the exact same WD Black 500G nvme I have.  The recommendation was to use the kernel flag "nvme_core.default_ps_max_latency_us=5500".  And low and behold I could boot into 18.04 could boot fine on 4.15 and 4.19.14.

One other Gotcha I had was in trying to make the kernel flag permanent by putting it in /etc/default/grub on the GRUB_CMDLINE_LINUX_DEFAULT line, it was not getting persisted to the /boot/grub/... after running update-grub.  Turns out there's some issues there with this /etc/default/grub.d/50-curtin-settings.cfg which seems to be added during install as a bug (?) when doing a regular install that is not via curtin or MAAS.  That overrides the user setting of GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub.  It also had 2 other settings I didn't want in it, one forcing my grub menu into text mode and the other turning off the probing for other OS's (not that I have any, but no reason for that to be disabled for me).  I just renamed /etc/default/grub.d/50-curtin-settings.cfg to /etc/default/grub.d/50-curtin-settings.cfg.disabled and ran update grub.  Rebooted and got a nice graphical grub screen and default kernel flags that prevent the nvme issue from locking the machine up during boot.
So now I'm in business.  What a relief!

---

